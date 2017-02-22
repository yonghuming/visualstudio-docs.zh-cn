---
title: "GetScheduledTasksForDebugger 方法 | Microsoft Docs"
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
  - "GetScheduledTasksForDebugger 方法，TaskScheduler 类 [.NET Framework 的调试引擎]"
ms.assetid: 7c9b4cde-6e4a-4cef-929f-7d02b1da5762
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# GetScheduledTasksForDebugger 方法
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

检索所有计划任务的数组。  
  
 **命名空间︰** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **程序集︰** mscorlib （在 mscorlib.dll\)  
  
 由于无法在.NET Framework 中访问此内部成员，下面的语法提供通用中间语言 \(CIL\)。  
  
## 语法  
  
```  
.method assembly hidebysig instance class System.Threading.Tasks.Task[] GetScheduledTasksForDebugger() cil managed  
```  
  
## 返回值  
 所有计划任务的数组。 每个任务执行或已完成执行。  
  
## 备注  
 此方法不是线程安全，不应与其他实例同时使用 <xref:System.Threading.Tasks.TaskScheduler> 它时，应调用从调试器仅调试器已挂起所有其他线程。  
  
## 请参阅  
 [TaskScheduler 类](../../extensibility/debugger/taskscheduler-class-internal-members.md)