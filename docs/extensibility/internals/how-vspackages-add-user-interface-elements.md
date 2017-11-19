---
title: "Vspackage 如何添加用户界面元素 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- user interfaces, adding elements
- UI element design [Visual Studio SDK], VSPackages
- VSPackages, contributing UI elements
ms.assetid: abc5d9d9-b267-48a1-92ad-75fbf2f4c1b9
caps.latest.revision: "60"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 171a31147aec5c0477d6a23e73dc0e66693b534d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-vspackages-add-user-interface-elements"></a>Vspackage 如何添加用户界面元素
VSPackage 可以添加用户界面 (UI) 元素，例如，菜单、 工具栏和工具窗口，到 Visual Studio 通过.vsct 文件。  
  
 UI 元素时，可查找设计准则[Visual Studio 用户体验指南](../../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md)。  
  
## <a name="the-visual-studio-command-table-architecture"></a>Visual Studio 命令表体系结构  
 如所述，命令表体系结构支持前面提到的体系结构原理。 后面的抽象，数据结构和工具的命令表体系结构的条原则是，如下所示：  
  
-   有三种基本类型的项： 菜单、 命令和组。 作为菜单、 子菜单、 工具栏或工具窗口，可以在 UI 中公开菜单。 命令是用户可以执行在 IDE 中，以及它们可作为菜单项、 按钮、 列表框或其他控件公开的过程。 组是菜单和命令的容器。  
  
-   每个项指定描述项目、 相对于其他项和修改其行为的标志其优先级的定义。  
  
-   每个项具有描述项的父级位置。 项可以有多个父级，以便它可以出现在 UI 中的多个位置。  
  
     每个命令必须具有与其父组，即使该组中的唯一子级。 每个标准菜单还必须具有父组。 工具栏和工具窗口充当自己的父项。 一组可有其父主 Visual Studio 菜单栏上，或任何菜单、 工具栏或工具窗口。  
  
### <a name="how-items-are-defined"></a>如何定义项  
 .Vsct 文件采用 XML 格式。 .Vsct 文件定义包的 UI 元素，并确定这些元素出现在 IDE 中的位置。 每个菜单、 组或包中的命令是首次分配的 GUID 和 ID 中的`Symbols`部分。 在剩下的.vsct 文件、 每个菜单、 命令和组都由其 GUID 和 ID 组合标识。 以下示例演示一个典型`Symbols`部分，如生成的 Visual Studio 包模板时**菜单命令**在模板中选择。  
  
```xml  
<Symbols>  
  <!-- This is the package guid. -->  
  <GuidSymbol name="guidMenuTextPkg" value="{b1253bc6-d266-402b-89e7-5e3d3b22c746}" />  
  
  <!-- This is the guid used to group the menu commands together -->  
  <GuidSymbol name="guidMenuTextCmdSet" value="{a633d4e4-6c65-4436-a138-1abeba7c9a69}">  
  
    <IDSymbol name="MyMenuGroup" value="0x1020" />  
    <IDSymbol name="cmdidMyCommand" value="0x0100" />  
  </GuidSymbol>  
  
  <GuidSymbol name="guidImages" value="{53323d9a-972d-4671-bb5b-9e418480922f}" >  
    <IDSymbol name="bmpPic1" value="1" />  
    <IDSymbol name="bmpPic2" value="2" />  
    <IDSymbol name="bmpPicSearch" value="3" />  
    <IDSymbol name="bmpPicX" value="4" />  
    <IDSymbol name="bmpPicArrows" value="5" />  
  </GuidSymbol>  
</Symbols>  
```  
  
 顶级元素`Symbols`部分[GuidSymbol 元素](../../extensibility/guidsymbol-element.md)。 `GuidSymbol`元素名称映射到 IDE 用于标识包和其组成部分的 Guid。  
  
