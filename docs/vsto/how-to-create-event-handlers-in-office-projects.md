---
title: "如何： 在 Office 项目中创建事件处理程序 |Microsoft 文档"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual Basic [Office development in Visual Studio], event handlers
- event handlers [Office development in Visual Studio]
- Visual C# [Office development in Visual Studio], event handlers
- events [Office development in Visual Studio]
ms.assetid: 2cfd6a45-4c25-4431-b4fc-e0f2c0a72e54
caps.latest.revision: "31"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: af681832a8c298427c13060d858b57b99654953a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-create-event-handlers-in-office-projects"></a>如何：在 Office 项目中创建事件处理程序
  有多种 Visual Basic 和 C# 中创建事件处理程序。 在设计视图中，你可以通过双击控件，创建默认值为控件的事件处理程序或使用的事件窗格**属性**窗口控件上创建任何事件的处理。 但是，如果要在代码视图中，你可能不想要切换到设计视图，以创建一个事件处理程序。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### <a name="to-create-an-event-handler-in-visual-basic"></a>若要在 Visual Basic 中创建事件处理程序  
  
1.  从**类名**代码编辑器顶部的下拉列表，选择你希望的对象创建的事件处理程序。  
  
    > [!NOTE]  
    >  如果你想要创建事件处理程序`ThisDocument`或`ThisWorkbook`，您必须选择**（ThisDocument 事件）**或**（ThisWorkbook 事件）**中**类名**下拉列表  
  
2.  从**方法名称**下拉列表在顶部的代码编辑器中，选择事件。  
  
     Visual Studio 创建事件处理程序，并将插入点移到新创建的事件处理程序。 如果事件处理程序已存在，插入点移到现有的事件处理程序。  
  
### <a name="to-create-an-event-handler-in-c"></a>在 C# 中创建事件处理程序  
  
1.  创建中的事件委托**启动**通过键入限定的事件名称后, 跟一个空格，然后键入类事件的 **+=** 没有空格。 例如:   
  
     `this.<object name>.<event name> +=`  
  
2.  在代码的行结束时，按 TAB 键两次。  
  
     Visual Studio 自动完成的代码行，创建事件处理程序，并将插入点移到新创建的事件处理程序。  
  
## <a name="see-also"></a>另请参阅  
 [在 Office 解决方案中编写代码](../vsto/writing-code-in-office-solutions.md)   
 [演练： 针对 NamedRange 控件的事件进行编程](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md)   
 [生成 Office 解决方案](../vsto/building-office-solutions.md)  
  
  