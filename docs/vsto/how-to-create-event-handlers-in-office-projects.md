---
title: "如何：在 Office 项目中创建事件处理程序 | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "事件处理程序 [Visual Studio 中的 Office 开发]"
  - "事件 [Visual Studio 中的 Office 开发]"
  - "Visual Basic [Visual Studio 中的 Office 开发], 事件处理程序"
  - "Visual C# [Visual Studio 中的 Office 开发], 事件处理程序"
ms.assetid: 2cfd6a45-4c25-4431-b4fc-e0f2c0a72e54
caps.latest.revision: 31
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 30
---
# 如何：在 Office 项目中创建事件处理程序
  可通过多种方式在 Visual Basic 和 C\# 中创建事件处理程序。  在设计视图中，可以通过双击控件来创建控件的默认事件处理程序，也可以使用**“属性”**窗口的事件窗格为控件的任何事件创建处理程序。  但是，如果您在代码视图中，那么可能不希望为了创建事件处理程序而切换到设计视图。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### 在 Visual Basic 中创建事件处理程序  
  
1.  从代码编辑器顶部的**“类名”**下拉列表中，选择要为其创建事件处理程序的对象。  
  
    > [!NOTE]  
    >  如果要为 `ThisDocument` 或 `ThisWorkbook` 创建事件处理程序，则必须在**“类名”**下拉列表中选择 **“\(ThisDocument 事件\)”**或**“\(ThisWorkbook 事件\)”**  
  
2.  从代码编辑器顶部的**“方法名”**下拉列表中选择事件。  
  
     Visual Studio 即为其创建事件处理程序并将插入点移动到新创建的事件处理程序。  如果该事件处理程序已存在，则插入点移动到现有的事件处理程序。  
  
### 在 C\# 中创建事件处理程序  
  
1.  通过键入限定的事件名再键入一个空格，然后键入 \+\=（后面没有空格），可以在类的 **Startup** 事件中创建事件委托。  例如：  
  
     `this.<object name>.<event name> +=`  
  
2.  在代码行末尾按两次 Tab 键。  
  
     Visual Studio 将自动完成代码行，创建事件处理程序，并将插入点移动到新创建的事件处理程序。  
  
## 请参阅  
 [在 Office 解决方案中编写代码](../vsto/writing-code-in-office-solutions.md)   
 [演练：根据 NamedRange 控件的事件进行编程](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md)   
 [生成 Office 解决方案](../vsto/building-office-solutions.md)  
  
  