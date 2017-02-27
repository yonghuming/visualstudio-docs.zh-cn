---
title: "提供命令 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "菜单 [Visual Studio SDK] 命令"
  - "最佳实践、 菜单和工具栏命令"
  - "工具栏 [Visual Studio]，最佳做法"
  - "菜单命令，最佳做法"
ms.assetid: 3ffc4312-c6db-4759-a946-a4bb85f4a17a
caps.latest.revision: 35
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 35
---
# 提供命令
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

当多个 VSPackages 迁移添加到 Visual Studio 时，用户界面 \(UI\) 可能会变得 overcrowded 使用命令。 你可以编程，您的包，以帮助减少此问题，如下所示:  
  
-   程序包，以便它仅在才加载用户需要它。  
  
-   编程包，以便只在他们可能需要在集成的开发环境 \(IDE\) 的当前状态的上下文中时，会显示其命令。  
  
## 延迟加载  
 若要启用的典型方式延迟加载是设计 VSPackage，以便其命令显示在 UI 中，但直到用户单击其中一个命令不会加载包本身。 若要实现此目的，在.vsct 文件中，创建命令，并不提供任何命令标志。  
  
 下面的示例演示.vsct 文件中的菜单命令的定义。 这是由 Visual Studio 包模板生成的命令时 **菜单命令** 选择模板中的选项。  
  
 [!CODE [TopLevelMenu#03](../CodeSnippet/VS_Snippets_VSSDK/toplevelmenu#03)]  
  
 在示例中，如果父组， `MyMenuGroup`, ，如是一个顶级菜单的子节点 **工具** 菜单上，该命令将显示在该菜单上，但执行该命令的包将不会加载，直到被用户单击该命令。 但是，通过编程来实现的命令 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 接口，可以使包可以在第一次展开的菜单中包含的命令时加载。  
  
 请注意延迟的加载还可以改善启动性能。  
  
## 当前上下文和命令的可见性  
 您可以编程 VSPackage 命令为可见或隐藏的具体取决于 VSPackage 数据或当前相关的操作的当前状态。 您可以启用 VSPackage 若要设置其命令的状态通常是通过使用实现 <xref:EnvDTE.IDTCommandTarget.QueryStatus%2A> 方法从 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 接口，但这需要 VSPackage，才会加载它可以执行的代码。 相反，我们建议您使 IDE 能够管理命令的可见性，而不加载包。 为此，请在.vsct 文件中，将与一个或多个特殊的 UI 上下文相关联的命令。 这些 UI 上下文由 GUID 标识称为 *命令上下文 GUID*。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 监视而导致的用户操作，例如加载项目，还是要从编辑到生成的更改。 发生更改时，将自动修改 IDE 的外观。 下表显示了四个主要 IDE 上下文更改 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 监视器。  
  
|上下文的类型|描述|  
|------------|--------|  
|活动项目类型|对于大多数项目类型，这 `GUID` 值并作为 VSPackage 实现项目的 GUID 相同。 但是， [!INCLUDE[vcprvc](../../debugger/includes/vcprvc_md.md)] 项目使用的项目类型 `GUID` 作为值。|  
|活动窗口|通常情况下，这是建立键绑定的当前 UI 上下文的最后一个活动文档窗口。 但是，这也可能是一个工具窗口，有一个类似于内部的 Web 浏览器的键绑定表。 对于多选项卡式文档窗口 HTML 编辑器等编辑器，每个选项卡均有一个不同的命令上下文 `GUID`。|  
|活动的语言服务|与当前显示在文本编辑器中的文件相关联的语言服务。|  
|活动工具窗口|工具窗口处于打开状态且具有焦点。|  
  
 第五个主要的上下文区域是 IDE 的 UI 状态。 UI 上下文由活动命令上下文 `GUID`s，如下所示:  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_SolutionBuilding>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_Debugging>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_Dragging>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_FullScreenMode>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_DesignMode>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_NoSolution>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_SolutionExists>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_EmptySolution>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_SolutionHasSingleProject>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_SolutionHasMultipleProjects>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_CodeWindow>  
  
 这些 Guid 被标记为活动或非活动，具体取决于 IDE 的当前状态。 多个 UI 上下文可以同时处于活动状态。  
  
### 隐藏和显示基于上下文的命令  
 可以显示或隐藏在 IDE 中的包命令，而不加载包本身。 若要执行此操作，该命令在.vsct 文件的包中使用定义 `DefaultDisabled`, ，`DefaultInvisible`, ，和 `DynamicVisibility` 命令标志和添加一个或多个 [VisibilityItem](../../extensibility/visibilityitem-element.md) 元素与 [VisibilityConstraints](../../extensibility/visibilityconstraints-element.md) 部分。 当指定的命令上下文 `GUID` 将变为活动状态时，该命令，显示不包含将包加载。  
  
### 自定义上下文 Guid  
 如果尚未定义 GUID 不适当的命令上下文中，您可以在你的 VSPackage 中定义，然后编写其成为活动状态还是处于非活动状态所需控制命令的可见性。 使用 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> 服务:  
  
-   注册上下文 Guid \(通过调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A> 方法\)。  
  
-   获取状态的上下文 `GUID` \(通过调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> 方法\)。  
  
-   打开上下文 `GUID`s 打开和关闭 \(通过调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A> 方法\)。  
  
    > [!CAUTION]
    >  请确保你的 VSPackage 不因为其他 Vspackage 可能依赖这些影响任何现有上下文 GUID 的状态。  
  
## 示例  
 VSPackage 命令的下面的示例演示的动态可见性由命令上下文而不加载 VSPackage 的命令。  
  
 该命令设置为处于启用状态并存在一种解决方案，则每当显示也就是说，只要下列命令行上下文的 Guid 之一处于活动状态:  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_EmptySolution>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_SolutionHasMultipleProjects>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_SolutionHasSingleProject>  
  
 在本示例中，请注意每个命令标志是一个单独 [的命令标志](../../extensibility/command-flag-element.md) 元素。  
  
 [!CODE [DynamicVisibility#01](DynamicVisibility#01)]  
  
 此外请注意，必须在单独授予每个 UI 上下文 `VisibilityItem` 元素，如下所示。  
  
 [!CODE [DynamicVisibility#02](DynamicVisibility#02)]  
  
## 请参阅  
 [MenuCommands 与 OleMenuCommands](../../misc/menucommands-vs-olemenucommands.md)   
 [Vspackage 如何添加用户界面元素](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Vspackage 中的命令传送](../../extensibility/internals/command-routing-in-vspackages.md)   
 [动态添加菜单项](../../extensibility/dynamically-adding-menu-items.md)