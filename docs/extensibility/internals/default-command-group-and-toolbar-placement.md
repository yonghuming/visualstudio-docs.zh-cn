---
title: "默认命令、 组和工具栏放置 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- commands [Visual Studio], default groups
- toolbars [Visual Studio], default
- commands [Visual Studio], default editor
- command groups
- commands [Visual Studio], default IDE
- commands [Visual Studio], default product
ms.assetid: 35342110-d639-4577-8367-00b21dcc6f07
caps.latest.revision: 30
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
ms.openlocfilehash: 1d418eea04791d85dd0e8d08fba23abe8dc7e054
ms.lasthandoff: 02/22/2017

---
# <a name="default-command-group-and-toolbar-placement"></a>默认的命令、 组和工具栏位置
有关产品的一致性和稳定性，用户界面所显示的默认情况下的某些命令组和[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]提供的命令和命令组的定义。 标准命令和命令组，还可以使用 Vspackage。  
  
 默认的命令组分为三类︰ IDE 命令、 产品命令和编辑器命令。  
  
## <a name="default-ide-commands"></a>默认 IDE 命令  
 默认 IDE 工具栏包括命令中包含的所有产品由共享[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 其中包括与泛型项目操作，如相关的命令**保存**命令和**添加项**命令。 Vspackage 应不加上或减去从此工具栏中，有一处例外︰ 如果产品或 VSPackage 添加一个新的工具窗口，然后在情况下，窗口中应添加到可用的工具窗口的列表**视图**菜单。 新的产品或 Vspackage 可以添加自己的工具栏。  
  
## <a name="default-product-commands"></a>默认产品命令  
 每个产品可以提供 IDE，它具有自己的默认工具栏，其中包含重要并经常使用的命令。 最好是，但是，若要使用现有菜单和工具栏，只要有可能，放入其他特定于任务的工具栏根据需要。  
  
 为工具栏优先级字段确定其行位置。 零个优先级将工具栏放在菜单栏下的第三行 （第 3 行），（第 1 行） 和**标准**工具栏 （第 2 行）。 因此，其他工具栏将显示在一行 （优先级 + 3）。 后续工具栏位于同一行中，如果空间;否则，它们将自动移至下一行。  
  
## <a name="default-editor-commands"></a>默认值编辑器命令  
 提供了一个自定义编辑器的 VSPackage 应提供默认的工具栏，其中包含最重要并经常在该编辑器中使用的命令。 在编辑器处于活动状态和编辑器中未处于活动状态时，将隐藏时，应显示编辑器工具栏。 此可见性控制在`VisibilityConstraints Element`.vsct 文件。  
  
 IDE 和产品工具栏下方应放编辑器工具栏。  
  
## <a name="see-also"></a>另请参阅  
 [IDE 定义的命令、 菜单和组](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)   
 [Vspackage 如何添加用户界面元素](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
