---
title: "“命中断点时”对话框 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.whenbreakpointishit"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "SQL"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 476e3d98-cf35-4338-b124-cd0f3010d854
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# “命中断点时”对话框
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

使用此对话框可以自定义命中断点时发生的操作。  
  
## UIElement 列表  
 **打印消息**  
 使用 DebuggerDisplay 语法打印消息。  有关详细信息，请参阅[使用 DebuggerDisplay 特性](../debugger/using-the-debuggerdisplay-attribute.md)。  
  
 此文本框还支持特殊关键字（如 $ADDRESS），这些关键字可以单独使用或者在 DebuggerDisplay 表达式的大括号中使用。  该对话框上列出了可用的关键字。  
  
 **继续执行**  
 仅当选择了**“打印消息”**时才启用此控件。  选择了此控件时，可以将断点用作跟踪点来跟踪程序执行，而不是在命中该位置时中断。  
  
## 请参阅  
 [使用断点](../debugger/using-breakpoints.md)   
 [使用 DebuggerDisplay 特性](../debugger/using-the-debuggerdisplay-attribute.md)