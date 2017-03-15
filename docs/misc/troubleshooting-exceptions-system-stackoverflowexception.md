---
title: "关于异常的疑难解答：System.StackOverflowException | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "StackOverflowException 类"
ms.assetid: 51b71217-c507-4f5b-bc35-0236180d7968
caps.latest.revision: 20
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 关于异常的疑难解答：System.StackOverflowException
当嵌套的方法调用过多而导致执行堆栈溢出时，将引发 <xref:System.StackOverflowException> 异常。  
  
## 相关提示  
 确保您没有无限循环或无限递归。  
 过多的方法调用通常意味着存在非常深的递归或无限递归。  
  
## 备注  
 您无法捕捉堆栈溢出异常，因为异常处理代码可能需要堆栈。 当普通应用程序中发生堆栈溢出时，公共语言运行时 \(CLR\) 会终止进程。  
  
 承载 CLR 的应用程序可以更改默认行为并指定 CLR 卸载发生异常的应用程序域，但允许进程继续进行。 有关更多信息，请参见[ICLRPolicyManager 接口](../Topic/ICLRPolicyManager%20Interface.md)。  
  
## 请参阅  
 <xref:System.StackOverflowException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [循环结构](/dotnet/visual-basic/programming-guide/language-features/control-flow/loop-structures)