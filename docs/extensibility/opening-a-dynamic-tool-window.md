---
title: "打开动态工具窗口 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "工具窗口动态"
ms.assetid: 21547ba7-6e81-44df-9277-265bf34f877a
caps.latest.revision: 21
caps.handback.revision: 19
ms.author: "gregvanl"
manager: "ghogen"
---
# 打开动态工具窗口
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

从上一个菜单或等效的键盘快捷方式命令通常打开工具窗口。 有时，但是，您可能需要一个工具窗口，只要特定 UI 上下文应用，并关闭 UI 上下文不再应用时打开。 类似这样的工具窗口称为 *动态* 或 *自动可见*。  
  
> [!NOTE]
>  预定义的 UI 上下文中的列表，请参阅 <xref:Microsoft.VisualStudio.VSConstants.UIContext>。 有关  
  
 如果你想要打开在启动时，动态工具窗口，并且很可能无法创建，则必须实现 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwnerEx> 接口，并在测试中的失败条件 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwnerEx.QueryShowTool%2A> 方法。 为了使外壳程序知道有动态工具窗口应打开在启动时，必须将添加 `SupportsDynamicToolOwner` 程序包注册到 \(设置为 1\) 的值。 此值不是标准的一部分 <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>, ，因此您必须创建自定义属性以将其添加。 有关自定义特性的详细信息，请参阅 [使用自定义注册特性注册扩展](/visual-cpp/misc/using-a-custom-registration-attribute-to-register-an-extension)。  
  
 使用 <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> 若要打开工具窗口。 工具窗口是根据需要创建的。  
  
> [!NOTE]
>  可以由用户关闭动态工具窗口。 如果您想要创建菜单命令，以便用户可以重新打开工具窗口中，应将打开工具窗口，并已禁用以其他方式的同一个 UI 上下文中启用菜单命令。  
  
### 若要打开动态工具窗口  
  
1.  创建一个名为的 VSIX 项目 **DynamicToolWindow** 并添加一个名为的工具窗口项模板 **DynamicWindowPane.cs**。 有关详细信息，请参阅[使用一个工具窗口创建扩展](../extensibility/creating-an-extension-with-a-tool-window.md)。  
  
2.  在 DynamicWindowPanePackage.cs 文件中，找到 DynamicWindowPanePackage 声明。 添加 <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> 和 T:Microsoft.VisualStudio.Shell.ProvideToolWindowVisibilityAttribute 属性，以注册工具窗口中。  
  
    ```vb  
    [[ProvideToolWindow(typeof(DynamicWindowPane)] [ProvideToolWindowVisibility(typeof(DynamicWindowPane), VSConstants.UICONTEXT.SolutionExists_string)] [PackageRegistration(UseManagedResourcesOnly = true)] [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About [ProvideMenuResource("Menus.ctmenu", 1)] [ProvideToolWindow(typeof(DynamicToolWindow.DynamicWindowPane))] [Guid(DynamicWindowPanePackageGuids.PackageGuidString)] public sealed class DynamicWindowPanePackage : Package {. . .}  
    ```  
  
     这将注册工具窗口中命名 DynamicWindowPane 为后关闭并重新打开 Visual Studio 并不会保持一个瞬态窗口。 打开 DynamicWindowPane 每当 <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_string> 应用样式以及否则关闭。  
  
3.  生成项目并启动调试。 应显示的实验实例。 不应看到工具窗口中。  
  
4.  在实验实例中打开一个项目。 工具窗口中应显示。