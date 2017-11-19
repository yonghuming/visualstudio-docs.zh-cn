---
title: "如何： 提供服务 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: services, providing
ms.assetid: 12bc1f12-47b1-44f6-b8db-862aa88d50d1
caps.latest.revision: "22"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d0adc9f69f1b0e873d2e1f38c9317070dc0d6a08
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-provide-a-service"></a>如何： 提供服务
VSPackage 可以提供其他 Vspackage 可以使用的服务。 若要提供服务，VSPackage 必须使用 Visual Studio 中注册该服务并添加服务。  
  
 <xref:Microsoft.VisualStudio.Shell.Package>类同时实现<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>和<xref:System.ComponentModel.Design.IServiceContainer>。 <xref:System.ComponentModel.Design.IServiceContainer>包含按需提供服务的回调方法。  
  
 有关服务的详细信息，请参阅[服务 Essentials](../extensibility/internals/service-essentials.md) 。  
  
> [!NOTE]
>  当 VSPackage 即将卸载时，Visual Studio 将等待，直到已传递为 VSPackage 提供的服务的所有请求。 它不允许对这些服务的新请求。 不，应显式调用<xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.RevokeService%2A>方法卸载时撤消服务。  
  
#### <a name="implementing-a-service"></a>实现服务  
  
1.  创建 VSIX 项目 (**文件 / 新建 / 项目 / Visual C# / Extensiblity / VSIX 项目**)。  
  
2.  将 VSPackage 添加到项目。 选择中的项目节点**解决方案资源管理器**单击**添加新 / 项 / Visual C# 项 / 扩展性 / Visual Studio 包**。  
  
3.  若要实现的服务，你需要创建三种类型：  
  
    -   一个描述该服务的接口。 许多这些接口为空，也就是说，它们有没有方法。  
  
    -   用于描述服务接口的接口。 此接口包括要实现的方法。  
  
    -   实现服务以及服务接口的类。  
  
     下面的示例演示三种类型的非常基本实现。 服务类的构造函数必须设置服务提供程序。  
  
    ```csharp  
    public class MyService : SMyService, IMyService  
    {  
        private Microsoft.VisualStudio.OLE.Interop.IServiceProvider serviceProvider;  
        private string myString;  
        public MyService(Microsoft.VisualStudio.OLE.Interop.IServiceProvider sp)  
        {  
            Trace.WriteLine(  
                   "Constructing a new instance of MyService");  
            serviceProvider = sp;  
        }  
        public void Hello()  
        {  
            myString = "hello";  
        }  
        public string Goodbye()  
        {  
           return "goodbye";  
        }  
    }  
    public interface SMyService  
    {  
    }  
    public interface IMyService  
    {  
        void Hello();  
        string Goodbye();  
    }  
  
    ```  
  
### <a name="registering-a-service"></a>注册服务  
  
1.  若要注册服务，添加<xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute>到 VSPackage 提供服务。 下面是一个示例：  
  
    ```csharp  
    [ProvideService(typeof(SMyService))]  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [Guid(VSPackage1.PackageGuidString)]  
    public sealed class VSPackage1 : Package  
    {. . . }  
    ```  
  
     此属性注册`SMyService`使用 Visual Studio。  
  
    > [!NOTE]
    >  若要注册一个服务来替换具有相同名称的另一个服务，使用<xref:Microsoft.VisualStudio.Shell.ProvideServiceOverrideAttribute>。 请注意允许的服务只能有一个重写。  
  
### <a name="adding-a-service"></a>添加服务  
  
1.  在 VSPackage 初始值设定项，添加服务，并添加一个回调方法来创建的服务。 下面是对进行的更改<xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>方法：  
  
    ```csharp  
    protected override void Initialize()  
    {  
        ServiceCreatorCallback callback =new ServiceCreatorCallback(CreateService);  
  
        ((IServiceContainer)this).AddService(typeof(SMyService), callback);  
    . . .  
    }  
    ```  
  
2.  实现的回调方法，这应创建并返回该服务，或如果无法创建为 null。  
  
    ```  
    private object CreateService(IServiceContainer container, Type serviceType)  
    {  
        if (typeof(SMyService) == serviceType)  
            return new SMyService(this);  
        return null;  
    }  
    ```  
  
    > [!NOTE]
    >  Visual Studio 可以拒绝的请求提供服务。 如果另一个 VSPackage 已提供服务，它会以。  
  
3.  现在，您可以获取该服务，使用它的方法。 我们将介绍此初始值设定项，但您可以获取的服务任意位置你想要使用服务。  
  
    ```csharp  
    protected override void Initialize()  
    {  
        ServiceCreatorCallback callback =new ServiceCreatorCallback(CreateService);  
  
        ((IServiceContainer)this).AddService(typeof(SMyService), callback);  
  
        MyService myService = (MyService) this.GetService(typeof(SMyService));  
        myService.Hello();  
        string helloString = myService.myString;  
  
        base.Initialize();  
    }  
    ```  
  
     值`helloString`应为"Hello"。  
  
## <a name="see-also"></a>另请参阅  
 [如何： 将获得的服务](../extensibility/how-to-get-a-service.md)   
 [使用和提供服务](../extensibility/using-and-providing-services.md)   
 [服务基础知识](../extensibility/internals/service-essentials.md)