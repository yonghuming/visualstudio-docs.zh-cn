---
title: "创作。Vsct 文件 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: VSCT files, manual authoring
ms.assetid: e9f715dc-12b7-439b-bdf3-f3dc75e62f1c
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bad1a8cbd8bc0369d405bf0a0c26c4285e143e46
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="authoring-vsct-files"></a>创作。Vsct 文件
本文档演示如何创作要将菜单项、 工具栏和其他用户界面 (UI) 元素添加到 Visual Studio 集成的开发环境 (IDE) 的.vsct 文件。 UI 元素添加到不具备.vsct 文件 Visual Studio 包 (VSPackage) 时，请使用以下步骤。  
  
 对于新项目，我们建议你使用 Visual Studio 包模板，因为它会生成一个.vsct 文件，具体取决于你的选择，已为菜单命令、 工具窗口或自定义编辑器所需的元素。 你可以修改此.vsct 文件以满足你的 VSPackage 的要求。 有关如何修改.vsct 文件的详细信息，请参阅中的示例[扩展菜单和命令](../../extensibility/extending-menus-and-commands.md)。  
  
## <a name="authoring-the-file"></a>创作文件  
 在这三个阶段中创作的.vsct 文件： 创建文件和资源的结构、 声明的 UI 元素、 将 UI 元素放在 IDE 中，和添加任何专用的行为。  
  
### <a name="file-structure"></a>文件结构  
 .Vsct 文件的基本结构是[CommandTable](../../extensibility/commandtable-element.md)包含的根元素[命令](../../extensibility/commands-element.md)元素和[符号](../../extensibility/symbols-element.md)元素。  
  
##### <a name="to-create-the-file-structure"></a>若要创建的文件结构  
  
1.  将.vsct 文件添加到你的项目中，按照中的步骤[如何： 创建。Vsct 文件](../../extensibility/internals/how-to-create-a-dot-vsct-file.md)。  
  
2.  添加到所需命名空间`CommandTable`元素，如下面的示例中所示。  
  
    ```xml  
    <CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable"   
        xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  
    ```  
  
3.  在`CommandTable`元素中，添加`Commands`要托管你的自定义菜单、 工具栏、 命令组和命令的所有元素。 以便可以加载自定义的 UI 元素，`Commands`元素必须具有其`Package`属性设置为包的名称。  
  
     后`Commands`元素中，添加`Symbols`元素定义的包，并名称 Guid 和命令 Id 的 UI 元素。  
  
### <a name="including-visual-studio-resources"></a>包括 Visual Studio 资源，  
 使用[Extern](../../extensibility/extern-element.md)元素访问定义 Visual Studio 命令和所需将你的 UI 元素放在 IDE 中的菜单的文件。 如果你将使用你的包的外部定义的命令，使用[UsedCommands](../../extensibility/usedcommands-element.md)元素以通知 Visual Studio。  
  
##### <a name="to-include-visual-studio-resources"></a>包含 Visual Studio 的资源  
  
1.  在顶部`CommandTable`元素中，添加一个`Extern`元素的引用，并且设置的每个外部文件`href`属性设为文件的名称。 你可以引用以下的标头文件，以访问 Visual Studio 资源：  
  
    -   Stdidcmd.h，定义由 Visual Studio 公开的所有命令的 Id。  
  
    -   Vsshlids.h，包含 Visual Studio 菜单的命令 Id。  
  
2.  如果您的包调用由 Visual Studio 或其他包定义的任何命令，将添加`UsedCommands`元素的后面`Commands`元素。 填充此元素[UsedCommand](../../extensibility/usedcommand-element.md) ，它是不是你的包的一部分调用每个命令的元素。 设置`guid`和`id`属性`UsedCommand`要调用的命令的 GUID 和 ID 值的元素。 有关如何查找的 Guid 和 Id 的 Visual Studio 命令的详细信息，请参阅[Guid 和 Id 的 Visual Studio 命令](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)。 若要从其他包调用命令，请使用的 GUID 和命令在这些包的.vsct 文件中定义的 ID。  
  
### <a name="declaring-ui-elements"></a>声明 UI 元素  
 声明中的所有新 UI 元素`Symbols`.vsct 文件的部分。  
  
##### <a name="to-declare-ui-elements"></a>若要声明 UI 元素  
  
