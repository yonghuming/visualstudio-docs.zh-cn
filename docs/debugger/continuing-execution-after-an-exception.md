---
title: "在出现异常之后继续执行 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
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
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "调试器, 异常"
  - "异常处理, 之后继续执行"
  - "“异常”对话框"
  - "异常, 之后继续执行"
  - "执行, 异常之后继续"
  - "托管代码, 异常处理"
  - "托管异常, 之后继续执行"
  - "程序执行"
  - "程序, 执行"
  - "线程处理 [Visual Studio], 出现异常后继续执行"
ms.assetid: 6fe97aac-2131-4615-bd92-d3afee741558
caps.latest.revision: 25
caps.handback.revision: 25
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 在出现异常之后继续执行
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

当调试器因出现异常而中断执行时，会显示一个对话框。  对于 Visual Basic 或 C\#，默认情况下，您将看到[Exception Assistant](../Topic/Exception%20Assistant.md)对话框。  对于 C\+\+，您将看到较早的**“异常”**对话框。  如果您使用的是 Visual Basic 或 C\#，但已在**“选项”**对话框中禁用**“异常助手”**，则您将看到**“异常”**对话框。  
  
 在出现**“异常助手”**或**“异常”**对话框时，您可以尝试修复导致异常的问题。  
  
## 托管代码  
 在托管代码中，您可以在出现未经处理的异常后在同一线程内继续执行。  **“异常助手”**将调用堆栈回退到引发异常的点。  
  
## 本机代码  
 在本机 C\/C\+\+ 中，您有两个选项：  
  
-   您可以单击**“中断”**并尝试修复问题。  在中断模式下，您可以右键单击**“调用堆栈”**窗口中的帧并选择快捷菜单中的**“展开到此帧”**来展开调用堆栈。  如果未能修复问题，则继续调试时，**“异常”**对话框将再次显示。  否则，**“异常”**对话框将不会再次出现。  
  
-   您可以单击**“继续”**以继续执行，而不尝试修复问题。  **“异常”**对话框随即重新出现。  
  
## 混合模式  
 如果在调试本机和托管混合的代码时遇到未经处理的异常，则操作系统约束将阻止调用堆栈展开。  如果尝试使用快捷菜单来展开调用堆栈，则会出现一个错误消息，告诉您在混合代码调试期间，调试器无法在异常未得到处理的情况下展开调用堆栈。  
  
## 请参阅  
 [管理调试器的异常](../debugger/managing-exceptions-with-the-debugger.md)