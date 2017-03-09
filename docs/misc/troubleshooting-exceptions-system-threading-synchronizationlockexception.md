---
title: "关于异常的疑难解答：System.Threading.SynchronizationLockException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SynchronizationLockException 异常"
  - "System.Threading.SynchronizationLockException 异常"
ms.assetid: 82d80643-fc5c-40ae-a579-46869772d25c
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 关于异常的疑难解答：System.Threading.SynchronizationLockException
当要求调用方拥有给定 `Monitor` 的锁的方法被没有该锁的调用方调用时引发的异常。  
  
## 备注  
 引发 <xref:System.Threading.SynchronizationLockException>，方法是从未同步的代码块调用 <xref:System.Threading.Monitor.Exit%2A> 类的 <xref:System.Threading.Monitor.Pulse%2A>、<xref:System.Threading.Monitor.PulseAll%2A>、<xref:System.Threading.Monitor.Wait%2A> 和 `Monitor` 方法。  
  
## 请参阅  
 <xref:System.Threading.SynchronizationLockException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)