---
title: "m_stateObject 字段 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "m_stateObject 字段中，任务类 [.NET Framework 的调试引擎]"
ms.assetid: 68c54b22-3e1c-4031-b9c7-b972c519d8a0
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# m_stateObject 字段
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

一个表示操作将使用的数据的对象。  
  
 **命名空间︰** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **程序集︰** mscorlib （在 mscorlib.dll\)  
  
 由于无法在.NET Framework 中访问此内部成员，下面的语法提供通用中间语言 \(CIL\)。  
  
## 语法  
  
```  
.field assembly object m_stateObject  
```  
  
## 备注  
 这是 `state` 中的参数 <xref:System.Threading.Tasks.Task.%23ctor%2A> 构造函数。 有关的后备字段也是 <xref:System.Threading.Tasks.Task.AsyncState%2A?displayProperty=fullName> 属性。  
  
## 请参阅  
 [Task 类](../../extensibility/debugger/task-class-internal-members.md)