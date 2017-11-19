---
title: "默认命令、 组和工具栏放置 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
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
caps.latest.revision: "30"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c5f1ec42408e4fd7d33d9445ae09252fae8d03db
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="default-command-group-and-toolbar-placement"></a>默认命令、 组和工具栏放置
有关产品一致性和稳定性，UI 所显示的默认情况下的某些命令组和[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]为命令和命令组提供了定义。 标准命令和命令组，还可以使用 Vspackage。  
  
 默认命令组分为三个类别： IDE 命令、 产品命令和编辑器命令。  
  
## <a name="default-ide-commands"></a>默认 IDE 命令  
 默认 IDE 工具栏包含共享的所有产品中包含的命令[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 其中包括与泛型项目操作，如相关的命令**保存**命令和**添加项**命令。 Vspackage 不应将添加到或减去此工具栏上，有一个例外： 如果产品或 VSPackage 添加一个新的工具窗口，则应将窗口添加到可用的工具窗口的列表上**视图**菜单。 新的产品或 Vspackage 可以添加自己的工具栏。  
  
## <a name="default-product-commands"></a>默认产品命令  
 每个产品可以提供具有自己的默认工具栏包含重要并经常使用的命令的 IDE。 它是最好的但是，使用现有的菜单和工具栏尽可能并根据需要补充它们与其他特定于任务的工具栏。  
  
 工具栏的优先级字段确定其行位置。 零个优先级将工具栏放置在菜单栏下的第三个行 （第 3 行），（行 1） 和**标准**工具栏 （第 2 行）。 因此，其他工具栏显示在行 （优先级 + 3）。 后续工具栏位于同一行中，当有空间;否则，它们将自动移到下一行。  
  
## <a name="default-editor-commands"></a>默认值编辑器命令  
 VSPackage 提供的自定义编辑器应提供默认的工具栏包含最重要并经常在该编辑器中使用的命令。 编辑器处于活动状态，并且当编辑器处于非活动状态时应隐藏时，应显示编辑器工具栏。 在中控制此可见性`VisibilityConstraints Element`的.vsct 文件。  
  
 IDE 和产品工具栏下方应放编辑器工具栏。  
  
## <a name="see-also"></a>另请参阅  
 [IDE 定义命令、 菜单和组](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)   
 [VSPackage 如何添加用户界面元素](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)