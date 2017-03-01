---
title: "Vspackage 将用户界面元素的添加 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- user interfaces, adding elements
- UI element design [Visual Studio SDK], VSPackages
- VSPackages, contributing UI elements
ms.assetid: abc5d9d9-b267-48a1-92ad-75fbf2f4c1b9
caps.latest.revision: 60
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
ms.openlocfilehash: 6bf44a2b1fa029753c4b3c00f911070a2132bb75
ms.lasthandoff: 02/22/2017

---
# <a name="how-vspackages-add-user-interface-elements"></a>Vspackage 如何添加用户界面元素
VSPackage 可以添加用户界面 (UI) 元素，例如，菜单、 工具栏和工具窗口，到通过.vsct 文件的 Visual Studio。  
  
 查找用户界面元素出现在设计准则[Visual Studio 用户体验指南](../../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md)。  
  
## <a name="the-visual-studio-command-table-architecture"></a>Visual Studio 命令表体系结构  
 如前所述，命令表体系结构支持上述体系结构原则。 后面的抽象、 数据结构和工具的命令表体系结构原则是，如下所示︰  
  
-   有三种基本类型的项︰ 菜单、 命令和组。 可以在用户界面以菜单、 子菜单、 工具栏或工具窗口显示菜单。 命令是用户可以执行在 IDE 中，并且它们可以公开为菜单项、 按钮、 列表框或其他控件的过程。 组是菜单和命令的容器。  
  
-   每个项目指定描述项目、 相对于其他项和修改其行为的标志其优先级的定义。  
  
-   每个项都有描述项的父级的放置。 项可以有多个父项，以便它可以显示在 UI 中的多个位置。  
  
     每个命令必须作为其父项，具有一个组，即使它是该组中的唯一子级。 每个标准菜单还必须具有父组。 工具栏和工具窗口充当自己的父项。 一组可将作为其父主 Visual Studio 菜单栏中，或任何菜单、 工具栏或工具窗口。  
  
### <a name="how-items-are-defined"></a>如何定义项目  
 .Vsct 文件以 XML 格式。 .Vsct 文件定义的 UI 元素的包，并确定这些元素出现在 IDE 中的位置。 每个菜单、 组或包中的命令 GUID 和 ID 中的第一次分配`Symbols`部分。 在剩下的.vsct 文件、 每个菜单、 命令和组都由其 GUID 和 ID 的组合标识。 下面的示例显示了典型`Symbols`部分由 Visual Studio 包模板生成时**菜单命令**在模板中选择。  
  
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
  
 顶级元素`Symbols`部分是[GuidSymbol 元素](../../extensibility/guidsymbol-element.md)。 `GuidSymbol`元素名映射到 IDE 用来标识包和其组件部分的 Guid。  
  
> [!NOTE]
>  Visual Studio 包模板自动生成的 Guid。 此外可以创建一个唯一的 GUID，通过单击**创建 GUID**上**工具**菜单。  
  
 第一个`GuidSymbol`元素中，"guid [PackageName] Pkg"，是包本身的 GUID。 这是 Visual Studio 用于加载包的 GUID。 通常情况下，它没有子元素。  
  
 按照约定，菜单和命令已归入到第二个`GuidSymbol`元素中，"guid [PackageName] CmdSet"，和位图是在第三个`GuidSymbol`元素中，"guidImages"。 不需要遵循此约定，但每个菜单、 组、 命令和位图必须的子级`GuidSymbol`元素。  
  
 在第二个`GuidSymbol`元素，它表示包的命令集，多个`IDSymbol`元素。 每个[IDSymbol 元素](../../extensibility/idsymbol-element.md)将名称映射为数字值，并且可能反映菜单、 组或命令的命令集的一部分。 `IDSymbol`中第三个元素`GuidSymbol`可能用作命令图标的元素表示位图。 因为必须是唯一的应用程序，任何两个子级的相同的 GUID/ID 对`GuidSymbol`元素可能具有相同的值。  
  
### <a name="menus-groups-and-commands"></a>菜单、 组和命令  
 当菜单、 组或命令具有 GUID 和 ID 时，它可以添加到 IDE 中。 每个 UI 元素必须具有以下操作︰  
  
-   一个`guid`属性的名称相匹配`GuidSymbol`下定义的用户界面元素的元素。  
  
-   `id`与关联的名称相匹配的属性`IDSymbol`元素。  
  
     在一起，`guid`和`id`属性撰写*签名*UI 元素。  
  
