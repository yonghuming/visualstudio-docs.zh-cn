---
title: "创作。Vsct 文件 | Microsoft Docs"
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
  - "VSCT 文件，手动创作"
ms.assetid: e9f715dc-12b7-439b-bdf3-f3dc75e62f1c
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# 创作。Vsct 文件
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

本文档演示如何编写.vsct 文件添加到 Visual Studio 集成的开发环境 \(IDE\) 的菜单项、 工具栏和其他用户界面 \(UI\) 元素。 当将 UI 元素添加到不具备.vsct 文件 Visual Studio Package \(VSPackage\)，请使用以下步骤。  
  
 对于新项目，我们建议你使用 Visual Studio Package 模板，因为它会生成一个.vsct 文件，具体取决于您的选择，已为菜单命令、 工具窗口或自定义编辑器所需的元素。 您可以修改此.vsct 文件以满足你的 VSPackage 的要求。 有关如何修改.vsct 文件的详细信息，请参阅中的示例 [扩展的菜单和命令](../../extensibility/extending-menus-and-commands.md)。  
  
## 编写文件  
 在这三个阶段中编写.vsct 文件: 创建文件和资源的结构、 声明的用户界面元素、 将 UI 元素放在 IDE 中，和添加任何特殊的行为。  
  
### 文件结构  
 .Vsct 文件的基本结构 [CommandTable](../../extensibility/commandtable-element.md) 根元素，其中包含 [命令](../../extensibility/commands-element.md) 元素和一个 [符号](../../extensibility/symbols-element.md) 元素。  
  
##### 若要创建的文件结构  
  
1.  按照中的步骤将.vsct 文件添加到您的项目 [如何: 创建。Vsct 文件](../../extensibility/internals/how-to-create-a-dot-vsct-file.md)。  
  
2.  添加到所需命名空间 `CommandTable` 元素，如下面的示例中所示。  
  
    ```xml  
    <CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable"   
    	xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  
    ```  
  
3.  在 `CommandTable` 元素中，添加 `Commands` 要承载您的自定义菜单、 工具栏、 命令组和命令的所有元素。 以便可以加载自定义用户界面元素， `Commands` 元素必须具有其 `Package` 属性设置为包的名称。  
  
     之后 `Commands` 元素中，添加 `Symbols` 元素来定义的包，以及名称的 Guid 和命令 Id 的 UI 元素。  
  
### 包括 Visual Studio 资源  
 使用 [Extern](../../extensibility/extern-element.md) 元素访问定义 Visual Studio 命令和菜单将用户界面元素放在 IDE 中所需的文件。 如果您将使用您的包的外部定义的命令，使用 [UsedCommands](../../extensibility/usedcommands-element.md) 元素以通知 Visual Studio。  
  
##### 若要包括 Visual Studio 资源  
  
1.  在顶部 `CommandTable` 元素中，添加一个 `Extern` 元素为每个外部文件引用，并设置 `href` 属性设为文件的名称。 你可以引用以下的标头文件，若要访问 Visual Studio 资源:  
  
    -   Stdidcmd.h，公开由 Visual Studio 的所有命令的定义 Id。  
  
    -   Vsshlids.h，包含用于 Visual Studio 菜单的命令 Id。  
  
2.  如果您的包调用由 Visual Studio 或其他包定义的任何命令，将添加 `UsedCommands` 元素的后面 `Commands` 元素。 填充此元素与 [UsedCommand](../../extensibility/usedcommand-element.md) 调用是不是您的包的一部分的每个命令的元素。 设置 `guid` 和 `id` 属性 `UsedCommand` 元素与要调用的命令的 GUID 和 ID 值。 有关如何查找 Guid 和 Id 的 Visual Studio 命令的详细信息，请参阅 [Guid 和 Id 的 Visual Studio 命令](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)。 若要从其他包调用命令，请使用 GUID 和命令，这些包.vsct 文件中定义的 ID。  
  
### 声明用户界面元素  
 声明中的所有新用户界面元素 `Symbols` .vsct 文件的部分。  
  
##### 若要声明 UI 元素  
  
