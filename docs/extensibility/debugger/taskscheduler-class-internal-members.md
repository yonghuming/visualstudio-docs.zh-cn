---
title: "TaskScheduler 类-内部成员 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "TaskScheduler 类 [.NET Framework 的调试引擎]"
  - "调试引擎，TaskScheduler 类 [.NET Framework]"
ms.assetid: 87f1c969-0217-4464-8907-7609c1bf61d3
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# TaskScheduler 类-内部成员
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

本主题介绍的内部成员的 <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName> 类来帮助您实现自定义调试器。 有关此类的常规信息，请参阅 <xref:System.Threading.Tasks.TaskScheduler> 参考主题。  
  
 **命名空间︰** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **程序集︰** mscorlib （在 mscorlib.dll\)  
  
 由于无法在.NET Framework 中访问这些内部成员，下面的语法提供通用中间语言 \(CIL\)。  
  
## 语法  
  
```  
.class public abstract auto ansi beforefieldinit System.Threading.Tasks.TaskScheduler  
       extends System.Object  
```  
  
## 成员  
  
### 方法  
  
|名称|描述|  
|--------|--------|  
|[GetScheduledTasksForDebugger](../../extensibility/debugger/getscheduledtasksfordebugger-method.md)|检索所有计划任务的数组。|  
|[GetTaskSchedulersForDebugger](../../extensibility/debugger/gettaskschedulersfordebugger-method.md)|检索所有的数组 <xref:System.Threading.Tasks.TaskScheduler> 当前处于活动状态的对象。|  
  
## 备注  
  
## 请参阅  
 <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>   
 [适用于.NET Framework 并行扩展内幕](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)