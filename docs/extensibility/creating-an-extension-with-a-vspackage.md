---
title: "使用 VSPackage 创建扩展 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c0cc5e08-4897-44f2-8309-e3478f1f999e
caps.latest.revision: "5"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: cb4ed4767146a07db6a4567768ee9a49fec97667
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="creating-an-extension-with-a-vspackage"></a>使用 VSPackage 创建扩展
本演练演示了如何创建一个 VSIX 项目并添加 VSPackage 项目项。 我们将使用 VSPackage 来获取 UI Shell 服务，以便显示一个消息框。  
  
## <a name="prerequisites"></a>先决条件  
 从 Visual Studio 2015 开始，你并不安装 Visual Studio SDK 从下载中心。 它将包括作为 Visual Studio 安装程序中的可选功能。 你还可以在以后安装 VS SDK。 有关详细信息，请参阅[安装 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## <a name="creating-a-vspackage"></a>创建 VSPackage  
  
1.  创建一个名为的 VSIX 项目**FirstPackage**。 你可以查找中的 VSIX 项目模板**新项目**下的对话框**Visual C# / 可扩展性**。  
  
2.  在项目打开，添加名为的 Visual Studio 包项目模板**FirstPackage**。 在**解决方案资源管理器**，右键单击项目节点并选择**添加 / 新项**。 在**添加新项**对话框中，转到**Visual C# / 可扩展性**和选择**Visual Studio 包**。 在**名称**在窗口底部字段中，命令文件名称更改为**FirstPackage.cs**。  
  
3.  生成项目并启动调试。  
  
     将显示 Visual Studio 的实验实例。 实验实例有关的详细信息，请参阅[实验实例](../extensibility/the-experimental-instance.md)。  
  
4.  在实验实例中，打开**工具 / 扩展和更新**窗口。 你应该会看到**FirstPackage**此处扩展。 (如果你打开**扩展和更新**在你的 Visual Studio 工作情况下，不会看到**FirstPackage**)。  
  
## <a name="loading-the-vspackage"></a>加载 VSPackage  
 在此点扩展不会加载，因为无需进行任何会导致它加载。 （单击打开工具窗口的菜单命令），其 UI 或通过指定 VSPackage，应在特定的 UI 上下文中加载交互时，通常可以加载扩展。 有关加载 Vspackage 和 UI 上下文的详细信息，请参阅[加载 Vspackage](../extensibility/loading-vspackages.md)。 对于此过程，我们将向你展示如何加载 VSPackage，打开解决方案时。  
  
1.  打开 FirstPackage.cs 文件。 查找 FirstPackage 类的声明。 替换以下内容的现有属性：  
  
    ```csharp  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About  
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]  
    [Guid(FirstPackageGuids.PackageGuidString)]  
    public sealed class FirstPackage : Package  
    ```  
  
2.  让我们添加一条消息，让我们知道已加载 VSPackage。 我们使用 VSPackage 的 initialize （） 方法来执行此操作，因为只有在已放置 VSPackage 后，你可以获取 Visual Studio 服务。 (有关获取服务的详细信息，请参阅[如何： 获取服务](../extensibility/how-to-get-a-service.md)。)Initialize （） 方法的 FirstPackage 替换代码，用于获取<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>服务，获取<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>接口，并调用其<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowMessageBox%2A>方法。  
  
    ```csharp  
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
  
3.  生成项目并启动调试。 实验实例中出现。  
  
4.  在实验实例中打开的解决方案。 你应看到显示一个消息框**第一个包内 initialize （)**。