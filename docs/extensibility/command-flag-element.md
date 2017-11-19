---
title: "命令标志元素 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- CommandFlag element (VSCT XML schema)
- VSCT XML schema elements, CommandFlag
ms.assetid: 5ef63399-d2db-4dc1-97ce-be1bd4ef4e39
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: cc69edbe0865953d242967490a0852c9da4942b3
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="command-flag-element"></a>命令标志元素
修改其父元素。  
  
## <a name="syntax"></a>语法  
  
```  
<CommandFlag>DynamicVisibility</CommandFlag>  
```  
  
## <a name="attributes-and-elements"></a>特性和元素  
 以下部分描述有效的元素值。  
  
### <a name="attributes"></a>特性  
 无。  
  
### <a name="child-elements"></a>子元素  
  
|值|描述|  
|-----------|-----------------|  
|AllowParams|指示用户可以输入中的命令参数**命令**窗口在其中键入该命令的规范名称。<br /><br /> 适用于：`Button`|  
|AlwaysCreate|即使它具有任何组或按钮创建菜单。<br /><br /> 适用于：`Menu`|  
|CaseSensitive|用户的项是区分大小写。<br /><br /> 适用于：`Combo`|  
|CommandWellOnly|如果该命令不显示在顶级菜单上，你想要使其可供其他外壳自定义设置，例如，用于绑定到的键盘快捷方式，应用此标志。 安装 VSPackage 后，你可以自定义这些命令打开**选项**对话框中，然后编辑下的命令放置**键盘环境**类别。 此标志不会影响在快捷菜单、 工具栏、 菜单控制器或子菜单上的位置。<br /><br /> 有关有效： `Button`，`Combo`|  
|DefaultDisabled|默认情况下，如果未加载 VSPackage 实现它禁用命令或`QueryStatus`尚未调用方法。<br /><br /> 有关有效： `Button`，`Combo`|  
|DefaultDocked|默认情况下停靠。 此设置不再适用于工具栏中，因为它们始终停靠。|  
|DefaultInvisible|默认情况下，该命令是未加载 VSPackage 实现它的情况下不可见或`QueryStatus`尚未调用方法。<br /><br /> 我们建议你将结合这一点与`DynamicVisibility`标志。<br /><br /> 有关有效： `Button`， `Combo`，`Menu`|  
|DontCache|开发环境不会缓存`QueryStatus`方法为此命令的结果。<br /><br /> 对于菜单，这将告知菜单控制器无法缓存其菜单项的文本。 菜单包含动态项或具有动态文本的项时，请使用此标志。<br /><br /> 有关有效： `Button`，`Menu`|  
|DynamicItemStart|指示动态列表的开头。 这使该环境以通过连续调用生成列表`QueryStatus`列表项之前返回 OLECMDERR_E_UNSUPPORTED 标志的方法。 这非常适用于项如最近使用 (过的 MRU) 列表和窗口列表的不同而不同。<br /><br /> 适用于：`Button`|  
|DynamicVisibility|该命令的可见性，可以通过更改`QueryStatus`方法或通过上下文中包含的 GUID`VisibilityConstraints`部分。<br /><br /> 适用于显示菜单和工具窗口工具栏，而不是显示在主窗口中的顶层工具栏上的命令。 可以禁用但不是能隐藏从返回 OLECMDF_INVISIBLE 标志时顶层工具栏项`QueryStatus`方法。 可以隐藏工具窗口工具栏显示的工具栏命令。<br /><br /> 在菜单上，此标志还指示，它应被自动隐藏时隐藏其所有成员。 因为顶级菜单中已有此行为，此标志通常会分派给子菜单。<br /><br /> 此标志应与组合`DefaultInvisible`标志。<br /><br /> 有关有效： `Button`， `Combo`，`Menu`|  
|筛选键|请参阅下的筛选键主题[组合元素](../extensibility/combo-element.md)。<br /><br /> 适用于：`Combo`|  
|FixMenuController|如果此命令位于菜单控制器，则命令始终是默认设置;也就是说，选择该命令时每当本身菜单控制器按钮处于选中状态。 如果菜单控制器具有`TextIsAnchorCommand`标志设置，则菜单控制器还将使用的命令从其文本`FixMenuController`标志。<br /><br /> 菜单控制器上的只能有一个命令应具有`FixMenuController`标志。 如果因此标记为多个命令，在菜单中的最后一个命令将成为默认命令。<br /><br /> 适用于：`Button`|  
|IconAndText|菜单和工具栏上显示的图标和文本。<br /><br /> 有关有效： `Button`， `Combo`，`Menu`|  
|NoAutoComplete|自动完成功能被禁用。<br /><br /> 适用于：`Combo`|  
|NoButtonCustomize|不要让用户可以自定义此按钮。<br /><br /> 有关有效： `Button`，`Combo`|  
|NoKeyCustomize|不要启用键盘自定义。<br /><br /> 有关有效： `Button`，`Combo`|  
|NoShowOnMenuController|如果此命令位于菜单控制器，该命令不出现在下拉列表中。<br /><br /> 适用于：`Button`|  
|NotInTBList|不在列表中可用的工具栏。 这是仅对工具栏菜单类型有效。<br /><br /> 适用于：`Menu`|  
|NoToolbarClose|用户无法关闭工具栏。 这是仅对工具栏菜单类型有效。<br /><br /> 适用于：`Menu`|  
|图像|在工具栏上，但仅在菜单上的文本中显示仅图标。 如果未指定图标，显示工具栏上的可单击的空白区域。<br /><br /> 适用于：`Button`|  
|PostExec|使命令非阻塞。 开发环境延迟执行，直到完成所有预先处理查询。<br /><br /> 适用于：`Button`|  
|RouteToDocs|该命令路由到活动文档。<br /><br /> 适用于：`Button`|  
|StretchHorizontally|当设置此标志时，宽度变成的组合框中，最小宽度，而如果在工具栏上的空间，组合框拉伸以填充可用空间。 仅当水平停靠工具栏，且在工具栏上只有一个组合框可以使用的标志 （标志将忽略在第一个组合框除外），将发生这种情况。<br /><br /> 适用于：`Combo`|  
|TextMenuUseButton|使用`ButtonText`字段对于菜单。 默认字段是`MenuText`如果指定此设置。<br /><br /> 适用于：`Button`|  
|TextChanges|命令或菜单文本可以在运行时，通常通过更改`QueryStatus`方法。<br /><br /> 有关有效： `Button`，`Menu`|  
|TextChangesButton|适用于：`Button`|  
|TextIsAnchorCommand|菜单控制器，菜单上的文本来自默认 （定位点） 命令。 定位点命令是处于选定状态或已锁定的最后一个命令。 如果未设置此标志，菜单控制器将使用其自己`MenuText`字段。 但是，单击菜单控制器仍可以启用该控制器中的最后一个所选的命令。<br /><br /> 我们建议你将结合使用此标志`TextChanges`标志。<br /><br /> 此标志仅适用于类型的菜单 MenuController 或 MenuControllerLatched。<br /><br /> 适用于：`Menu`|  
|TextMenuCtrlUseMenu|使用`MenuText`字段菜单控制器上。 默认字段是`ButtonText`。<br /><br /> 适用于：`Button`|  
|TextMenuUseButton|使用`ButtonText`字段对于菜单。 默认字段是`MenuText`如果指定此设置。<br /><br /> 适用于：`Button`|  
|TextOnly|即使指定图标，请在工具栏或菜单但没有图标上显示纯文本。<br /><br /> 适用于：`Button`|  
  
### <a name="parent-elements"></a>父元素  
  
|元素|描述|  
|-------------|-----------------|  
|[Buttons 元素](../extensibility/buttons-element.md)|提供的组[Button 元素](../extensibility/button-element.md)元素。|  
|[Menus 元素](../extensibility/menus-element.md)|定义 VSPackage 实现的所有菜单。|  
  
## <a name="see-also"></a>另请参阅  
 [Visual Studio 命令表格 (.Vsct) 文件](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)