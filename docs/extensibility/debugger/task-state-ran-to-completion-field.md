---
title: "TASK_STATE_RAN_TO_COMPLETION 字段 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "TASK_STATE_RAN_TO_COMPLETION 字段中，任务类 [.NET Framework 的调试引擎]"
ms.assetid: 0f4830af-fe0c-4141-b768-817f4e426b8c
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# TASK_STATE_RAN_TO_COMPLETION 字段
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

已成功完成执行的任务。  
  
 **命名空间︰** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **程序集︰** mscorlib （在 mscorlib.dll\)  
  
 由于无法在.NET Framework 中访问此内部成员，下面的语法提供通用中间语言 \(CIL\)。  
  
## 语法  
  
```  
.field static assembly literal int32 TASK_STATE_RAN_TO_COMPLETION = int32(0x02000000)  
```  
  
## 备注  
 如果 [m\_stateFlags](../../extensibility/debugger/m-stateflags-field.md) 字段包含此值， <xref:System.Threading.Tasks.Task.Status%2A> 属性将返回 <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName>。  
  
## 请参阅  
 [Task 类](../../extensibility/debugger/task-class-internal-members.md)