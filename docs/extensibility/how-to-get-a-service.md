---
title: "如何： 将获得的服务 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- services, consuming
ms.assetid: 1f000020-8fb7-4e39-8e1e-2e38c7fec3d4
caps.latest.revision: 20
ms.author: gregvanl
manager: ghogen
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
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 1679fe1834b5d6246194ee4f9b3e24d6d9c09540
ms.contentlocale: zh-cn
ms.lasthandoff: 09/06/2017

---
# <a name="how-to-get-a-service"></a>如何： 将获得的服务
你经常需要以获取 Visual Studio 服务访问不同的功能。 一般情况下，Visual Studio 服务提供你可以使用的一个或多个接口。 你可以从 VSPackage 获取大多数服务。  
  
 派生自任何 VSPackage<xref:Microsoft.VisualStudio.Shell.Package>和已正确放置的任何全局服务可以要求。 因为包类实现<xref:System.IServiceProvider>，派生自包任何 VSPackage 也是服务提供程序。  
  
 Visual Studio 加载时<xref:Microsoft.VisualStudio.Shell.Package>，它将传递<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>对象传递给<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>在初始化过程中的方法。 这称为*安置功能*VSPackage。 包类包装此服务提供程序，并提供<xref:Microsoft.VisualStudio.Shell.Package.GetService%2A>来获取服务的方法。  
  
## <a name="getting-a-service-from-an-initialized-vspackage"></a>从初始化 VSPackage 获取服务  
  
1.  每个 Visual Studio 扩展开头 VSIX 部署项目将包含扩展资产。 创建[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]名为 VSIX 项目`GetServiceExtension`。 你可以查找中的 VSIX 项目模板**新项目**下的对话框**Visual C# / 可扩展性**。  
  
2.  现在，添加名为的自定义命令项模板**GetServiceCommand**。 在**添加新项**对话框中，转到**Visual C# / 可扩展性**和选择**自定义命令**。 在**名称**在窗口底部字段中，命令文件名称更改为**GetServiceCommand.cs**。 有关如何创建自定义命令的详细信息[使用菜单命令创建扩展](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
3.  在 GetServiceCommand.cs，删除 MenuItemCommand 方法的正文，并添加以下代码：  
  
    ```csharp  
    IVsActivityLog activityLog = ServiceProvider.GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
    if (activityLog == null) return;  
    System.Windows.Forms.MessageBox.Show("Found the activity log service.");  
  
    ```  
  
     此代码获取 SVsActivityLog 服务并将强制转换到<xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog>接口，可用来向活动日志中写入。 有关示例，请参阅[如何： 使用活动日志](../extensibility/how-to-use-the-activity-log.md)。  
  
4.  生成项目并启动调试。 实验实例中出现。  
  
5.  在实验实例中的工具菜单上，找到**调用 GetServiceCommand**按钮。 单击此按钮时，你应看到显示一个消息框**找到活动日志服务。**  
  
## <a name="getting-a-service-from-a-tool-window-or-control-container"></a>从工具窗口或控件容器获取服务  
 有时你可能需要从工具窗口中获得的服务或控制容器不放置，或是已放置一个并不了解所需的服务的服务提供商。 例如，你可能想要写入到的活动日志从控件内。  
  
 静态<xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>方法依赖于缓存的服务提供程序初始化任何 VSPackage 派生自第一次<xref:Microsoft.VisualStudio.Shell.Package>占位。  
  
 之前放置 VSPackage 调用 VSPackage 构造函数，因为全局服务时通常不可用从 VSPackage 构造函数中。 请参阅[如何： 解决服务](../extensibility/how-to-troubleshoot-services.md)要解决此问题。  
  
 下面是方法的在工具窗口或其他非 VSPackage 元素中获取服务的示例。  
  
```csharp  
IVsActivityLog log = Package.GetGlobalService(typeof(SVsActivityLog)) as IVsActivityLog;  
if (log == null) return;  
```  
  
## <a name="getting-a-service-from-the-dte-object"></a>从 DTE 对象获取服务  
 你还可以获取从服务<xref:EnvDTE.DTEClass>对象。 但是，你必须获得的 DTE 对象作为服务从 VSPackage 或通过调用静态<xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>方法。  
  
 DTE 对象实现<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>，您可以使用该查询通过使用服务<xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A>。  
  
 下面介绍了如何从 DTE 对象获取服务。  
  
```csharp  
// Start with the DTE object, for example:   
// using EnvDTE;  
// DTE dte = (DTE)GetService(typeof(DTE));  
  
ServiceProvider sp = new ServiceProvider((Microsoft.VisualStudio.OLE.Interop.IServiceProvider)dte);  
if (sp != null)  
{  
    IVsActivityLog log = sp.GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
    if (log != null)  
    {   
        System.Windows.Forms.MessageBox.Show("Found the activity log service.");  
    }  
}  
```  
  
## <a name="see-also"></a>另请参阅  
 [如何： 提供服务](../extensibility/how-to-provide-a-service.md)   
 [使用和提供服务](../extensibility/using-and-providing-services.md)   
 [服务基础知识](../extensibility/internals/service-essentials.md)
