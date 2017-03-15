---
title: "命令放置指南 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- commands, small command sets
- small command sets
- command sets
ms.assetid: 63b3478e-e08a-420b-a0ec-76767e0cb289
caps.latest.revision: 28
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
ms.openlocfilehash: ca84800a199e9db420379697051fece598eb9295
ms.lasthandoff: 02/22/2017

---
# <a name="command-placement-guidelines"></a>命令放置指导原则
最佳做法，用于在 Visual Studio 集成的开发环境 (IDE) 中定位的命令根据命令集的大小会有所不同。 定义命令和定位根据.vsct 文件中的信息。  
  
## <a name="best-practices-for-all-command-sets"></a>所有命令集的最佳做法  
 每个命令集，请遵循以下准则︰  
  
-   事先做好准备命令结构的图表。 标识命令、 组合框、 命令组和将用于多个位置中的快捷菜单。  
  
-   出现在同一组中的命令应该与相关。  
  
-   包含只是一个命令的组是可接受的。  
  
-   包不应在现有的 Visual Studio 菜单中添加大量命令。 相反，他们应创建菜单或子菜单以承载新的命令。  
  
-   当将一个命令在现有的菜单上，名称中的命令，以便清除其用途且不会与现有命令混淆。  
  
## <a name="best-practices-for-small-command-sets"></a>对于较小的命令集的最佳做法  
 如果要开发具有几个命令的 VSPackage，还请遵循以下准则︰  
  
-   如果可能，请使用[父元素](../../extensibility/parent-element.md)的命令、 组合框、 组或子菜单将其放在适当的组。  
  
-   将这些组分配到 VSPackage 所显示的菜单。  
  
-   父项的子菜单或命令必须是[组元素](../../extensibility/group-element.md)。 命令和子菜单，为组分配，然后将这些组分配到父菜单。  
  
-   你可以通过添加一个命令将在其他组[CommandPlacements 元素](../../extensibility/commandplacements-element.md)部分的命令，在定义之后，随后向添加`CommandPlacements Element` [CommandPlacement 元素](../../extensibility/commandplacement-element.md)为每个其他组。  
  
## <a name="best-practices-for-large-command-sets"></a>对于较大的命令集的最佳做法  
 如果你的 VSPackage 将具有很多命令将显示在多个上下文中，还请遵循以下准则︰  
  
-   请菜单、 组和自作为父级的命令。 也就是说，不要分配`Parent Element`中项的定义。  
  
-   使用`CommandPlacement Element`中的条目`CommandPlacements Element`部分，以将菜单、 组和命令放在其父菜单和组。  
  
-   在`CommandPlacements`部分填充给定的菜单项或组应该是彼此相邻。 这有助于提高可读性并使`Priority`更容易地确定排名。  
  
## <a name="see-also"></a>另请参阅  
 [Vspackage 如何添加用户界面元素](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Visual Studio 命令表 (。Vsct) 文件](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
