---
title: "TASK_STATE_FAULTED 字段 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "TASK_STATE_FAULTED 字段中，任务类 [.NET Framework 的调试引擎]"
ms.assetid: ced826ae-09a9-4acf-af00-a2343d396bb8
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# TASK_STATE_FAULTED 字段
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

由于未处理异常的原因而完成的任务。  
  
 **命名空间︰** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **程序集︰** mscorlib （在 mscorlib.dll\)  
  
 由于无法在.NET Framework 中访问此内部成员，下面的语法提供通用中间语言 \(CIL\)。  
  
## 语法  
  
```  
.field static assembly literal int32 TASK_STATE_FAULTED = int32(0x00400000)  
```  
  
## 备注  
 如果 [m\_stateFlags](../../extensibility/debugger/m-stateflags-field.md) 字段包含此值， <xref:System.Threading.Tasks.Task.Status%2A> 属性将返回 <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName>。  
  
## 请参阅  
 [Task 类](../../extensibility/debugger/task-class-internal-members.md)