> [!NOTE]
>  Visual Studio 包模板自动生成 Guid。 你还可以通过单击创建的唯一 GUID**创建 GUID**上**工具**菜单。  
  
 第一个`GuidSymbol`元素，"guid [PackageName] Pkg"，是包本身的 GUID。 这是 Visual Studio 用于加载包的 GUID。 通常情况下，它没有子元素。  
  
 按照约定，菜单和命令已归入第二个`GuidSymbol`元素，"guid [PackageName] CmdSet"，并且位图下第三个`GuidSymbol`元素中，"guidImages"。 不需要遵循此约定，但每个菜单、 组、 命令和位图必须的子级`GuidSymbol`元素。  
  
 在第二个`GuidSymbol`元素，它表示包命令集，有几个`IDSymbol`元素。 每个[IDSymbol 元素](../../extensibility/idsymbol-element.md)将名称映射为数字值，并且可能反映菜单、 组或是命令集的一部分的命令。 `IDSymbol`中第三个元素`GuidSymbol`可能用于命令以图标形式的元素表示位图。 因为 GUID/ID 对必须是唯一的应用程序，任何两个子级的相同`GuidSymbol`元素可能具有相同的值。  
  
### <a name="menus-groups-and-commands"></a>菜单、 组和命令  
 当菜单、 组或命令具有 GUID 和 ID 时，它可以添加到 IDE 中。 每个 UI 元素必须具有以下操作：  
  
-   A`guid`匹配的名称属性`GuidSymbol`下定义的用户界面元素的元素。  
  
-   `id`与关联的名称匹配的属性`IDSymbol`元素。  
  
     在一起，`guid`和`id`属性撰写*签名*的 UI 元素。  
  
-   A`priority`确定了其父菜单或组中的 UI 元素的位置的属性。  
  
-   A[父元素](../../extensibility/parent-element.md)具有`guid`和`id`指定的签名的父菜单或组的属性。  
  
#### <a name="menus"></a>菜单  
 每个菜单指[Menu 元素](../../extensibility/menu-element.md)中`Menus`部分。 菜单必须具有`guid`， `id`，和`priority`特性，和一个`Parent`元素，还的以下其他属性和子级：  
  
-   A`type`属性，指定是否应在 IDE 中作为一种类型的菜单或工具栏显示菜单。  
  
-   A[字符串元素](../../extensibility/strings-element.md)包含[ButtonText 元素](../../extensibility/buttontext-element.md)，它指定在 IDE 中的菜单标题和[CommandName 元素](../../extensibility/commandname-element.md)，它指定的名称在中使用**命令**窗口来访问菜单。  
  
-   可选标志。 A[命令标志元素](../../extensibility/command-flag-element.md)可能在要更改其外观或行为在 IDE 中的菜单定义中出现。  
  
 每个`Menu`元素必须有一组作为其父级，除非它是如工具栏可停靠元素。 可停靠的菜单是其自身的上级。 有关菜单和值的详细信息`type`属性，请参阅[Menu 元素](../../extensibility/menu-element.md)文档。  
  
 下面的示例演示一个菜单，将出现在 Visual Studio 菜单栏上，接下来**工具**菜单。  
  
```xml  
<Menu guid="guidTopLevelMenuCmdSet"  
id="TopLevelMenu" priority="0x700" type="Menu">  
  <Parent guid="guidSHLMainMenu"  
          id="IDG_VS_MM_TOOLSADDINS" />  
  <Strings>  
    <ButtonText>TestMenu</ButtonText>  
    <CommandName>TestMenu</CommandName>  
  </Strings>  
</Menu>  
```  
  
#### <a name="groups"></a>组  
 组是在中定义的项`Groups`.vsct 文件的部分。 组是只是容器。 它们不会出现在 IDE 中，除为菜单上分隔线。 因此，[组元素](../../extensibility/group-element.md)仅由其签名、 优先级和父定义。  
  
 一组只能有一个菜单、 另一个组，或本身作为父级。 但是，父级通常是将菜单或工具栏。 前面示例中的菜单是的子级`IDG_VS_MM_TOOLSADDINS`组，并且该组是 Visual Studio 菜单栏的子级。 下面的示例中的组是菜单的前面示例中的子级。  
  
```  
 <Group guid="guidTopLevelMenuCmdSet" id="MyMenuGroup"  
priority="0x0600">  
   <Parent guid="guidTopLevelMenuCmdSet" id="TopLevelMenu"/>  
 </Group>  
```  
  
 因为它是菜单的一部分，则此组将通常包含命令。 但是，它可能还包含其他菜单。 这是子菜单的定义方式，如下面的示例中所示。  
  