1.  在 `Symbols` 元素中，添加三个 [GuidSymbol](../../extensibility/guidsymbol-element.md) 元素。 每个 `GuidSymbol` 元素具有 `name` 属性和一个 `value` 属性。 设置 `name` 属性，以便其能够反映元素的用途。`value` 特性将一个 GUID。 \(若要在生成的 GUID， **工具** 菜单上，单击 **创建 GUID**, ，然后选择 **注册表格式**。\)  
  
     第一个 `GuidSymbol` 元素表示您的软件包，并通常没有任何子级。 第二个 `GuidSymbol` 元素不表示该命令设置，并将包含所有的符号的定义菜单、 组和命令。 第三个 `GuidSymbol` 元素表示图像存储区，并包含用于所有命令的图标的符号。 如果您有没有使用图标的命令，则可以省略第三个 `GuidSymbol` 元素。  
  
2.  在 `GuidSymbol` 元素，它表示你的命令集，添加一个或多个 [IDSymbol](../../extensibility/idsymbol-element.md) 元素。 其中每个表示菜单、 工具栏、 组或你添加到 UI 的命令。  
  
     每个 `IDSymbol` 元素中，设置 `name` 属性的名称将用于指对应的菜单、 组或命令，并将 `value` 为十六进制数表示其命令 id 的元素。 没有两 `IDSymbol` 具有相同的父元素可以具有相同的值。  
  
3.  如果需要图标的任何用户界面元素，将添加 `IDSymbol` 到每个图标的元素 `GuidSymbol` 表示映像存储元素。  
  
### 在 IDE 中将 UI 元素  
 [菜单](../../extensibility/menus-element.md) 元素， [组](../../extensibility/groups-element.md) 元素，并 [按钮](../../extensibility/buttons-element.md) 元素包含的定义的所有菜单、 组和您的包中定义的命令。 将这些菜单、 组和命令放在可通过使用 IDE 中 [父](../../extensibility/parent-element.md) 元素，它是在 UI 元素定义，或是由使用 [CommandPlacement](../../extensibility/commandplacement-element.md) 元素是在其他位置定义。  
  
 每个 `Menu`, ，`Group`, ，和 `Button` 元素具有 `guid` 属性和一个 `id` 属性。 始终设置 `guid` 要匹配的名称特性 `GuidSymbol` 元素，它表示您的命令设置，并设置 `id` 属性的名称为 `IDSymbol` 元素，它表示菜单、 组或在命令 `Symbols` 部分。  
  
##### 若要定义 UI 元素  
  
1.  如果您正在定义任何新的菜单、 子菜单、 快捷菜单或工具栏，将添加 `Menus` 元素 `Commands` 元素。 然后，对于要创建每个菜单上，添加 [菜单](../../extensibility/menu-element.md) 元素 `Menus` 元素。  
  
     设置 `guid` 和 `id` 属性 `Menu` 元素，然后将设置 `type` 属性设为所需的菜单的种类。 您还可以设置 `priority` 特性来确定父组中的菜单中的相对位置。  
  
    > [!NOTE]
    >  `priority` 属性不适用于工具栏和上下文菜单。  
  
2.  Visual Studio IDE 中的所有命令都必须直接子项的菜单和工具栏的命令组由都承载。 如果要向 IDE 添加新菜单或工具栏，其中必须包含命令中的新组。 您还可以向现有菜单和工具栏添加命令组，以便您命令可以直观地进行分组。  
  
     当添加新的命令组时，必须首先创建 `Groups` 元素，然后向其中添加和 [组](../../extensibility/group-element.md) 为每个命令组的元素。  
  
     设置 `guid` 和 `id` 的每个属性 `Group` 元素，然后将设置 `priority` 特性来确定父菜单上的组的相对位置。 有关详细信息，请参阅[创建可重用的按钮的组](../../extensibility/creating-reusable-groups-of-buttons.md)。  
  