-   一个`priority`属性以重新确定其父菜单或组中的 UI 元素的位置。  
  
-   一个[父元素](../../extensibility/parent-element.md)具有`guid`和`id`属性，用于指定父菜单或组的签名。  
  
#### <a name="menus"></a>菜单  
 每个菜单定义为[Menu 元素](../../extensibility/menu-element.md)中`Menus`部分。 必须具有菜单`guid`， `id`，和`priority`属性，和一个`Parent`元素，还以下附加属性和子级︰  
  
-   一个`type`属性，指定菜单中是否应该出现在 IDE 中作为一种类型的菜单或工具栏。  
  
-   一个[字符串元素](../../extensibility/strings-element.md)，其中包含[ButtonText 元素](../../extensibility/buttontext-element.md)，它在 IDE 中，指定菜单上的标题和一个[CommandName 元素](../../extensibility/commandname-element.md)，用于指定中使用的名称**命令**窗口来访问菜单。  
  
-   可选标志。 一个[命令标志元素](../../extensibility/command-flag-element.md)可能会出现在菜单上定义，以更改其外观和行为在 IDE 中的。  
  
 每个`Menu`元素必须具有一个组作为其父项，除非它是一个可停靠工具栏等元素。 可停靠菜单是其自身的上级。 有关菜单和值的详细信息`type`属性，请参阅[Menu 元素](../../extensibility/menu-element.md)文档。  
  
 下面的示例演示在 Visual Studio 菜单栏上，旁边显示一个菜单**工具**菜单。  
  
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
 一组是指在中定义的项目`Groups`.vsct 文件的部分。 组是不仅仅是容器。 它们不作为菜单上一条分隔线显示在 IDE 中，除。 因此，[组元素](../../extensibility/group-element.md)仅由其签名、 优先级别和父定义。  
  
 一组只能有一个菜单、 另一个组，或本身作为父级。 但是，父级通常是将菜单或工具栏。 在前面的示例中的菜单是的子级`IDG_VS_MM_TOOLSADDINS`组中，并且该组是 Visual Studio 菜单栏上的子节点。 下面的示例中的组是菜单的在前面的示例中的子级。  
  
```  
 <Group guid="guidTopLevelMenuCmdSet" id="MyMenuGroup"  
priority="0x0600">  
   <Parent guid="guidTopLevelMenuCmdSet" id="TopLevelMenu"/>  
 </Group>  
```  
  
 因为它是菜单的一部分，此组将通常包含命令。 但是，它还可能包含其他菜单。 这是子菜单的定义方式，如下面的示例中所示。  
  
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
 提供给 IDE 的命令定义为[Button 元素](../../extensibility/button-element.md)或[组合元素](../../extensibility/combo-element.md)。 若要显示一个菜单或工具栏上，该命令必须作为其父项具有一个组。  
  
##### <a name="buttons"></a>按钮  
 在定义按钮`Buttons`部分。 任何菜单项、 按钮或其他用户单击它可执行单个命令的元素被视为一个按钮。 某些按钮类型还可以包括列表功能。 按钮都有相同所需和菜单所具有的可选属性，也可以有[Icon 元素](../../extensibility/icon-element.md)，用于指定 GUID 和位图表示在 IDE 中的按钮的 ID。 有关按钮和其属性的详细信息，请参阅[按钮元素](../../extensibility/buttons-element.md)文档。  
  
 下面的示例中的按钮是在较早的示例中，组的子组，并将在 IDE 中显示为该组的父菜单中的菜单项。  
  
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
 在中定义组合`Combos`部分。 每个`Combo`元素表示在 IDE 中的下拉列表框。 列表框中，也可能不是由用户，具体取决于值的可写`type`属性的组合。 组合具有相同的元素和按钮的行为，并且也可以有以下附加属性︰  
  
-   一个`defaultWidth`属性，指定像素宽度。  
  
-   `idCommandList`属性，指定包含在列表框中显示的项的列表。 必须在同一个声明命令列表`GuidSymbol`节点，其中包含组合框。  
  
 下面的示例定义一个组合元素。  
  
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
 将随的图标一起显示的命令必须包括`Icon`元素，它引用一个位图，通过使用其 GUID 和 id。 每个位图被定义为[位图元素](../../extensibility/bitmap-element.md)中`Bitmaps`部分。 唯一所需的属性`Bitmap`定义都包含`guid`和`href`，它指向的源代码文件。 如果源文件是一个资源条， **usedList**属性也是必需的若要列出的栏中可用的映像。 有关详细信息，请参阅[位图元素](../../extensibility/bitmap-element.md)文档。  
  
