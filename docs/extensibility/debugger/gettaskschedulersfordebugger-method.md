---
title: "GetTaskSchedulersForDebugger 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "GetTaskSchedulersForDebugger 方法，TaskScheduler 类 [.NET Framework 的调试引擎]"
ms.assetid: 58aa236a-5ab8-4695-b303-89dffdbcd946
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# GetTaskSchedulersForDebugger 方法
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

检索所有的数组 <xref:System.Threading.Tasks.TaskScheduler> 当前处于活动状态的对象。  
  
 **命名空间︰** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **程序集︰** mscorlib （在 mscorlib.dll\)  
  
 由于无法在.NET Framework 中访问此内部成员，下面的语法提供通用中间语言 \(CIL\)。  
  
## 语法  
  
```  
.method assembly hidebysig static class System.Threading.Tasks.TaskScheduler[] GetTaskSchedulersForDebugger() cil managed  
```  
  
## 返回值  
 所有的数组 <xref:System.Threading.Tasks.TaskScheduler> 中当前处于活动状态的对象 <xref:System.AppDomain>。  
  
## 备注  
 此方法不是线程安全，不应与其他实例同时使用 <xref:System.Threading.Tasks.TaskScheduler>。 它应调用从调试器仅在调试器已挂起所有其他线程时。  
  
## 请参阅  
 [TaskScheduler 类](../../extensibility/debugger/taskscheduler-class-internal-members.md)