---
title: "m_stateFlags 字段 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "m_stateFlags 字段中，任务类 [.NET Framework 的调试引擎]"
ms.assetid: 82b20efc-08f2-4cd2-91f6-4e01e3da906b
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# m_stateFlags 字段
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

存储的当前状态有关的信息 <xref:System.Threading.Tasks.Task> 对象。  
  
 **命名空间︰** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **程序集︰** mscorlib （在 mscorlib.dll\)  
  
 由于无法在.NET Framework 中访问此内部成员，下面的语法提供通用中间语言 \(CIL\)。  
  
## 语法  
  
```  
.field assembly int32 modreq(System.Runtime.CompilerServices.IsVolatile) m_stateFlags  
```  
  
## 备注  
 通常使用 <xref:System.Threading.Tasks.Task.Status%2A?displayProperty=fullName> 属性来访问此值。  
  
 此成员可以是下列值中的任意组合︰  
  
-   [TASK\_STATE\_EXECUTED](../../extensibility/debugger/task-state-executed-field.md)  
  
-   [TASK\_STATE\_FAULTED](../../extensibility/debugger/task-state-faulted-field.md)  
  
-   [TASK\_STATE\_CANCELED](../../extensibility/debugger/task-state-canceled-field.md)  
  
-   [TASK\_STATE\_WAITING\_ON\_CHILDREN](../../extensibility/debugger/task-state-waiting-on-children-field.md)  
  
-   [TASK\_STATE\_RAN\_TO\_COMPLETION](../../extensibility/debugger/task-state-ran-to-completion-field.md)  
  
## 请参阅  
 [Task 类](../../extensibility/debugger/task-class-internal-members.md)