1.  在`Symbols`元素中，添加三个[GuidSymbol](../../extensibility/guidsymbol-element.md)元素。 每个`GuidSymbol`元素具有`name`属性和`value`属性。 设置`name`特性，使其能够反映元素的用途。 `value`特性接受一个 GUID。 (若要在生成 GUID，**工具**菜单上，单击**创建 GUID**，然后选择**注册表格式**。)  
  
     第一个`GuidSymbol`元素表示你的包，并通常没有任何子级。 第二个`GuidSymbol`元素表示该命令设置，并将包含的所有符号定义菜单、 组和命令。 第三个`GuidSymbol`元素表示图像存储区和包含的所有命令的图标的符号。 如果你不有使用图标任何命令，则可以省略第三个`GuidSymbol`元素。  
  
2.  在`GuidSymbol`表示你的命令集的元素添加一个或多个[IDSymbol](../../extensibility/idsymbol-element.md)元素。 其中每个表示菜单、 工具栏、 组中或要添加到 UI 的命令。  
  
     每个`IDSymbol`元素，设置`name`属性的名称将用于指对应的菜单、 组或命令，并将`value`为十六进制数，它将代表其命令 id 的元素。没有两`IDSymbol`具有相同父元素可以具有相同的值。  
  
3.  如果任何 UI 元素需要图标，添加`IDSymbol`到每个图标的元素`GuidSymbol`表示映像存储区的元素。  
  
### <a name="putting-ui-elements-in-the-ide"></a>在 IDE 中将 UI 元素  
 [菜单](../../extensibility/menus-element.md)元素，[组](../../extensibility/groups-element.md)元素，并[按钮](../../extensibility/buttons-element.md)元素包含的所有菜单、 组和包中定义的命令定义。 通过使用 IDE 中放置这些菜单、 组和命令[父](../../extensibility/parent-element.md)元素，它是一部分的 UI 元素定义，或使用[CommandPlacement](../../extensibility/commandplacement-element.md)其他位置定义的元素。  
  
 每个`Menu`， `Group`，和`Button`元素具有`guid`属性和`id`属性。 始终设置`guid`特性以匹配的名称特性`GuidSymbol`元素，它表示你的命令设置，并设置`id`属性的名称为`IDSymbol`表示菜单、 组或中的命令的元素`Symbols`部分。  
  
##### <a name="to-define-ui-elements"></a>定义用户界面元素  
  
1.  如果你正在定义任何新的菜单、 子菜单、 快捷菜单或工具栏，添加`Menus`元素`Commands`元素。 然后，对于要创建每个菜单上，添加[菜单](../../extensibility/menu-element.md)元素`Menus`元素。  
  
     设置`guid`和`id`属性`Menu`元素，，然后将设置`type`属性设为所需的菜单的种类。 您还可以设置`priority`特性来确定父组中的菜单的相对位置。  
  
    > [!NOTE]
    >  `priority`属性不适用于工具栏和上下文菜单。  
  
2.  必须由命令组菜单和工具栏的直接子级承载 Visual Studio IDE 中的所有命令。 如果你要向 IDE 添加新菜单或工具栏，它们必须包含新的命令组。 此外可能会将命令组添加到现有菜单和工具栏，以便你的命令可以直观地进行分组。  
  
     在添加新命令组时，必须首先创建`Groups`元素，然后将添加到它[组](../../extensibility/group-element.md)为每个命令组的元素。  
  
     设置`guid`和`id`每个属性`Group`元素，，然后将设置`priority`特性来确定父菜单上的组的相对位置。 有关详细信息，请参阅[按钮创建可重用组](../../extensibility/creating-reusable-groups-of-buttons.md)。  
  
3.  如果你要向 IDE 添加新的命令，将添加`Buttons`元素`Commands`元素。 然后，对于每个命令中，添加[按钮](../../extensibility/button-element.md)元素`Buttons`元素。  
  
    1.  设置`guid`和`id`每个属性`Button`元素，，然后将设置`type`属性设为所需的按钮的种类。 您还可以设置`priority`特性来确定父组中的命令的相对位置。  
  
        > [!NOTE]
        >  使用`type="button"`标准菜单命令和工具栏上的按钮。  
  
    2.  在`Button`元素中，添加[字符串](../../extensibility/strings-element.md)包含的元素[ButtonText](../../extensibility/buttontext-element.md)元素和[CommandName](../../extensibility/commandname-element.md)元素。 `ButtonText`元素为一个菜单项或工具栏按钮的工具提示中提供的文本标签。 `CommandName`元素提供很好地在命令中使用的命令的名称。  
  
    3.  如果你的命令将有一个图标，创建[图标](../../extensibility/icon-element.md)中的元素`Button`元素，并设置其`guid`和`id`特性以`Bitmap`图标的元素。  
  
        > [!NOTE]
        >  工具栏按钮必须具有的图标。  
  
     有关详细信息，请参阅[MenuCommands 与。OleMenuCommands](../../extensibility/menucommands-vs-olemenucommands.md)。  
  
