---
title: "如何：创建菜单、子菜单和快捷菜单 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "命令栏, 体系结构"
  - "菜单, 创建"
  - "菜单, 体系结构"
  - "命令, 菜单"
  - "菜单"
ms.assetid: 62004fd9-7f99-4f00-8d01-1dde53e23dbb
caps.latest.revision: 46
caps.handback.revision: 46
manager: "douge"
---
# 如何：创建菜单、子菜单和快捷菜单
若要将菜单添加到 Visual Studio 集成开发环境 \(IDE\)，VSPackage 必须将 [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] 体系结构用于命令组菜单。 命令组菜单允许组件和 IDE 共享命令。 有关命令组菜单的详细信息，请参阅 [Vspackage 如何添加用户界面元素](../extensibility/internals/how-vspackages-add-user-interface-elements.md)。  
  
 在 Vspackage 中，在 .vsct 文件的 [Menus](../extensibility/menus-element.md) 部分定义菜单。 .vsct 文件定义菜单、工具栏、组和命令。 用户单击命令即可执行功能。 组是命令的容器。 菜单是组的容器。 若要创建基本菜单，必须创建一个菜单、一个命令组和至少一个命令。  
  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中可以以三种基本方式显示菜单：  
  
-   显示为主菜单栏上的菜单。  
  
-   显示为另一个菜单的子菜单。  
  
-   显示为快捷菜单（通常通过右键单击显示）。  
  
 本主题演示如何创建每种菜单。 下面的演练也将演示如何执行此操作：  
  
-   [添加到 Visual Studio 菜单栏的菜单](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)  
  
-   [将子菜单添加到菜单](../extensibility/adding-a-submenu-to-a-menu.md)  
  
-   [在工具窗口中添加快捷菜单](../extensibility/adding-a-shortcut-menu-in-a-tool-window.md)  
  
### 创建菜单、子菜单或快捷菜单  
  
1.  在你的项目中，双击 .vsct 文件以在编辑器中打开它。  
  
     如果你的项目中没有 .vsct 文件，请添加。 如果使用 Visual Studio 包模板创建包，请选择“菜单命令”；执行此操作将生成一个 .vsct 文件。  
  
2.  在 `Symbols` 部分中，找到包含组和命令的 [GuidSymbol](../extensibility/guidsymbol-element.md) 元素。  
  