3.  如果您要向 IDE 添加新的命令，将添加 `Buttons` 元素 `Commands` 元素。 然后，对于每个命令添加 [按钮](../../extensibility/button-element.md) 元素 `Buttons` 元素。  
  
    1.  设置 `guid` 和 `id` 的每个属性 `Button` 元素，然后将设置 `type` 属性设为所需的按钮类型。 您还可以设置 `priority` 特性来确定父组中的命令的相对位置。  
  
        > [!NOTE]
        >  使用 `type="button"` 标准菜单命令和工具栏上的按钮。  
  
    2.  在 `Button` 元素中，添加 [字符串](../../extensibility/strings-element.md) 元素，其中包含 [ButtonText](../../extensibility/buttontext-element.md) 元素和一个 [CommandName](../../extensibility/commandname-element.md) 元素。`ButtonText` 元素提供的菜单项或工具栏按钮的工具提示的文本标签。`CommandName` 元素提供了要在命令中也使用的命令的名称。  
  
    3.  如果您的命令将具有一个图标，创建 [图标](../../extensibility/icon-element.md) 中的元素 `Button` 元素，并设置其 `guid` 和 `id` 属性到 `Bitmap` 图标的元素。  
  
        > [!NOTE]
        >  工具栏按钮必须具有图标。  
  
     有关详细信息，请参阅[MenuCommands 与 OleMenuCommands](../../misc/menucommands-vs-olemenucommands.md)。  
  
4.  如果您的命令的任何需要的图标，将添加 [位图](../../extensibility/bitmaps-element.md) 元素 `Commands` 元素。 然后，对于每个图标，添加 [位图](../../extensibility/bitmap-element.md) 元素 `Bitmaps` 元素。 这是在其中指定位图资源的位置。 有关更多信息，请参见[将图标添加到菜单命令](../../extensibility/adding-icons-to-menu-commands.md)。  
  
 您可以依赖父级关系结构，从而可以正确放置大多数菜单、 组和命令。 对于非常大的命令集，或当菜单、 组或命令必须出现在多个位置中，我们建议您指定命令放置。  
  
##### 若要依赖于放置在 IDE 中的用户界面元素的子级  
  
1.  对于典型的子级创建 `Parent` 中每个元素 `Menu`, ，`Group`, ，和 `Command` 在您的包中定义的元素。  
  
     目标的 `Parent` 元素是菜单或将包含菜单上的组、 组或命令。  
  
    1.  设置 `guid` 属性的名称为 `GuidSymbol` 元素，用于定义该命令集。 如果目标元素不是您的软件包的一部分，该命令集，使用的 guid 相应.vsct 文件中定义。  
  
    2.  设置 `id` 属性以匹配 `id` 目标菜单或组的属性。 有关菜单和由 Visual Studio 的组的列表，请参阅 [Guid 和 Id 的 Visual Studio 菜单](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md) 或 [Guid 和 Id 的 Visual Studio 工具栏](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)。  
  
 如果您有大量的用户界面元素放置在 IDE 中，或者您有应出现在多个位置的元素，定义其放置在 [CommandPlacements](../../extensibility/commandplacements-element.md) 元素，如下面的步骤中所示。  
  
##### 若要使用命令放置在 IDE 中放置 UI 元素  
  
1.  之后 `Commands` 元素中，添加 `CommandPlacements` 元素。  
  
2.  在 `CommandPlacements` 元素中，添加 `CommandPlacement` 的每个菜单、 组或命令可将放元素。  
  
     每个 `CommandPlacement` 元素或 `Parent` 元素放在一个 IDE 位置放置一个菜单、 组或命令。 UI 元素只能有一个父级，但它可以有多个命令安排。 若要在多个位置放置 UI 元素，添加 `CommandPlacement` 为每个位置的元素。  
  
3.  设置 `guid` 和 `id` 的每个属性 `CommandPlacement` 元素到宿主的菜单或组，就像您那样 `Parent` 元素。 您还可以设置 `priority` 特性来确定的用户界面元素的相对位置。  
  
 您可以混合使用位置的子级和命令位置。 但是，对于非常大的命令集，我们建议使用仅命令放置。  
  
### 添加专用的行为  
 您可以使用 [CommandFlag](../../extensibility/command-flag-element.md) 元素若要修改的行为的菜单和命令，例如，若要更改其外观和可见性。 您也可能会影响当命令是可见的通过使用 [VisibilityConstraints](../../extensibility/visibilityconstraints-element.md), ，或通过使用添加键盘快捷方式 [键绑定](../../extensibility/keybindings-element.md)。 某些种类的菜单和命令已经拥有的专用中内置的行为。  
  
##### 若要添加专用的行为  
  
