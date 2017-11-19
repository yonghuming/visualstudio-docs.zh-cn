---
title: "向用户反馈 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- user model feedback
- environment, context
- IDE, context
- IDE, user feedback
ms.assetid: 2d472a24-3813-4f5f-9783-b491ad8a71ad
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ffc6ecc620f57f0cc1e4dd8baf02f1bd1b17d53b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="feedback-to-the-user"></a>向用户的反馈
在[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]集成的开发环境 (IDE)，有关可用的功能取决于用户的当前所选内容和全局选择上下文的视觉反馈。 下表列出不同的选择上下文中提供的功能。  
  
|选择上下文|可用的功能|  
|-----------------------|-----------------------------|  
|IDE|Global|  
|当前的产品集|产品特定|  
|活动的层次结构|特定层次结构类型|  
|活动的层次结构项|特定层次结构项类型|  
|活动文档|特定于文档类型|  
|最顶层的多文档界面 (MDI) 窗口|特定窗口类型|  
|当前选定内容上下文|选择特定的上下文|  
  
 如果仅呈现用户需要并不断地提供一致的选择和环境上下文反馈的功能，你可以减少 IDE 中的复杂性。 每次在 IDE 中打开一个窗口，将应用以下规则：  
  
-   如果窗口更改其选择上下文，所选内容的反馈清楚地表明后，在窗口中，并且动态帮助窗口中，如果所示，将更新以反映当前上下文。  
  
-   如果窗口更改全局选择上下文，所有特定于上下文菜单、 的有效层次结构窗口中，以及应用程序标题栏将更新以反映当前上下文。  
  
-   窗口应图面中的当前选择的属性**属性**窗口和 （可选） 如果所示，**属性页**对话框。  
  
-   当它不再是活动窗口在 IDE 中时，如果该窗口不外围属性或更改全局选择上下文，所选内容的反馈应不会保留在该窗口中。  
  
-   所有文档特定工具窗口持续应都反映活动文档。  
  
-   菜单、 工具栏和应用程序标题栏应反映最顶层的多文档界面 (MDI) 客户端窗口。  
  
 例如，如果打开 Web 窗体在 Visual Basic Web 应用程序项目内的 HTML 视图，并在用户选择`<td>`标记中，按以下方式提供反馈：  
  
-   选择是指示在活动的窗口中，并反映在**属性**窗口。  
  
-   特定于文档的**工具箱**更新以反映活动文档。  
  
-   **编辑器**工具栏和**表**显示菜单和标题栏更新以反映 Web 窗体的窗口。  
  
-   活动的层次结构窗口，这通常是**解决方案资源管理器**，和其标题栏更新以反映当前上下文和上下文相关**项目**菜单命令将应用于活动站点应用程序项目。  
  
## <a name="see-also"></a>另请参阅  
 [选择和 IDE 中的货币](../../extensibility/internals/selection-and-currency-in-the-ide.md)   
 [选择上下文对象](../../extensibility/internals/selection-context-objects.md)   
 [层次结构和选择](../../extensibility/internals/hierarchies-and-selection.md)