```xml  
<Menu guid="guidTopLevelMenuCmdSet" id="SubMenu"  
priority="0x0100" type="Menu">  
  <Parent guid="guidTopLevelMenuCmdSet" id="MyMenuGroup"/>  
  <Strings>  
    <ButtonText>Sub Menu</ButtonText>  
    <CommandName>Sub Menu</CommandName>  
  </Strings>  
</Menu>  
```  
  
#### <a name="commands"></a>命令  
 为 IDE 提供的命令定义为[Button 元素](../../extensibility/button-element.md)或[组合元素](../../extensibility/combo-element.md)。 要显示在菜单或工具栏上，该命令必须具有与其父组。  
  
##### <a name="buttons"></a>按钮  
 在中定义按钮`Buttons`部分。 任何菜单项、 按钮或在用户单击以执行单个命令的其他元素被视为一个按钮。 某些按钮类型还可以包含列表功能。 按钮具有相同所需和菜单具有的可选属性，也可以有[图标元素](../../extensibility/icon-element.md)，它指定的 GUID 和用于表示在 IDE 中的按钮的位图的 ID。 有关按钮和及其属性的详细信息，请参阅[按钮元素](../../extensibility/buttons-element.md)文档。  
  
 下面的示例中的按钮在前面的示例中，组的子级，并且将在 IDE 中显示为该组的父菜单中的菜单项。  
  
```  
<Button guid="guidTopLevelMenuCmdSet" id="cmdidTestCommand" priority="0x0100" type="Button">  
  <Parent guid="guidTopLevelMenuCmdSet" id="MyMenuGroup" />  
  <Icon guid="guidImages" id="bmpPic1" />  
  <Strings>  
    <CommandName>cmdidTestCommand</CommandName>  
    <ButtonText>Test Command</ButtonText>  
  </Strings>  
</Button>  
```  
  
##### <a name="combos"></a>组合  
 在中定义组合`Combos`部分。 每个`Combo`元素表示在 IDE 中的下拉列表框。 列表框可能或可能不是可写入的用户，具体取决于值`type`属性的组合。 组合具有相同的元素和按钮的行为，并且可以具有以下其他属性：  
  
-   A`defaultWidth`属性，指定像素宽度。  
  
-   `idCommandList`属性，指定包含在列表框中显示的项的列表。 必须在同一声明命令列表`GuidSymbol`包含组合的节点。  
  
 下面的示例定义的组合元素。  
  
```xml  
<Combos>  
  <Combo guid="guidFirstToolWinCmdSet"  
         id="cmdidWindowsMediaFilename"  
         priority="0x0100" type="DynamicCombo"  
         idCommandList="cmdidWindowsMediaFilenameGetList"  
         defaultWidth="130">  
    <Parent guid="guidFirstToolWinCmdSet"  
            id="ToolbarGroupID" />  
    <CommandFlag>IconAndText</CommandFlag>  
    <CommandFlag>CommandWellOnly</CommandFlag>  
    <CommandFlag>StretchHorizontally</CommandFlag>  
    <Strings>  
      <CommandName>Filename</CommandName>  
      <ButtonText>Enter a Filename</ButtonText>  
    </Strings>  
  </Combo>  
</Combos>  
```  
  
##### <a name="bitmaps"></a>位图  
 将与一个图标一起显示的命令必须包括`Icon`通过使用其 GUID 和 id。 是指位图的元素 每个位图定义为[位图元素](../../extensibility/bitmap-element.md)中`Bitmaps`部分。 唯一所需的属性为`Bitmap`定义都包含`guid`和`href`，了指向源文件。 如果源文件是一个资源条， **usedList**属性也是必需的若要列出可用的映像的栏中。 有关详细信息，请参阅[位图元素](../../extensibility/bitmap-element.md)文档。  
  
### <a name="parenting"></a>设置父级  
 以下规则将管理如何项可以调用另一个作为其父项。  
  