4.  如果你的命令的任何需要的图标，添加[位图](../../extensibility/bitmaps-element.md)元素`Commands`元素。 然后，对于每个图标，添加[位图](../../extensibility/bitmap-element.md)元素`Bitmaps`元素。 这是你在其中指定位图资源的位置。 有关详细信息，请参阅[将图标添加到菜单命令](../../extensibility/adding-icons-to-menu-commands.md)。  
  
 你可以依赖于设置父级结构正确放置大多数菜单、 组和命令。 对于非常大的命令集，或当菜单、 组或命令必须出现在多个位置中，我们建议您指定命令放置。  
  
##### <a name="to-rely-on-parenting-to-place-ui-elements-in-the-ide"></a>依赖于设置父级来放置在 IDE 中的 UI 元素  
  
1.  对于典型设置父级，创建`Parent`中每个元素`Menu`， `Group`，和`Command`在你的包中定义的元素。  
  
     目标`Parent`元素是菜单或将包含菜单上的组、 组或命令。  
  
    1.  设置`guid`属性的名称为`GuidSymbol`定义该命令集的元素。 如果目标元素不是你的包的一部分，为该命令集，使用的 guid 在相应的.vsct 文件中定义。  
  
    2.  设置`id`特性以匹配特性`id`目标菜单或组的属性。 有关菜单和公开的 Visual Studio 的组的列表，请参阅[Guid 和 Id 的 Visual Studio 菜单](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)或[Guid 和 Id 的 Visual Studio 工具栏](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)。  
  
 如果你有大量的 UI 元素将在 IDE 中，或者是否可以应出现在多个位置处的元素，定义其放置在[CommandPlacements](../../extensibility/commandplacements-element.md)元素，如以下步骤中所示。  
  
##### <a name="to-use-command-placement-to-place-ui-elements-in-the-ide"></a>若要使用命令放置来放置在 IDE 中的 UI 元素  
  
1.  后`Commands`元素中，添加`CommandPlacements`元素。  
  
2.  在`CommandPlacements`元素中，添加`CommandPlacement`为每个菜单、 组或命令放置的元素。  
  
     每个`CommandPlacement`元素或`Parent`元素在一个 IDE 位置放置一个菜单、 组或命令。 UI 元素只能有一个父级，但它可以有多个命令放置。 若要在多个位置放置 UI 元素，添加`CommandPlacement`的每个位置的元素。  
  
3.  设置`guid`和`id`每个属性`CommandPlacement`元素托管的菜单或组，就像你将为`Parent`元素。 你还可以设置`priority`特性来确定的用户界面元素的相对位置。  
  
 可以混合使用通过设置父级的放置和命令放置。 但是，对于非常大的命令集，我们建议你使用仅命令放置。  
  
### <a name="adding-specialized-behaviors"></a>添加专用的行为  
 你可以使用[CommandFlag](../../extensibility/command-flag-element.md)元素若要修改的行为的菜单和命令，例如，若要更改其外观和可见性。 你也会影响命令时可见，通过使用[VisibilityConstraints](../../extensibility/visibilityconstraints-element.md)，或通过使用添加键盘快捷方式[键绑定](../../extensibility/keybindings-element.md)。 某些种类的菜单和命令已具有专用的内置的行为。  
  
##### <a name="to-add-specialized-behaviors"></a>若要添加专用的行为  
  
