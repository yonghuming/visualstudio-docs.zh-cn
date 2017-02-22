---
title: "DA0007：避免使用控制流异常 | Microsoft Docs"
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
  - "vs.performance.rules.DAExceptionsThrown"
  - "vs.performance.7"
  - "vs.performance.rules.DA0007"
  - "vs.performance.DA0007"
ms.assetid: ee8ba8b5-2313-46c9-b129-3f3a2a232898
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# DA0007：避免使用控制流异常
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|规则 ID|DA0007|  
|类别|.NET Framework 使用|  
|分析方法|全部|  
|消息|正在持续引发大量的异常。  请考虑在程序逻辑中减少对异常的使用。|  
|消息类型|警告|  
  
 在使用采样、.NET 内存或资源争用方法进行分析时，必须收集至少 25 个样本才能触发此规则。  
  
## 原因  
 分析数据中 .NET Framework 异常处理程序的调用率高。  请考虑使用其他控制流逻辑来减少引发的异常数。  
  
## 规则说明  
 虽然使用异常处理程序来中断程序执行的错误和其他事件是一个不错的办法，但作为常规程序执行逻辑一部分的异常处理程序的使用可能很昂贵，并且应当避免。  在大多数情况中，只应将异常用于很少出现并是预期之外的情况。  异常不应作为典型程序流程的一部分来返回值。  在很多的情况中，可以通过验证值和使用条件逻辑暂停导致问题的语句的执行以避免引发异常。  
  
 有关更多信息请参见MSDN 上**Microsoft Patterns and Practices**库中**Improving .NET Application Performance and Scalability** 卷内**Chapter 5 — Improving Managed Code Performance** 的 [托管异常](http://go.microsoft.com/fwlink/?LinkID=177825) 部分。  
  
## 如何调查警告  
 双击“错误列表”窗口中的该消息以导航到标记视图。  查找包含 **.NET CLR Exceptions\(@ProcessInstance\)\\\# of Exceps Thrown \/ sec** 度量的列。  确定程序执行过程中是否有一些特定阶段的异常处理多于其他处理。  使用采样分析，尝试识别产生频繁异常的 throw 语句和 try\/catch 块。  如有必要，向 catch 块添加逻辑以帮助您了解最频繁处理的是哪些异常。  如果可能，将经常执行的 throw 语句或 catch 块替换为简单的流控制逻辑或验证代码。  
  
 例如，如果发现应用程序频繁处理 DivideByZeroException 异常，则向您的程序添加逻辑以检查具有零值的分母将提高应用程序的性能。