---
title: "如何︰ 获取服务 |Microsoft 文档"
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
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: f66c7e1f01c8d8eb69c6718314890bfb02cccc17
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-get-a-service"></a>如何︰ 获取服务
您通常需要先获取 Visual Studio 服务访问不同的功能。 一般情况下，Visual Studio 服务提供了一个或多个接口，可以使用。 您可以从 VSPackage 中获取的大多数服务。  
  
 派生自任何 VSPackage<xref:Microsoft.VisualStudio.Shell.Package>并已正确放置，可以用于任何全局服务请求。</xref:Microsoft.VisualStudio.Shell.Package> 因为程序包类实现<xref:System.IServiceProvider>，任何从包派生而来的 VSPackage 也是服务提供商。</xref:System.IServiceProvider>  
  
 当 Visual Studio 加载<xref:Microsoft.VisualStudio.Shell.Package>，它将传递<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>对象传递给<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>在初始化过程中的方法。</xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> </xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> </xref:Microsoft.VisualStudio.Shell.Package> 这称为*选址*VSPackage。 程序包类包装该服务提供程序，并提供了<xref:Microsoft.VisualStudio.Shell.Package.GetService%2A>用于获取服务的方法。</xref:Microsoft.VisualStudio.Shell.Package.GetService%2A>  
  
## <a name="getting-a-service-from-an-initialized-vspackage"></a>从已初始化的 VSPackage 中获取一项服务  
  
1.  每个 Visual Studio 的扩展从一个 VSIX 部署项目，它将包含的扩展资产开始。 创建[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]VSIX 项目名为`GetServiceExtension`。 您可以找到中的 VSIX 项目模板**新项目**下的对话框**Visual C# / 可扩展性**。  
  
2.  现在，添加一个名为的自定义命令项模板**GetServiceCommand**。 在**添加新项**对话框中，转到**Visual C# / 可扩展性**，然后选择**自定义命令**。 在**名称**在窗口的底部字段中，命令文件名称更改为**GetServiceCommand.cs**。 有关如何创建自定义命令的详细信息[使用菜单命令创建扩展](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
3.  在 GetServiceCommand.cs，MenuItemCommand 方法的主体中删除并添加以下代码︰  
  
    ```c#  
    IVsActivityLog activityLog = ServiceProvider.GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
    if (activityLog == null) return;  
    System.Windows.Forms.MessageBox.Show("Found the activity log service.");  
  
    ```  
  
     此代码将获取 SVsActivityLog 服务并将其转换为一个<xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog>接口，可用于写入活动日志。</xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> 有关示例，请参阅[如何︰ 使用活动日志](../extensibility/how-to-use-the-activity-log.md)。  
  
4.  生成项目并启动调试。 将显示的实验实例。  
  
5.  在实验实例中的工具菜单上，找到**调用 GetServiceCommand**按钮。 当单击此按钮时，您应看到一个消息框，指示**找到活动日志服务。**  
  
## <a name="getting-a-service-from-a-tool-window-or-control-container"></a>从工具窗口或控件容器中获取一项服务  
 有时您可能需要从一个工具窗口中获取一项服务或控件未放置，否则一个并不了解所需的服务的服务提供商确定位置的容器。 例如，您可能想要写入活动日志，以从控件内。  
  
 静态<xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>方法依赖于任何 VSPackage 派生自第一次进行初始化的缓存的服务提供商<xref:Microsoft.VisualStudio.Shell.Package>占位。</xref:Microsoft.VisualStudio.Shell.Package> </xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>  
  
 因为 VSPackage 构造函数进行调用之前放置 VSPackage，全球服务不可用通常从 VSPackage 构造函数内。 请参阅[如何︰ 解决服务](../extensibility/how-to-troubleshoot-services.md)要解决此问题。  
  
 下面是方法的举例说明如何在一个工具窗口或其他非 VSPackage 元素中获取服务。  
  
```c#  
IVsActivityLog log = Package.GetGlobalService(typeof(SVsActivityLog)) as IVsActivityLog;  
if (log == null) return;  
```  
  
## <a name="getting-a-service-from-the-dte-object"></a>从 DTE 对象获取服务  
 您还可以从服务<xref:EnvDTE.DTEClass>对象。</xref:EnvDTE.DTEClass> 但是，您必须获得 DTE 对象作为服务从 VSPackage 或通过调用静态<xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>方法。</xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>  
  
 DTE 对象实现<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>，您可以使用该查询通过使用<xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A>。</xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A>服务</xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>  
  
 下面介绍了如何从 DTE 对象获取服务。  
  
```c#  
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
 [如何︰ 提供的服务](../extensibility/how-to-provide-a-service.md)   
 [使用并提供服务](../extensibility/using-and-providing-services.md)   
 [服务基础知识](../extensibility/internals/service-essentials.md)