1.  若要在加载解决方案时，使 UI 元素仅在某些 UI 上下文中，例如中, 可见，请使用可见性约束。  
  
    1.  后`Commands`元素中，添加`VisibilityConstraints`元素。  
  
    2.  若要将限制每个 UI 项目，将添加[VisibilityItem](../../extensibility/visibilityitem-element.md)元素。  
  
    3.  每个`VisibilityItem`元素，设置`guid`和`id`属性菜单、 组中，或命令，以及然后将其设置到`context`属性设为所需的 UI 上下文中定义<xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80>类。 有关详细信息，请参阅[VisibilityItem 元素](../../extensibility/visibilityitem-element.md)。  
  
2.  若要在代码中设置的可见性和可用性 UI 项，使用一个或多个以下的命令标志：  
  
    -   DefaultDisabled  
  
    -   DefaultInvisible  
  
    -   DynamicItemStart  
  
    -   DynamicVisibility  
  
    -   NoShowOnMenuController  
  
    -   NotInTBList  
  
     有关详细信息，请参阅[命令标志元素](../../extensibility/command-flag-element.md)。  
  
3.  若要更改元素显示，或动态更改其外观的方式，使用一个或多个以下的命令标志：  
  
    -   AlwaysCreate  
  
    -   CommandWellOnly  
  
    -   DefaultDocked  
  
    -   DontCache  
  
    -   DynamicItemStart  
  
    -   FixMenuController  
  
    -   IconAndText  
  
    -   图像  
  
    -   StretchHorizontally  
  
    -   TextMenuUseButton  
  
    -   TextChanges  
  
    -   TextOnly  
  
     有关详细信息，请参阅[命令标志元素](../../extensibility/command-flag-element.md)。  
  
4.  若要更改在收到命令时，元素的反应方式，使用一个或多个以下的命令标志：  
  
    -   AllowParams  
  
    -   CaseSensitive  
  
    -   CommandWellOnly  
  
    -   筛选键  
  
    -   NoAutoComplete  
  
    -   NoButtonCustomize  
  
    -   NoKeyCustomize  
  
    -   NoToolbarClose  
  
    -   PostExec  
  
    -   RouteToDocs  
  
    -   TextIsAnchorCommand  
  
     有关详细信息，请参阅[命令标志元素](../../extensibility/command-flag-element.md)。  
  
5.  若要附加到菜单或菜单上的项的依赖于菜单的键盘快捷方式，将添加一个 & 号字符 (&) 在`ButtonText`的菜单或菜单项元素。 打开父菜单时，后面 & 符的字符是活动的键盘快捷方式。  
  
6.  若要将独立于菜单的键盘快捷方式附加到命令中，使用[键绑定](../../extensibility/keybindings-element.md)。 有关详细信息，请参阅[键绑定元素](../../extensibility/keybinding-element.md)。  
  
7.  若要将本地化菜单文本，请使用`LocCanonicalName`元素。 有关详细信息，请参阅[字符串元素](../../extensibility/strings-element.md)。  
  
 某些菜单和按钮的类型包括专用的行为。 下表介绍一些专用的菜单和按钮类型。 对于其他类型，请参阅`types`属性中的描述[Menu 元素](../../extensibility/menu-element.md)， [Button 元素](../../extensibility/button-element.md)，和[组合元素](../../extensibility/combo-element.md)。  
  
 组合框  
 组合框进行了可以使用工具栏的下拉列表。 若要将组合框添加到 UI 中，创建[组合](../../extensibility/combos-element.md)中的元素`Commands`元素。 然后将添加到`Combos`元素`Combo`的每个组合框，以添加元素。 `Combo`元素具有相同的特性和子级作为`Button`元素，并且还具有`DefaultWidth`和`idCommandList`属性。 `DefaultWidth`属性以像素为单位设置宽度和`idCommandList`属性指向用于填充组合框命令 ID。 有关详细信息，请参阅`Combo`元素文档。  
  
 MenuController  
 菜单控制器是具有它旁边的箭头按钮。 单击的箭头可打开列表。 若要将菜单控制器添加到 UI 中，创建`Menu`元素，并设置其`type`属性设为**MenuController**或**MenuControllerLatched**，取决于你想要的行为。 若要填充菜单控制器，请将其设置为的父级`Group`元素。 菜单控制器将显示其下拉列表上的该组的所有子级。  
  
## <a name="see-also"></a>另请参阅  
 [扩展菜单和命令](../../extensibility/extending-menus-and-commands.md)   
 [Visual Studio 命令表 (。Vsct) 文件](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [VSCT XML 架构参考](../../extensibility/vsct-xml-schema-reference.md)