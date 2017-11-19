---
title: "命令放置准则 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- commands, small command sets
- small command sets
- command sets
ms.assetid: 63b3478e-e08a-420b-a0ec-76767e0cb289
caps.latest.revision: "28"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e74bda24459bedeef007b451c7fabe3922e7ab37
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="command-placement-guidelines"></a>命令放置准则
在 Visual Studio 集成的开发环境 (IDE) 中定位命令的最佳方案而异命令集的大小。 命令定义，并根据.vsct 文件中的信息调整位置。  
  
## <a name="best-practices-for-all-command-sets"></a>所有的命令集的最佳实践  
 每个命令集，请遵循以下准则：  
  
-   提前准备命令结构图表。 标识命令、 组合框、 命令组和将多个位置中使用的快捷菜单。  
  
-   显示同一组中的命令应该与相关。  
  
-   包含一个命令的组是可接受的。  
  
-   包不应将大量命令添加到现有 Visual Studio 菜单。 相反，他们应创建菜单或子菜单来承载新的命令。  
  
-   当你将命令在现有的菜单上，名称命令以便清除其用途且不将与现有命令混淆。  
  
## <a name="best-practices-for-small-command-sets"></a>对于小命令集的最佳做法  
 如果你正在开发 VSPackage 包含几个命令，也请遵循以下准则：  
  
-   如果可能，请使用[父元素](../../extensibility/parent-element.md)的命令、 组合框、 组或子菜单将其放在相应的组。  
  
-   将这些组分配给由 VSPackage 显示的菜单。  
  
-   子菜单或命令的父项必须是[组元素](../../extensibility/group-element.md)。 将命令和子菜单分配给组，并将组分配给父菜单。  
  
-   你可以通过添加其他组中将命令[CommandPlacements 元素](../../extensibility/commandplacements-element.md)部分的命令，在定义之后，随后向添加`CommandPlacements Element` [CommandPlacement 元素](../../extensibility/commandplacement-element.md)每个其他组。  
  
## <a name="best-practices-for-large-command-sets"></a>对于较大的命令集的最佳做法  
 如果你的 VSPackage 将要包含在多个上下文中将出现的很多命令，也请遵循以下准则：  
  
-   请菜单、 组和命令自用作父级。 也就是说，不分配`Parent Element`中的项的定义。  
  
-   使用`CommandPlacement Element`中的条目`CommandPlacements Element`部分将在其父菜单和组的菜单、 组和命令。  
  
-   在`CommandPlacements`部分，填充给定的菜单的条目或组应处于彼此相邻。 这有助于提高可读性并使`Priority`排名更方便地确定。  
  
## <a name="see-also"></a>另请参阅  
 [Vspackage 如何添加用户界面元素](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Visual Studio 命令表格 (.Vsct) 文件](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)