---
title: "命令标志元素 | Microsoft Docs"
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
  - "CommandFlag 元素 (VSCT XML 架构)"
  - "VSCT XML 架构元素 CommandFlag"
ms.assetid: 5ef63399-d2db-4dc1-97ce-be1bd4ef4e39
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# 命令标志元素
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

修改其父元素。  
  
## 语法  
  
```  
<CommandFlag>DynamicVisibility</CommandFlag>  
```  
  
## 特性和元素  
 以下部分描述了有效的元素值。  
  
### 特性  
 无。  
  
### 子元素  
  
|值|描述|  
|-------|--------|  
|AllowParams|指示用户可以输入中的命令参数 **命令** 窗口在其中键入该命令的规范名称。<br /><br /> 适用于: `Button`|  
|AlwaysCreate|即使它具有任何组或按钮创建菜单。<br /><br /> 适用于: `Menu`|  
|CaseSensitive|用户项是区分大小写。<br /><br /> 适用于: `Combo`|  
|CommandWellOnly|如果命令未显示在顶级菜单上，并且你想要使其适用于其他外壳自定义设置，例如，用于将其绑定到的键盘快捷方式，将应用此标志。 安装 VSPackage 后，你可以自定义这些命令打开 **选项** 对话框中，然后编辑下的命令放置 **键盘环境** 类别。 此标志不会影响在快捷菜单、 工具栏、 菜单控制器或子菜单上的位置。<br /><br /> 对于有效: `Button`, ，`Combo`|  
|DefaultDisabled|默认情况下，该命令已禁用，如果未加载 VSPackage，实现该接口或 `QueryStatus` 不调用方法。<br /><br /> 对于有效: `Button`, ，`Combo`|  
|DefaultDocked|停靠在默认情况下。 此设置，将不再适用于工具栏，因为它们始终的停靠。|  
|DefaultInvisible|默认情况下，该命令是不可见，如果未加载 VSPackage，实现该接口或 `QueryStatus` 不调用方法。<br /><br /> 我们建议您将组合这一点与 `DynamicVisibility` 标志。<br /><br /> 对于有效: `Button`, ，`Combo`, ，`Menu`|  
|DontCache|开发环境不会缓存 `QueryStatus` 此命令的方法的结果。<br /><br /> 对于菜单，这将告知未要缓存其菜单项的文本的菜单控制器。 当菜单包含动态项或项具有动态文本时，请使用此标志。<br /><br /> 对于有效: `Button`, ，`Menu`|  
|DynamicItemStart|指示动态列表的开头。 这可以使环境来通过连续调用生成的列表 `QueryStatus` 直到返回 OLECMDERR\_E\_UNSUPPORTED 标志的列表项上的方法。 这非常适合于项如最近使用过的 \(MRU\) 列表和窗口列表。<br /><br /> 适用于: `Button`|  
|DynamicVisibility|该命令的可见性，可以通过更改 `QueryStatus` 方法或通过上下文中包含的 GUID `VisibilityConstraints` 部分。<br /><br /> 适用于显示菜单和工具窗口工具栏上，而不是在顶层出现在主窗口的工具栏上显示的命令。 顶层工具栏项可以禁用，但不是能隐藏从返回 OLECMDF\_INVISIBLE 标志时 `QueryStatus` 方法。 可以隐藏工具窗口工具栏显示的工具栏命令。<br /><br /> 在菜单上，此标志还指示，它时，应会自动隐藏其所有成员处于隐藏都状态。 因为顶级菜单中已有此行为，此标志通常会分配给子菜单。<br /><br /> 此标志应结合 `DefaultInvisible` 标志。<br /><br /> 对于有效: `Button`, ，`Combo`, ，`Menu`|  
|筛选键|请参阅下的筛选键主题 [组合元素](../extensibility/combo-element.md)。<br /><br /> 适用于: `Combo`|  
|FixMenuController|如果此命令将位于菜单控制器，该命令始终是默认设置;也就是说，选择该命令时选择菜单控制器按钮本身时。 如果菜单控制器有 `TextIsAnchorCommand` 标志设置，则菜单控制器还将其文本的命令从 `FixMenuController` 标志。<br /><br /> 在菜单控制器上的只能有一个命令应具有 `FixMenuController` 标志。 因此标记多个命令，如果菜单中的最后一个命令将成为默认命令。<br /><br /> 适用于: `Button`|  
|IconAndText|在菜单和工具栏上显示的图标和文本。<br /><br /> 对于有效: `Button`, ，`Combo`, ，`Menu`|  
|NoAutoComplete|记忆式键入功能被禁用。<br /><br /> 适用于: `Combo`|  
|NoButtonCustomize|不要让用户可以自定义此按钮。<br /><br /> 对于有效: `Button`, ，`Combo`|  
|NoKeyCustomize|不要启用键盘自定义。<br /><br /> 对于有效: `Button`, ，`Combo`|  
|NoShowOnMenuController|如果此命令位于菜单控制器上，该命令不未出现在下拉列表中。<br /><br /> 适用于: `Button`|  
|NotInTBList|不出现在可用工具栏的列表中。 这是仅对工具栏菜单类型有效。<br /><br /> 适用于: `Menu`|  
|NoToolbarClose|用户不能关闭工具栏。 这是仅对工具栏菜单类型有效。<br /><br /> 适用于: `Menu`|  
|Pict|在工具栏上，但只在菜单上的文本上显示仅一个图标。 如果指定无图标，显示工具栏上单击空白区域。<br /><br /> 适用于: `Button`|  
|PostExec|使命令非阻塞。 开发环境推迟到执行预处理的所有查询都已都完成。<br /><br /> 适用于: `Button`|  
|RouteToDocs|该命令路由到活动文档。<br /><br /> 适用于: `Button`|  
|StretchHorizontally|当设置此标志时，宽度将成为最小宽度的组合框中，而如果在工具栏上的空间，组合框拉伸以填充可用空间。 仅当水平停靠工具栏上，且在工具栏上的只有一个组合框可以使用的标志 \(所有除第一个组合框忽略该标志\)，将发生这种情况。<br /><br /> 适用于: `Combo`|  
|TextMenuUseButton|使用 `ButtonText` 字段中为菜单。 默认字段是 `MenuText` 如果已指定。<br /><br /> 适用于: `Button`|  
|TextChanges|命令或菜单文本可以在运行时，通常通过更改 `QueryStatus` 方法。<br /><br /> 对于有效: `Button`, ，`Menu`|  
|TextChangesButton|适用于: `Button`|  
|TextIsAnchorCommand|对于菜单控制器而言，菜单上的文本摘自默认 \(定位点\) 命令。 一个定位点命令，选择或闩锁的最后一个命令。 如果未设置此标志，菜单控制器将使用其自己 `MenuText` 字段。 但是，单击菜单控制器仍可启用从该控制器的最后一个所选的命令。<br /><br /> 我们建议您将组合使用此标志 `TextChanges` 标志。<br /><br /> 此标志仅适用于类型的菜单 MenuController 或 MenuControllerLatched。<br /><br /> 适用于: `Menu`|  
|TextMenuCtrlUseMenu|使用 `MenuText` 菜单控制器上的字段。 默认字段是 `ButtonText`。<br /><br /> 适用于: `Button`|  
|TextMenuUseButton|使用 `ButtonText` 字段中为菜单。 默认字段是 `MenuText` 如果已指定。<br /><br /> 适用于: `Button`|  
|TextOnly|即使指定了图标，请在工具栏或菜单上，但无图标上显示纯文本。<br /><br /> 适用于: `Button`|  
  
### 父元素  
  
|元素|描述|  
|--------|--------|  
|[按钮元素](../extensibility/buttons-element.md)|提供了一组为 [Button 元素](../extensibility/button-element.md) 元素。|  
|[菜单元素](../extensibility/menus-element.md)|定义 VSPackage 实现的所有菜单。|  
  
## 请参阅  
 [Visual Studio 命令表 \(。Vsct\) 文件](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)