3.  为你想要添加的每个菜单、组或命名创建 [IDSymbol](../extensibility/idsymbol-element.md) 元素，如下面的示例所示。  
  
     [!CODE [ButtonGroup#01](../CodeSnippet/VS_Snippets_VSSDK/buttongroup#01)]  
  
     `GuidSymbol` 和 `IDSymbol` 元素的 `name` 特性为每个新建的菜单、组或命令提供 GUID:ID 对。`GUID` 表示为你的 VSPackage 定义的命令集。 你可以定义多个命令集。 每个 GUID:ID 对必须是唯一的。  
  
4.  在 `Menus` 部分中定义新菜单，如下所示：  
  
    1.  将 `guid` 和 `id` 字段设置为与新菜单的 GUID:ID 相匹配。  
  
    2.  设置 `priority` 特性。  
  
         .vsct 文件使用 `priority` 特性来确定菜单在父组中的其他对象间的位置。  
  
         具有较低优先级值的菜单显示在具有较高优先级值的菜单之前。 允许使用重复的优先级值，但具有同等优先级的菜单的相对位置由运行时处理 Vspackage 的顺序来确定，并且无法预先确定该顺序。 省略 `priority` 特性会将其值设置为 0。  
  
         请勿为快捷菜单设置优先级，因为其位置是由对其进行调用的代码设置的。  
  
    3.  对于菜单和子菜单中，将 `type` 特性设置为描述典型菜单的 `Menu`。 对于快捷菜单，将 `type` 特性设置为 `Context`。  
  
         有关其他有效菜单类型（如工具栏和菜单控制器）的说明，请参阅[Menu 元素](../extensibility/menu-element.md)。  
  
    4.  在菜单定义中，创建一个包含 [ButtonText](../extensibility/buttontext-element.md) 元素的 [Strings](../extensibility/strings-element.md) 部分以包含菜单名称（菜单在 IDE 中显示时），并包含一个 [CommandName](../extensibility/commandname-element.md) 元素以包含用于在“命令”窗口中访问菜单的命令的名称。  
  
         如果按钮文本字符串包含“&”字符，则用户可通过按 ALT 加上紧跟“&”之后的字符打开菜单。  
  
    5.  根据需要添加命令标志，以更改菜单的外观和行为。 若要执行此操作，请在菜单定义中添加 [CommandFlag](../extensibility/command-flag-element.md) 元素。 有关详细信息，请参阅[命令标志元素](../extensibility/command-flag-element.md)。  
  
5.  设置菜单的父项。 对于标准菜单或子菜单，请根据你的设计用以下方法之一实现此目的：  
  
    -   在 `Menu` 元素中，创建一个 [Parent](../extensibility/parent-element.md) 元素，并将其 `guid` 和 `id` 字段设置为将承载菜单的组的 GUID:ID（也称为*主父组*）。 父组可以是你在 `Symbols` 部分中创建的组、来自另一个包的组或来自 IDE 的组。 例如，若要向 IDE 的顶级菜单栏添加菜单，请在“工具”菜单附近将父项设置为 guidSHLMainMenu:IDG\_VS\_MM\_TOOLSADDINS。  
  
         下面的示例演示将在 Visual Studio 菜单栏上显示的一个菜单。  
  
         [!CODE [TopLevelMenu#01](../CodeSnippet/VS_Snippets_VSSDK/toplevelmenu#01)]  
  
    -   如果菜单是通过使用命令放置来定位的，则可以忽略 `Parent`。 在 `Symbols` 部分之前创建 [CommandPlacements](../extensibility/commandplacements-element.md) 部分，并添加具有菜单的 GUID:ID、优先级和父项的 [CommandPlacement](../extensibility/commandplacement-element.md)，如下面的示例所示。  
  
         [!CODE [ButtonGroup#04](../CodeSnippet/VS_Snippets_VSSDK/buttongroup#04)]  
  
         创建具有相同 GUID:ID 和不同父级的多个命令放置会导致菜单在多个位置显示。 有关更多信息，请参见[CommandPlacements 元素](../extensibility/commandplacements-element.md)。  
  
     标准菜单必须以 Visual Studio 菜单栏上的组作为其父项。 对于子菜单，父项必须是另一个菜单（或工具栏或其他菜单类型）上的组。 对于将显示的菜单或子菜单，它必须承载包含至少一个活动命令的组，或设置 `AlwaysCreate` 命令标志。  
  
     快捷菜单不具有父项或命令放置。 相反，它们必须在代码中激活。 通常情况下，快捷菜单会在响应控件图面上的右键单击时被激活。 下面的示例定义一个快捷菜单。  
  
     [!CODE [ButtonGroup#06](../CodeSnippet/VS_Snippets_VSSDK/buttongroup#06)]  
  
6.  在 [Groups](../extensibility/groups-element.md) 部分中，创建一个 [Group](../extensibility/group-element.md) 元素以包含将显示在你的菜单上的命令。`Symbols` 部分必须包含一个与 `Group` 元素具有相同 GUID:ID 的项。  
  
    1.  设置组的优先级，使其出现在菜单上你所希望的位置。  
  
         菜单上每个组的边界将显示为水平线。  
  
    2.  将这一新组的父项设置为你所创建的菜单的 GUID:ID。 执行此操作会将命令组放置于菜单上。  
  
     以下示例中的组将出现在前述示例中所示的顶级菜单上。  
  
     [!CODE [TopLevelMenu#02](../CodeSnippet/VS_Snippets_VSSDK/toplevelmenu#02)]  
  
     菜单可以同时包含命令和子菜单。 子菜单（有时成为级联菜单）也是菜单，但它被添加到另一个菜单的组中，且仅当调用另一个菜单时才会显示出来。 将以下示例所示的菜单放置在顶级菜单的组中，即将其变为子菜单。  
  
     [!CODE [TopLevelMenu#06](../CodeSnippet/VS_Snippets_VSSDK/toplevelmenu#06)]  
  
7.  在 [Buttons](../extensibility/buttons-element.md) 部分中创建命令项，并将每一项的父项设置为组的 GUID:ID，即可向菜单添加命令。 每个 [Button](../extensibility/button-element.md) 元素都必须有与 `Symbols` 部分中的项相对应的 GUID:ID。  
  
     使用每个按钮项的 `priority` 特性来指定命令在组中的显示顺序。  
  
     下面的示例定义了将显示在顶级菜单上的命令。  
  
     [!CODE [TopLevelMenu#03](../CodeSnippet/VS_Snippets_VSSDK/toplevelmenu#03)]  
  
     有关按钮和菜单项的详细信息，请参阅 [Button 元素](../extensibility/button-element.md)。  
  
     有关如何在代码中实现菜单命令的信息，请参阅[MenuCommands 与 OleMenuCommands](../misc/menucommands-vs-olemenucommands.md) 或本主题中的前述演练。  
  
### 激活快捷菜单  
  
1.  获取快捷菜单的 GUID:ID。 默认情况下，包模板将在 PkgCmdID.cs 文件中创建 `GuidList` 类，用于保存命令集的 GUID。 该模板还将在 PkgCmdId.cs 文件中创建 `PkgCmdIdList` 类，用于保存在模板中声明的命令的整数 ID 值。 快捷菜单和任何其他命令必须在套用完模板后进行声明。 下面的示例演示了这些声明。  
  
     [!CODE [TWShortcutMenu#12](../CodeSnippet/VS_Snippets_VSSDK/twshortcutmenu#12)]  
  
     如果将直接使用 GUID 和 ID 值，则可省略此步骤。 但是，我们建议在此处设置值以便阅读。  
  
2.  附加到事件处理程序。 通常情况下，快捷菜单附加到控件图面的右键单击，如下面的示例所示。  
  
     [!CODE [TWShortcutMenu#43](../CodeSnippet/VS_Snippets_VSSDK/twshortcutmenu#43)]  
  
     <xref:System.Windows.Forms.Control.PointToScreen%2A> 方法会将相对于控件的单击位置转换为屏幕位置。<xref:Microsoft.VisualStudio.Shell.OleMenuCommandService.ShowContextMenu%2A> 方法显示快捷菜单。  
  
     包含事件处理程序的文件必须包括 <xref:System.ComponentModel.Design> 命名空间以访问 <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> 类，还必须包括 <xref:Microsoft.VisualStudio.Shell> 命名空间以访问 <xref:System.ComponentModel.Design.IMenuCommandService> 接口。  
  
     [!CODE [TWShortcutMenu#41](../CodeSnippet/VS_Snippets_VSSDK/twshortcutmenu#41)]  
  
## 请参阅  
 [MenuCommands 与 OleMenuCommands](../misc/menucommands-vs-olemenucommands.md)   
 [VSCT XML 架构参考](../extensibility/vsct-xml-schema-reference.md)   
 [扩展的菜单和命令](../extensibility/extending-menus-and-commands.md)