### <a name="parenting"></a>用作父级  
 以下规则控制项调用另一项作为其父项的方式。  
  
|元素|在此部分中的命令表定义|可能包含 (作为父级，或通过中放置`CommandPlacements`部分中，或两者)|可能包含 （也称为父）|  
|-------------|--------------------------------------------------|---------------------------------------------------------------------------------------------------|---------------------------------------------|  
|Group|[Groups 元素](../../extensibility/groups-element.md)，IDE、 其他 Vspackage|菜单上，一个组，则项本身|菜单、 组和命令|  
|菜单|[菜单元素](../../extensibility/menus-element.md)，IDE、 其他 Vspackage|1 到*n*组|0 到*n*组|  
|Toolbar|[菜单元素](../../extensibility/menus-element.md)，IDE、 其他 Vspackage|针对项本身|0 到*n*组|  
|菜单项|[按钮元素](../../extensibility/buttons-element.md)，IDE、 其他 Vspackage|1 到*n*组、 项目本身|-范围为&0; 到*n*组|  
|Button|[按钮元素](../../extensibility/buttons-element.md)，IDE、 其他 Vspackage|1 到*n*组、 项目本身||  
|Combo|[组合元素](../../extensibility/combos-element.md)，IDE、 其他 Vspackage|1 到*n*组、 项目本身||  
  
### <a name="menu-command-and-group-placement"></a>菜单、 命令和组放置  
 菜单、 组或命令可以出现在 IDE 中的多个位置中。 对于要在多个位置中显示项，必须将它添加到`CommandPlacements`部分作为[CommandPlacement 元素](../../extensibility/commandplacement-element.md)。 可以作为命令放置添加任何菜单、 组或命令。 但是，工具栏不能以这种方式放置因为它们不能出现在多个上下文相关的位置。  
  
 命令放置具有`guid`， `id`，和`priority`属性。 GUID 和 ID 必须与匹配的项的定位。 `priority`属性管理方面的其他项的项的位置。 当 IDE 合并两个或多个具有相同的优先级的项时，其位置是不确定的因为 IDE 不保证，软件包资源读取相同的顺序生成包每次。  
  
 如果菜单上或组出现在多个位置，该菜单或组的所有子级将都出现在每个实例。  
  
## <a name="command-visibility-and-context"></a>命令可见性和上下文  
 当安装多个 VSPackages 迁移时，大量的菜单、 菜单项和工具栏可能会使 IDE 显得杂乱。 若要避免此问题，可以控制各个用户界面元素的可见性使用*可见性限制*以及命令的标志。  
  