|元素|在本节中的命令表定义|可能包含 (作为父项，或通过中的放置位置来`CommandPlacements`部分中，和/或文件名)|可能包含 （也称为父）|  
|-------------|--------------------------------------------------|---------------------------------------------------------------------------------------------------|---------------------------------------------|  
|Group|[Groups 元素](../../extensibility/groups-element.md)，IDE、 其他 Vspackage|菜单上，一个组，针对项本身|菜单、 组和命令|  
|菜单|[菜单元素](../../extensibility/menus-element.md)，IDE、 其他 Vspackage|1 到 *n* 组|0 到 *n* 组|  
|Toolbar|[菜单元素](../../extensibility/menus-element.md)，IDE、 其他 Vspackage|针对项本身|0 到 *n* 组|  
|菜单项|[按钮元素](../../extensibility/buttons-element.md)，IDE、 其他 Vspackage|1 到 *n* 组，而针对项本身|-0 到 *n* 组|  
|Button|[按钮元素](../../extensibility/buttons-element.md)，IDE、 其他 Vspackage|1 到 *n* 组，而针对项本身||  
|组合|[组合元素](../../extensibility/combos-element.md)，IDE、 其他 Vspackage|1 到 *n* 组，而针对项本身||  
  
### <a name="menu-command-and-group-placement"></a>菜单、 命令和组放置  
 菜单、 组或命令可以出现在 IDE 中的多个位置中。 在多个位置显示的项，必须将它添加到`CommandPlacements`部分作为[CommandPlacement 元素](../../extensibility/commandplacement-element.md)。 可以作为命令放置添加任何菜单、 组或命令。 但是，工具栏不能以这种方式定位因为它们不能出现在多个上下文相关的位置。  
  
 命令放置具有`guid`， `id`，和`priority`属性。 GUID 和 ID 必须与匹配的定位的项。 `priority`属性控制与其他项的项的位置。 当 IDE 合并两个或多个具有相同的优先级的项时，其放置不确定的因为 IDE 不保证，程序包资源读取相同顺序生成包每次。  
  
 如果菜单或组出现在多个位置，该菜单或组的所有子级将都出现在每个实例。  
  
## <a name="command-visibility-and-context"></a>命令的可见性和上下文  
 当安装多个 Vspackage 时，大量的菜单、 菜单项和工具栏可能会使 IDE 显得杂乱。 若要避免此问题，可以控制各个 UI 元素的可见性使用*可见性约束*和命令标志。  
  
##### <a name="visibility-constraints"></a>可见性约束  
 可见性约束设置为[VisibilityItem 元素](../../extensibility/visibilityitem-element.md)中`VisibilityConstraints`部分。 可见性约束定义特定 UI 上下文的目标项处于可见。 仅当定义的上下文中的一个处于活动状态，菜单或包括在本部分的命令才可见。 如果本部分中未引用的菜单或命令，将始终默认情况下可见。 本节不适用于组。  
  
 `VisibilityItem`元素必须具有三个特性，如下所示：`guid`和`id`的目标 UI 元素，并`context`。 `context`属性指定当目标项将是可见的并采用任何有效的 UI 上下文作为其值。 Visual Studio 的 UI 上下文常量属于<xref:Microsoft.VisualStudio.VSConstants>类。 每个`VisibilityItem`元素接受只有一个上下文的值。 若要应用的第二个上下文，创建第二个`VisibilityItem`指向同一个项，如下面的示例中所示的元素。  
  
```xml  
<VisibilityConstraints>  
  <VisibilityItem guid="guidSolutionToolbarCmdSet"  
        id="cmdidTestCmd"  
        context="UICONTEXT_SolutionHasSingleProject" />  
  <VisibilityItem guid="guidSolutionToolbarCmdSet"  
        id="cmdidTestCmd"  
        context="UICONTEXT_SolutionHasMultipleProjects" />  
</VisibilityConstraints>  
```  
  
