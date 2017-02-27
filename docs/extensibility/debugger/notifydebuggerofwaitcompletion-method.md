---
title: "NotifyDebuggerOfWaitCompletion 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "NotifyDebuggerOfWaitCompletion 方法中，任务类 [.NET Framework 的调试引擎]"
ms.assetid: 841c5908-4f3f-400b-a7b0-96a95f362817
caps.latest.revision: 5
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 5
---
# NotifyDebuggerOfWaitCompletion 方法
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

调试程序所使用的断点目标的占位符方法。 此方法不得内联或已优化。  
  
 **命名空间:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **程序集:** mscorlib \(在 mscorlib.dll\)  
  
## 语法  
  
```vb  
private void NotifyDebuggerOfWaitCompletion()  
```  
  
## 备注  
 与任务的所有联接操作应都调用此方法，如果其调试器通知位被设置。  
  
## 要求  
  
## 请参阅  
 [Task 类](../../extensibility/debugger/task-class-internal-members.md)