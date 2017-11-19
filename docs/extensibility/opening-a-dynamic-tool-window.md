---
title: "打开动态工具窗口 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: tool windows, dynamic
ms.assetid: 21547ba7-6e81-44df-9277-265bf34f877a
caps.latest.revision: "21"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 588badc75a604df65949c99fa16f84ad4e9c9175
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="opening-a-dynamic-tool-window"></a>打开动态工具窗口
从菜单中或等效的键盘快捷方式上的命令通常打开工具窗口。 有时，但是，你可能需要打开每当特定的 UI 上下文适用，并且 UI 上下文不再适用时，将关闭的工具窗口。 类似这样的工具窗口称为*动态*或*自动可见*。  
  
> [!NOTE]
>  有关预定义的 UI 上下文的列表，请参阅<xref:Microsoft.VisualStudio.VSConstants.UICONTEXT>。 有关  
  
 如果你想要打开在启动时，动态工具窗口，并且可以用于创建失败，则必须实现<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwnerEx>接口，并在测试中的失败条件<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwnerEx.QueryShowTool%2A>方法。 在外壳程序知道你有一个动态工具窗口，应在启动时打开的顺序，你必须添加`SupportsDynamicToolOwner`对包注册 （设为 1） 的值。 此值不是标准的一部分<xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>，因此你必须创建要将其添加的自定义属性。 有关自定义特性的详细信息，请参阅[使用自定义注册特性注册扩展](../extensibility/registering-and-unregistering-vspackages.md#using-a-custom-registration-attribute-to-register-an-extension)。  
  
 使用<xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A>以打开工具窗口。 根据需要创建工具窗口。  
  
> [!NOTE]
>  可以由用户关闭了动态工具窗口。 如果你想要创建菜单命令，以便用户可以重新打开工具窗口，应在相同的 UI 上下文，这将打开工具窗口以及禁用否则为中启用菜单命令。  
  
### <a name="to-open-a-dynamic-tool-window"></a>若要打开动态工具窗口  
  
1.  创建一个名为的 VSIX 项目**DynamicToolWindow**并添加名为的工具窗口项模板**DynamicWindowPane.cs**。 有关详细信息，请参阅[使用工具窗口创建扩展](../extensibility/creating-an-extension-with-a-tool-window.md)。  
  
2.  在 DynamicWindowPanePackage.cs 文件中查找 DynamicWindowPanePackage 声明。 添加<xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute>和 T:Microsoft.VisualStudio.Shell.ProvideToolWindowVisibilityAttribute 属性，以注册工具窗口。  
  
    ```vb  
    [[ProvideToolWindow(typeof(DynamicWindowPane)]  
    [ProvideToolWindowVisibility(typeof(DynamicWindowPane), VSConstants.UICONTEXT.SolutionExists_string)]  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About  
    [ProvideMenuResource("Menus.ctmenu", 1)]  
    [ProvideToolWindow(typeof(DynamicToolWindow.DynamicWindowPane))]  
    [Guid(DynamicWindowPanePackageGuids.PackageGuidString)]  
    public sealed class DynamicWindowPanePackage : Package  
    {. . .}  
    ```  
  
     这将会注册命名 DynamicWindowPane 为一个暂时性的窗口，其中后关闭并重新打开 Visual Studio 并不会保持该工具窗口。 打开 DynamicWindowPane 每当<xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_string>应用，并且否则关闭。  
  
3.  生成项目并启动调试。 应显示的实验实例。 不应看到工具窗口。  
  
4.  在实验实例中打开一个项目。 应显示该工具窗口。