##### <a name="visibility-constraints"></a>可见性约束  
 可见性约束设置为[VisibilityItem 元素](../../extensibility/visibilityitem-element.md)中`VisibilityConstraints`部分。 可见性约束定义的目标项处于可见的特定 UI 上下文。 仅当已定义的上下文中的一个处于活动状态，菜单或包含在此部分中的命令才可见。 如果未在本部分中引用的菜单或命令，它始终是默认情况下可见。 本部分不会应用到组中。  
  
 `VisibilityItem`元素必须具有三个属性，如下所示︰`guid`和`id`目标 UI 元素，并`context`。 `context`属性指定当目标项将是可见的并接受任何有效的 UI 上下文作为其值。 Visual Studio UI 上下文常量是类的成员<xref:Microsoft.VisualStudio.VSConstants>类。</xref:Microsoft.VisualStudio.VSConstants> 每个`VisibilityItem`元素可以使用只有一个上下文值。 若要将应用第二个上下文，请创建第二个`VisibilityItem`指向同一个项，如下面的示例中所示的元素。  
  
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
 下面的命令标志可能会影响菜单和命令中它们应用于的可见性。  
  
 AlwaysCreate  
 即使它具有任何组或按钮创建菜单。  
  
 适用于︰`Menu`  
  
 CommandWellOnly  
 将应用此标志如果命令未显示在顶级菜单上，并且你想要使其可供其他外壳自定义设置，例如，将其绑定到的键。 安装 VSPackage 后，用户可以通过自定义这些命令打开**选项**对话框中，然后编辑下的命令放置**键盘环境**类别。 并不影响在快捷菜单、 工具栏、 菜单控制器或子菜单上的位置。  
  
 对于有效︰ `Button`，`Combo`  
  
 DefaultDisabled  
 默认情况下，如果未加载 VSPackage，实现的命令或尚未调用 QueryStatus 方法，将禁用该命令。  
  
 对于有效︰ `Button`，`Combo`  
  
 DefaultInvisible  
 默认情况下，该命令是不可见，如果未加载 VSPackage，实现的命令或尚未调用 QueryStatus 方法。  
  
 应结合`DynamicVisibility`标志。  
  
 Valid for: `Button`, `Combo`,`Menu`  
  
 DynamicVisibility  
 该命令的可见性可通过使用 QueryStatus 方法或上下文中包含的 GUID 更改`VisibilityConstraints`部分。  
  
 适用于显示在菜单中，不在工具栏上的命令。 可以禁用，但不是能隐藏 OLECMDF_INVISIBLE 标志从 QueryStatus 方法返回时顶层工具栏项。  
  
 在菜单上，此标志还指示，它时，应会自动隐藏其成员处于隐藏状态。 因为顶级菜单中已有此行为，此标志通常会分配给子菜单。  
  
 应结合`DefaultInvisible`标志。  
  
 Valid for: `Button`, `Combo`,`Menu`  
  
 NoShowOnMenuController  
 如果具有此标志的命令位于菜单控制器上，该命令不未出现在下拉列表中。  
  
 适用于︰`Button`  
  
 有关命令标志的详细信息，请参阅[命令标志元素](../../extensibility/command-flag-element.md)文档。  
  
##### <a name="general-requirements"></a>一般要求  
 您的命令必须通过以下一系列测试，然后它可以显示并启用︰  
  
-   正确定位该命令。  
  
-   `DefaultInvisible`未设置标志。  
  
-   父菜单或工具栏是可见的。  
  
-   该命令不是不可见中的上下文项由于[VisibilityConstraints 元素](../../extensibility/visibilityconstraints-element.md)部分。  
  
-   实现的 VSPackage 代码<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>接口显示，并使您的命令。</xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 没有接口代码截获此，并在其上执行相应操作。  
  
-   当用户单击您的命令时，它将成为受中概述的过程[路由算法](../../extensibility/internals/command-routing-algorithm.md)。  
  
## <a name="calling-pre-defined-commands"></a>调用预定义的命令  
 [UsedCommands 元素](../../extensibility/usedcommands-element.md)使 VSPackages 迁移到由其他 VSPackages 迁移或 IDE 提供了访问命令。 若要执行此操作，创建[UsedCommand 元素](../../extensibility/usedcommand-element.md)具有 GUID 和要使用的命令 ID。 这可确保 Visual Studio 中，将加载该命令是即使它不是当前的 Visual Studio 配置的一部分。 有关详细信息，请参阅[UsedCommand 元素](../../extensibility/usedcommand-element.md)。  
  
## <a name="interface-element-appearance"></a>界面元素外观  
 选择和定位命令元素的注意事项如下所示︰  
  
-   [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]提供以不同方式显示，具体取决于放置的许多 UI 元素。  
  
-   通过定义一个 UI 元素`DefaultInvisible`标志除非它是通过其 VSPackage 实现中显示不会在 IDE 中显示<xref:EnvDTE.IDTCommandTarget.QueryStatus%2A>方法，或与特定 UI 上下文中关联`VisibilityConstraints`部分。</xref:EnvDTE.IDTCommandTarget.QueryStatus%2A>  
  
-   即使成功定位的命令不会显示。 这是因为 IDE 自动隐藏或显示一些命令，具体取决于 VSPackage 具有 （或不具有） 的接口实现的。 例如，一些的 VSPackage 实现生成接口原因与生成相关的菜单项，以自动显示。  
  
-   应用`CommandWellOnly`的 UI 元素定义中的标志的含义，可以仅由自定义项添加该命令。  
  
-   仅当 IDE 位于设计视图中时显示一个对话框时，可能仅适用于某些 UI 上下文中，例如，命令。  
  
-   若要使某些用户界面元素在 IDE 中显示，必须实现一个或多个接口，或编写一些代码。  
  
## <a name="see-also"></a>另请参阅  
 [扩展的菜单和命令](../../extensibility/extending-menus-and-commands.md)