##### <a name="command-flags"></a>命令标志  
 下面的命令标志可能会影响菜单和它们适用于命令的可见性。  
  
 AlwaysCreate  
 即使它具有任何组或按钮创建菜单。  
  
 适用于：`Menu`  
  
 CommandWellOnly  
 将应用此标志如果该命令不显示在顶级菜单上，你想要使其可供其他外壳自定义设置，例如，将其绑定到一个密钥。 安装 VSPackage 后，用户可以通过自定义这些命令打开**选项**对话框中，然后编辑下的命令放置**键盘环境**类别。 不会影响在快捷菜单、 工具栏、 菜单控制器或子菜单上的位置。  
  
 有关有效： `Button`，`Combo`  
  
 DefaultDisabled  
 默认情况下，如果未加载 VSPackage 实现命令或者尚未调用 QueryStatus 方法，则禁用该命令。  
  
 有关有效： `Button`，`Combo`  
  
 DefaultInvisible  
 默认情况下，该命令是不可见，如果未加载 VSPackage 实现命令或者尚未调用 QueryStatus 方法。  
  
 应结合`DynamicVisibility`标志。  
  
 有关有效： `Button`， `Combo`，`Menu`  
  
 DynamicVisibility  
 可以使用 QueryStatus 方法或上下文中包含的 GUID 更改该命令的可见性`VisibilityConstraints`部分。  
  
 适用于在菜单中，不在工具栏显示的命令。 可以禁用，但不是能隐藏 OLECMDF_INVISIBLE 标志从 QueryStatus 方法返回时顶层工具栏项。  
  
 在菜单上，此标志还指示，它应被自动隐藏隐藏其成员时。 因为顶级菜单中已有此行为，此标志通常会分派给子菜单。  
  
 应结合`DefaultInvisible`标志。  
  
 有关有效： `Button`， `Combo`，`Menu`  
  
 NoShowOnMenuController  
 如果命令具有此标志位于菜单控制器，该命令不出现在下拉列表中。  
  
 适用于：`Button`  
  
 有关命令标志的详细信息，请参阅[命令标志元素](../../extensibility/command-flag-element.md)文档。  
  
##### <a name="general-requirements"></a>一般要求  
 你的命令必须通过以下一系列测试，然后可以显示并启用：  
  
-   正确定位该命令。  
  
-   `DefaultInvisible`未设置标志。  
  
-   该父菜单或工具栏可见。  
  
-   此命令不可见由于中的上下文项[VisibilityConstraints 元素](../../extensibility/visibilityconstraints-element.md)部分。  
  
-   实现的 VSPackage 代码<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>接口显示，并使你的命令。 没有接口代码截获此和已按照它。  
  
-   当用户单击你的命令时，则它将成为受中概述的过程[路由算法](../../extensibility/internals/command-routing-algorithm.md)。  
  
## <a name="calling-pre-defined-commands"></a>调用预定义的命令  
 [UsedCommands 元素](../../extensibility/usedcommands-element.md)使 Vspackage 能够访问其他 Vspackage 或由 IDE 提供的命令。 若要执行此操作，创建[UsedCommand 元素](../../extensibility/usedcommand-element.md)具有 GUID 和要使用的命令 ID。 这确保该命令，将加载的 Visual Studio 中，即使它不是当前的 Visual Studio 配置的一部分。 有关详细信息，请参阅[UsedCommand 元素](../../extensibility/usedcommand-element.md)。  
  
## <a name="interface-element-appearance"></a>界面元素外观  
 选择和定位命令元素的注意事项如下所示：  
  
-   [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]提供以不同方式显示，具体取决于放置的许多 UI 元素。  
  
-   UI 元素定义的使用`DefaultInvisible`标志将不会显示在 IDE 除非它是由其 VSPackage 实现显示<xref:EnvDTE.IDTCommandTarget.QueryStatus%2A>方法，或与中的特定 UI 上下文关联`VisibilityConstraints`部分。  
  
-   即使成功定位的命令可能不会显示。 这是因为 IDE 自动隐藏或显示一些命令，具体取决于 VSPackage 不含 （或不包含） 的接口实现的。 例如，VSPackage 的实现的一些生成界面原因与生成相关的菜单项来自动显示。  
  
-   应用`CommandWellOnly`的命令，可以添加仅通过自定义的 UI 元素的定义中的标记表示。  
  
-   仅当 IDE 时在设计视图中显示一个对话框时，可能仅在某些 UI 上下文中，例如中, 可用命令。  
  
-   若要使某些用户界面元素在 IDE 中显示，必须实现一个或多个接口，或编写一些代码。  
  
## <a name="see-also"></a>另请参阅  
 [扩展菜单和命令](../../extensibility/extending-menus-and-commands.md)