1.  若要在加载解决方案时仅在某些 UI 上下文中，例如，显示用户界面元素，使用可见性限制。  
  
    1.  之后 `Commands` 元素中，添加 `VisibilityConstraints` 元素。  
  
    2.  若要将限制每个 UI 项目，将添加 [VisibilityItem](../../extensibility/visibilityitem-element.md) 元素。  
  
    3.  每个 `VisibilityItem` 元素中，设置 `guid` 和 `id` 与菜单、 组中，或命令，然后将其设置的属性 `context` 属性为所需的 UI 上下文中定义 <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> 类。 有关详细信息，请参阅[VisibilityItem 元素](../../extensibility/visibilityitem-element.md)。  
  
2.  若要在代码中设置的可见性和用户界面项的可用性，使用一个或多个以下的命令标志:  
  
    -   DefaultDisabled  
  
    -   DefaultInvisible  
  
    -   DynamicItemStart  
  
    -   DynamicVisibility  
  
    -   NoShowOnMenuController  
  
    -   NotInTBList  
  
     有关详细信息，请参阅[命令标志元素](../../extensibility/command-flag-element.md)。  
  
3.  若要更改元素方式显示，或者动态地更改其外观，使用一个或多个以下的命令标志:  
  
    -   AlwaysCreate  
  
    -   CommandWellOnly  
  
    -   DefaultDocked  
  
    -   DontCache  
  
    -   DynamicItemStart  
  
    -   FixMenuController  
  
    -   IconAndText  
  
    -   Pict  
  
    -   StretchHorizontally  
  
    -   TextMenuUseButton  
  
    -   TextChanges  
  
    -   TextOnly  
  
     有关详细信息，请参阅[命令标志元素](../../extensibility/command-flag-element.md)。  
  
4.  若要更改某个元素在收到命令时的反应，使用一个或多个以下的命令标志:  
  
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
  
5.  若要将依赖于菜单的键盘快捷方式附加到菜单或菜单中的项，将添加一个与符号字符 \(&\) 在 `ButtonText` 菜单或菜单项的元素。 在父菜单处于打开状态时，后面 & 符的字符是活动的键盘快捷方式。  
  
6.  若要将独立于菜单的键盘快捷方式附加到某个命令，使用 [键绑定](../../extensibility/keybindings-element.md)。 有关详细信息，请参阅[键绑定元素](../../extensibility/keybinding-element.md)。  
  
7.  若要本地化的菜单文本，请使用 `LocCanonicalName` 元素。 有关详细信息，请参阅[字符串元素](../../extensibility/strings-element.md)。  
  
 某些菜单和按钮的类型包括特殊的行为。 下表描述某些专用的菜单和按钮类型。 对于其他类型，请参阅 `types` 属性中的说明 [Menu 元素](../../extensibility/menu-element.md), ，[Button 元素](../../extensibility/button-element.md), ，和 [组合元素](../../extensibility/combo-element.md)。  
  
 组合框  
 组合框进行了可以使用工具栏的下拉列表。 若要将组合框添加到用户界面中，创建 [组合](../../extensibility/combos-element.md) 中的元素 `Commands` 元素。 然后将添加到 `Combos` 元素 `Combo` 对于每个组合框，若要添加的元素。`Combo` 元素具有相同的特性和作为子级 `Button` 元素并且还要 `DefaultWidth` 和 `idCommandList` 属性。`DefaultWidth` 属性设置的宽度以像素为单位，与 `idCommandList` 属性指向用于填充组合框中的命令 ID。 有关详细信息，请参阅 `Combo` 元素文档。  
  
 MenuController  
 菜单控制器是具有其旁边的箭头的按钮。 单击箭头打开列表。 若要将菜单控制器添加到用户界面中，创建 `Menu` 元素，并设置其 `type` 属性设为 **MenuController** 或 **MenuControllerLatched**, ，取决于所需的行为。 若要填充菜单控制器，请将其设置为的父级 `Group` 元素。 菜单控制器将在其下拉列表显示该组的所有子级。  
  
## 请参阅  
 [扩展的菜单和命令](../../extensibility/extending-menus-and-commands.md)   
 [Visual Studio 命令表 \(。Vsct\) 文件](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [VSCT XML 架构参考](../../extensibility/vsct-xml-schema-reference.md)