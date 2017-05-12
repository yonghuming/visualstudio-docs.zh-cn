---
title: "如何︰ 使用 AsyncPackage 加载 Vspackage 在后台 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dedf0173-197e-4258-ae5a-807eb3abc952
caps.latest.revision: 8
ms.author: gregvanl
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: c9df048a49580f3526b48e29041ef3758722ed27
ms.openlocfilehash: bcfdf6991c12affc1000ace72b16f97be9de469a
ms.lasthandoff: 05/03/2017

---
# <a name="how-to-use-asyncpackage-to-load-vspackages-in-the-background"></a>如何︰ 使用 AsyncPackage 加载在后台的 Vspackage
加载和初始化 VS 包可以导致磁盘 I/O。 如果此类 I/O 在 UI 线程上发生，它会导致响应能力问题。 若要解决此问题，Visual Studio 2015，引入了允许在后台线程上加载的包 < xref:Microsoft.VisualStudio.Shell.AsyncPackage > 类。  
  
## <a name="creating-an-asyncpackage"></a>创建 AsyncPackage  
 你可以通过创建 VSIX 项目 (**文件 / 新建 / 项目 / Visual C# / 扩展性 / VSIX 项目**) 并添加到项目的 VSPackage (右键单击项目和**添加新项 / C# 项/扩展性 /visual Studio 包**)。 然后，你可以创建你的服务，并将这些服务添加到你的包。  
  
1.  派生自 < xref:Microsoft.VisualStudio.Shell.AsyncPackage > 的包。  
  
2.  如果你要提供其查询可能会导致你要加载的包的服务︰  
  
     若要指示到 Visual Studio 中，您的软件包不安全的后台加载，并且若要选择加入此行为，你 < xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute > 应设置**AllowsBackgroundLoading**为 true 的特性构造函数中的属性。  
  
    ```c#  
    [PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]  
  
    ```  
  
     若要指示到 Visual Studio，则可以安全地实例化你的服务在后台线程上，应为 true < xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute > 构造函数中设置 < xref:Microsoft.VisualStudio.Shell.ProvideServiceAttributeBase.IsAsyncQueryable%2A > 属性。  
  
    ```c#  
    [ProvideService(typeof(SMyTestService), IsAsyncQueryable = true)]  
  
    ```  
  
3.  如果您正在加载通过 UI 上下文，则应指定**PackageAutoLoadFlags.BackgroundLoad**为 < xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute > 或作为包的自动加载项的值写入到标志的值 (0x2)。  
  
    ```c#  
    [ProvideAutoLoad(UIContextGuid, PackageAutoLoadFlags.BackgroundLoad)]  
  
    ```  
  
4.  如果你有工作要做的异步初始化，则应重写 < xref:Microsoft.VisualStudio.Shell.AsyncPackage.InitializeAsync%2A >。 删除**initialize （)** VSIX 模板提供的方法。 ( **Initialize （)**中的方法**AsyncPackage**都密封的)。 你可以使用任何 < xref:Microsoft.VisualStudio.Shell.AsyncPackage.AddService%2A > 方法将异步服务添加到你的包。  
  
     注意︰ 若要调用**基。InitializeAsync()**，你可以更改到你的源代码︰  
  
    ```c#  
    await base.InitializeAsync(cancellationToken, progress);  
    ```  
  
5.  你必须注意，不作 Rpc （远程过程调用） 在异步初始化代码中 (在**InitializeAsync**)。 这些会直接或间接调用 < xref:Microsoft.VisualStudio.Shell.Package.GetService%2A > 时发生。  需要同步加载时，将会阻止 UI 线程，使用 < xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory >。 默认阻止模型禁用 Rpc。 这意味着，如果你尝试使用 RPC 从异步任务，你将发生死锁如果 UI 线程本身等待包以进行加载。 常规的替代方法是将需要使用类似的情况下封送将代码移植到 UI 线程**加入任务工厂**的 < xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A > 或不使用 RPC 的某种其他机制。  不要使用**ThreadHelper.Generic.Invoke**或通常阻止调用线程正在等待获取对 UI 线程。  
  
     注意︰ 你应避免使用**GetService**或**QueryService**中你**InitializeAsync**方法。 如果你必须使用这些，你将需要先切换到 UI 线程。 替代方法是从使用 < xref:Microsoft.VisualStudio.Shell.AsyncServiceProvider.GetServiceAsync%2A > 你**AsyncPackage** （通过其强制转换为 < xref:Microsoft.VisualStudio.Shell.Interop.IAsyncServiceProvider >。）  
  
 C# 中︰ 创建 AsyncPackage:  
  
```c#  
[PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]       
[ProvideService(typeof(SMyTestService), IsAsyncQueryable = true)]   
public sealed class TestPackage : AsyncPackage   
{   
    protected override Task InitializeAsync(System.Threading.CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)   
    {               
        this.AddService(typeof(SMyTestService), CreateService, true);   
        return Task.FromResult<object>(null);   
    }   
}  
```  
  
## <a name="convert-an-existing-vspackage-to-asyncpackage"></a>将现有的 VSPackage 转换为 AsyncPackage  
 大多数工作都创建一个新相同**AsyncPackage**。 你需要执行步骤 1 至 5 上面。 你还需要特别注意以下︰  
  
1.  请记住删除**初始化**必须在包中的替代。  
  
2.  避免死锁︰ 可能有在现在在后台线程发生的代码中隐藏 Rpc。 你需要确保如果要进行 RPC (例如**GetService**)、 你需要任一 (1) 切换到主线程或 （2） 使用的 API，如果一个异步版本存在 (例如**GetServiceAsync**)。  
  
3.  不会改变过于频繁地在线程之间。 尝试本地化可以发生在后台线程的工作。 这将减少加载时间。  
  
## <a name="querying-services-from-asyncpackage"></a>查询从 AsyncPackage 服务  
 **AsyncPackage**可能或可能不会加载以异步方式具体取决于调用方。 例如，  
  
-   如果调用方调用**GetService**或**QueryService** (这两个同步 Api) 或  
  
-   如果调用方调用**IVsShell::LoadPackage** (或**IVsShell5::LoadPackageWithContext**) 或  
  
-   由 UI 上下文中，触发负载，但未指定的 UI 上下文机制可以以异步方式加载你  
  
 然后你的包将以同步方式加载。  
  
 请注意，你的包上仍有机会 （在其异步初始化阶段） 来完成工作，关闭 UI 线程，但将为该工作完成阻止 UI 线程。 如果调用方使用**IAsyncServiceProvider**到为你的服务的异步查询，然后负载测试和初始化将完成异步假设立即不阻止在生成的任务对象上。  
  
 C# 中︰ 如何以异步方式查询服务︰  
  
```c#  
using Microsoft.VisualStudio.Shell;   
using Microsoft.VisualStudio.Shell.Interop;   
  
IAsyncServiceProvider asyncServiceProvider = Package.GetService(typeof(SAsyncServiceProvider)) as IAsyncServiceProvider;   
IMyTestService testService = await ayncServiceProvider.GetServiceAsync(typeof(SMyTestService)) as IMyTestService;  
```

