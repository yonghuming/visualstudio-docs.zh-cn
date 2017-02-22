---
title: "SetNotificationForWaitCompletion 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SetNotificationForWaitCompletion 方法中，任务类 [.NET Framework 的调试引擎]"
ms.assetid: da149c9a-20f4-4543-a29e-429c8c1d2e19
caps.latest.revision: 5
caps.handback.revision: 5
ms.author: "gregvanl"
manager: "ghogen"
---
# SetNotificationForWaitCompletion 方法
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

设置或清除 TASK\_STATE\_WAIT\_COMPLETION\_NOTIFICATION 状态位。  
  
 **命名空间:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **程序集:** mscorlib \(在 mscorlib.dll\)  
  
## 语法  
  
```vb  
internal void SetNotificationForWaitCompletion(bool enabled)  
```  
  
#### 参数  
 `enabled`  
  
 `true` 若要设置的位; `false` 到未设置该位。  
  
## 异常  
  
## 备注  
 调试器将设置此位，以帮助单步 async 方法主体外部。 如果 `enabled` 是 `true`, ，必须调用此方法仅在尚未完成的任务上。 如果 `enabled` 是 `false`, ，可能会对已完成的任务调用此方法。 在既情况下，它应仅用于承诺样式任务。  
  
## 要求  
  
## 请参阅  
 [Task 类](../../extensibility/debugger/task-class-internal-members.md)