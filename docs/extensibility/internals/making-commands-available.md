---
title: "使命令可 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- menus [Visual Studio SDK], commands
- best practices, menu and toolbar commands
- toolbars [Visual Studio], best practices
- menu commands, best practices
ms.assetid: 3ffc4312-c6db-4759-a946-a4bb85f4a17a
caps.latest.revision: "35"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6e9644353430fa70d6876ab3210ad340ac30312d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="making-commands-available"></a>使命令可
当多个 Vspackage 添加到 Visual Studio 时，用户界面 (UI) 可能会变得 overcrowded 使用命令。 你可以编程包以减少此问题，如下所示：  
  
-   包的程序，以便仅当用户加载需要它。  
  
-   编程包，以便仅在它们可能需要在集成的开发环境 (IDE) 的当前状态的上下文中时，会显示其命令。  
  
## <a name="delayed-loading"></a>延迟加载  
 若要启用的典型方法延迟加载是设计 VSPackage，以便其命令显示在 UI 中，但直到用户单击其中一个命令包本身不会加载。 若要实现此目的，.vsct 文件中，创建不具有任何命令标志的命令。  
  
 下面的示例演示.vsct 文件中的菜单命令的定义。 这是由 Visual Studio 包模板生成的命令时**菜单命令**选择模板中的选项。  
  
```xml  
<Button guid="guidTopLevelMenuCmdSet" id="cmdidTestCommand" priority="0x0100" type="Button">  
  <Parent guid="guidTopLevelMenuCmdSet" id="MyMenuGroup" />  
  <Icon guid="guidImages" id="bmpPic1" />  
  <Strings>  
    <CommandName>cmdidTestCommand</CommandName>  
    <ButtonText>Test Command</ButtonText>  
  </Strings>  
</Button>  
  
```  
  
 在示例中，如果父组， `MyMenuGroup`，如是顶级菜单的子级**工具**菜单上，将可看到在该菜单上，该命令，但将不加载的包执行的命令，直到单击该命令由用户。 但是，通过编程来实现命令<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>接口，你可以使包可以首先展开包含该命令的菜单时加载。  
  
 请注意延迟的加载还可以提高启动性能。  
  
## <a name="current-context-and-the-visibility-of-commands"></a>当前上下文和命令的可见性  
 你可以编程 VSPackage 命令是可见还是隐藏的具体取决于 VSPackage 数据或当前相关的操作的当前状态。 你可以使 VSPackage 可以设置其命令的状态通常是通过使用实现<xref:EnvDTE.IDTCommandTarget.QueryStatus%2A>方法从<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>接口，但这需要 VSPackage，才会加载它可以执行代码。 相反，我们建议你启用 IDE 以不将包加载的情况下管理命令的可见性。 为此，请.vsct 文件中，请将命令与一个或多个特殊的 UI 上下文相关联。 由名为 GUID 标识这些 UI 上下文*命令上下文 GUID*。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]监视因用户操作如加载项目或从编辑转到生成的更改。 发生更改，则自动修改 IDE 的外观。 下表显示 IDE 的以下四种主要上下文更改[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]监视器。  
  
|类型的上下文|描述|  
|---------------------|-----------------|  
|活动项目类型|对于大多数项目类型，这`GUID`值均为 VSPackage 实现项目的 GUID 相同。 但是，[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]项目使用项目类型`GUID`作为值。|  
|活动窗口|通常，这是建立键绑定的当前 UI 上下文的最后一个活动文档窗口。 但是，这也可能是该工具窗口具有类似于内部的 Web 浏览器的键绑定表。 对于多选项卡式文档窗口 （如 HTML 编辑器），每个选项卡将具有不同的命令上下文`GUID`。|  
|活动的语言服务|语言服务与当前显示在文本编辑器中的文件关联。|  
|活动工具窗口|工具窗口处于打开状态且具有焦点。|  
  
 第五个主要上下文区域是 IDE 的 UI 状态。 UI 上下文由活动命令上下文`GUID`s，如下所示：  
  
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
  
### <a name="hiding-and-displaying-commands-based-on-context"></a>隐藏和显示基于上下文的命令  
 你可以显示或隐藏在 IDE 中的包命令，而不加载包本身。 若要这样做，请定义该命令包的.vsct 文件中使用`DefaultDisabled`， `DefaultInvisible`，和`DynamicVisibility`命令标志和添加一个或多个[VisibilityItem](../../extensibility/visibilityitem-element.md)元素与[VisibilityConstraints](../../extensibility/visibilityconstraints-element.md)部分。 当指定的命令上下文`GUID`变为活动状态，该命令将显示不加载包。  
  
### <a name="custom-context-guids"></a>自定义上下文 Guid  
 如果不合适的命令上下文中尚未定义的 GUID，你可以定义一个在你的 VSPackage，然后程序其成为活动或非活动所需控制你的命令的可见性。 使用<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>服务来：  
  
-   注册上下文 Guid (通过调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A>方法)。  
  
-   获取上下文的状态`GUID`(通过调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A>方法)。  
  
-   打开上下文`GUID`s 打开和关闭 (通过调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A>方法)。  
  
    > [!CAUTION]
    >  请确保你的 VSPackage 不因为其他 Vspackage 可能依赖于它们影响任何现有上下文 GUID 的状态。  
  
## <a name="example"></a>示例  
 VSPackage 命令的下面的示例演示的动态可见性由命令上下文而不加载 VSPackage 的命令。  
  
 该命令设置为处于启用状态并显示每当解决方案存在;即，每当下面的命令上下文 Guid 之一处于活动状态：  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_EmptySolution>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_SolutionHasMultipleProjects>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_SolutionHasSingleProject>  
  
 在示例中，请注意，每个命令标志是单独[命令标志](../../extensibility/command-flag-element.md)元素。  
  
```  
<Button guid="guidDynamicVisibilityCmdSet" id="cmdidMyCommand"   
        priority="0x0100" type="Button">  
  <Parent guid="guidDynamicVisibilityCmdSet" id="MyMenuGroup" />  
  <Icon guid="guidImages" id="bmpPic1" />  
  <CommandFlag>DefaultDisabled</CommandFlag>  
  <CommandFlag>DefaultInvisible</CommandFlag>  
  <CommandFlag>DynamicVisibility</CommandFlag>  
  <Strings>  
    <CommandName>cmdidMyCommand</CommandName>  
    <ButtonText>My Command name</ButtonText>  
  </Strings>  
</Button>  
  
```  
  
 此外请注意，必须在单独指定每个 UI 上下文`VisibilityItem`元素，如下所示。  
  
```xml  
<VisibilityConstraints>  
  <VisibilityItem guid="guidDynamicVisibilityCmdSet"  
                  id="cmdidMyCommand" context="UICONTEXT_EmptySolution" />  
  <VisibilityItem guid="guidDynamicVisibilityCmdSet"  
                      id="cmdidMyCommand" context="UICONTEXT_SolutionHasSingleProject" />  
  <VisibilityItem guid="guidDynamicVisibilityCmdSet"  
                  id="cmdidMyCommand" context="UICONTEXT_SolutionHasMultipleProjects" />  
</VisibilityConstraints>  
  
```  
  
## <a name="see-also"></a>另请参阅  
 [MenuCommands 与OleMenuCommands](../../extensibility/menucommands-vs-olemenucommands.md)   
 [Vspackage 如何添加用户界面元素](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Vspackage 中的路由的命令](../../extensibility/internals/command-routing-in-vspackages.md)   
 [动态添加菜单项](../../extensibility/dynamically-adding-menu-items.md)