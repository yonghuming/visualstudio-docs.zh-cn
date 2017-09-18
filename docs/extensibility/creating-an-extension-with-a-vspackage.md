---
title: "使用 VSPackage 创建扩展 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c0cc5e08-4897-44f2-8309-e3478f1f999e
caps.latest.revision: 5
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 5
---
# 使用 VSPackage 创建扩展
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

本演练演示如何创建一个 VSIX 项目并添加 VSPackage 项目项。 我们将使用 VSPackage 来获取 UI 外壳服务，以便显示一个消息框。  
  
## 先决条件  
 启动 Visual Studio 2015 中，您并不安装 Visual Studio SDK 从下载中心获得。 它将包括作为 Visual Studio 安装程序中的可选功能。 您还可以在以后安装 VS SDK。 有关详细信息，请参阅[安装 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## 创建 VSPackage  
  
1.  创建一个名为的 VSIX 项目 **FirstPackage**。 您可以找到中的 VSIX 项目模板 **新项目** 下的对话框 **Visual C\# \/ 可扩展性**。  
  
2.  当项目打开后时，添加一个名为的 Visual Studio 程序包项目模板 **FirstPackage**。 在 **解决方案资源管理器**, ，用鼠标右键单击项目节点并选择 **添加 \/ 新项**。 在 **添加新项** 对话框中，转到 **Visual C\# \/ 可扩展性** ，然后选择 **Visual Studio Package**。 在 **名称** 在窗口的底部字段中，命令文件名称更改为 **FirstPackage.cs**。  
  
3.  生成项目并启动调试。  
  
     将显示 Visual Studio 的实验实例。 有关的实验实例的详细信息，请参阅 [实验实例](../extensibility/the-experimental-instance.md)。  
  
4.  在实验实例中，打开 **工具 \/ 扩展和更新** 窗口。 您应该看到 **FirstPackage** 此处扩展。 \(如果您打开 **扩展和更新** 中的 Visual Studio 工作实例，不会看到 **FirstPackage**\)。  
  
## 加载 VSPackage  
 此时未加载该扩展，因为没有执行任何操作后，即可加载。 在交互 \(单击菜单命令，打开工具窗口\)，其 UI 或通过指定特定 UI 上下文中应该加载 VSPackage 时，您通常可以加载扩展。 有关加载 Vspackage 和 UI 上下文的详细信息，请参阅 [加载 Vspackage](../extensibility/loading-vspackages.md)。 对于此过程，我们将向您展示如何加载 VSPackage，打开解决方案时。  
  
1.  打开 FirstPackage.cs 文件。 寻找 FirstPackage 类的声明。 将现有属性替换以下内容:  
  
    ```c#  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About  
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]  
    [Guid(FirstPackageGuids.PackageGuidString)]  
    public sealed class FirstPackage : Package  
    ```  
  
2.  让我们添加一条消息，让我们知道已加载 VSPackage。 我们使用 VSPackage 的 initialize \(\) 方法来执行此操作，因为只有在 VSPackage 已就位后，可以将 Visual Studio 服务。 \(有关获取服务的详细信息，请参阅 [如何: 获取服务](../Topic/How%20to:%20Get%20a%20Service.md)。\) 用获取的代码替换 FirstPackage initialize \(\) 方法 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> 服务，获取 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> 接口并调用其 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowMessageBox%2A> 方法。  
  
    ```c#  
    protected override void Initialize()  
    {  
        base.Initialize();  
  
        IVsUIShell uiShell = (IVsUIShell)GetService(typeof(SVsUIShell));  
        Guid clsid = Guid.Empty;  
        int result;  
        Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(uiShell.ShowMessageBox(  
            0,  
            ref clsid,  
            "FirstPackage",  
             string.Format(CultureInfo.CurrentCulture, "Inside {0}.Initialize()", this.GetType().FullName),  
            string.Empty,  
            0,  
            OLEMSGBUTTON.OLEMSGBUTTON_OK,  
            OLEMSGDEFBUTTON.OLEMSGDEFBUTTON_FIRST,  
            OLEMSGICON.OLEMSGICON_INFO,  
            0,  
            out result));  
    }  
    ```  
  
3.  生成项目并启动调试。 将显示的实验实例。  
  
4.  在实验实例中打开的解决方案。 您应看到一个消息框，指示 **第一个包内 initialize \(\)**。