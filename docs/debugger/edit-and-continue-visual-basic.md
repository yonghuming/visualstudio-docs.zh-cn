---
title: "编辑并继续 (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "VB"
helpviewer_keywords: 
  - "64 位编辑并继续"
  - "调试 [Visual Basic], 编辑并继续"
  - "编辑并继续 [Visual Basic]"
  - "编辑并继续, 64 "
  - "Visual Basic, 编辑并继续"
ms.assetid: 7e90f34f-e699-45ab-a4c9-a4b527c498c8
caps.latest.revision: 40
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 40
---
# 编辑并继续 (Visual Basic)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

“编辑并继续”是 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 调试的一项功能，当代码在中断模式下执行时，使用该功能可以更改代码。  在应用代码编辑后，可以就地继续执行新编辑过的代码并观察效果。  
  
 每次进入中断模式时都可以使用“编辑并继续”功能。  在中断模式下，指令指针（即源代码窗口中的黄色箭头）指向接下来将要执行的行，并将位于方法或属性体内的一条可执行语句上。  您可以在中断模式下对可执行语句进行几乎所有类型的更改，所做更改将被合并到基础项目中。  但是，在中断模式下一般不允许对声明语句（如公共方法、公共字段或类声明）进行更改。  
  
 如果进行了未经授权的编辑，则所做更改会被加上紫色波浪下划线标记，并且会在任务列表中显示一个任务。  如果要继续使用“编辑并继续”功能，必须撤消未经授权的编辑。  在“编辑并继续”之外，可能允许执行某些未经授权的编辑。  如果要保留这种未经授权的编辑的结果，必须停止调试并重新启动应用程序。  
  
 面向 .NET Framework 4.5.1 的 64 位项目支持“编辑并继续”。  
  
 当使用**“附加到进程”**启动调试时不支持“编辑并继续”。  优化代码、混合托管代码和本机代码或 Compact Framework（智能设备）项目都不支持“编辑并继续”。  
  
 本节中各个主题提供的详细信息涉及：如何使用此功能，允许进行哪些类型的更改。  
  
## 本节内容  
 [如何：使用“编辑并继续”在中断模式下应用编辑](../debugger/how-to-apply-edits-in-break-mode-with-edit-and-continue.md)  
 解释如何在中断模式下应用代码编辑。  
  
 [Visual Basic“编辑并继续”中不支持的编辑](../debugger/unsupported-edits-in-visual-basic-edit-and-continue.md)  
 描述了无法在 [!INCLUDE[vb_current_short](../debugger/includes/vb_current_short_md.md)]“编辑并继续”中执行的编辑的类型。  
  
## 相关章节  
 [编辑并继续](../debugger/edit-and-continue.md)  
 提供“编辑并继续”主题的列表。