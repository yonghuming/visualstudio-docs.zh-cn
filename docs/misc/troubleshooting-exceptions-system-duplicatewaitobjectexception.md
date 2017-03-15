---
title: "关于异常的疑难解答：System.DuplicateWaitObjectException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
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
  - "DuplicateWaitObjectException 类"
ms.assetid: b9ff6932-a7cf-4a89-bd7d-e4ef1a3ff353
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 关于异常的疑难解答：System.DuplicateWaitObjectException
如果传递给 <xref:System.DuplicateWaitObjectException> 或 <xref:System.Threading.WaitHandle> 的 <xref:System.Threading.WaitHandle.WaitAll%2A> 对象的数组包含任何重复的操作系统句柄，则会引发 <xref:System.Threading.WaitHandle.WaitAny%2A> 异常。  
  
## 相关提示  
 **确保传递至 WaitAll 或 WaitAny 的 WaitHandle 对象是唯一的。**  
 <xref:System.Threading.WaitHandle> 数组不能包含对同一对象的多个引用。  
  
### 备注  
 公共语言运行时 \(CLR\) 提供了一种基于 <xref:System.Threading.WaitHandle> 对象的数组中等待执行的同步对象的线程同步机制。  
  
## 请参阅  
 <xref:System.DuplicateWaitObjectException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)