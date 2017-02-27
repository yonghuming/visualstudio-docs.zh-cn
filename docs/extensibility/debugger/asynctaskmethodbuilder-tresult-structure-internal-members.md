---
title: "AsyncTaskMethodBuilder &lt; TResult &gt; 结构-内部成员 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "AsyncTaskMethodBuilder < TResult > 结构 [.NET Framework 的调试引擎]"
  - "调试引擎，AsyncTaskMethodBuilder < TResult > 结构 [.NET Framework]"
ms.assetid: 17ebc340-8170-4aff-bf54-dc4548c83632
caps.latest.revision: 4
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 4
---
# AsyncTaskMethodBuilder &lt; TResult &gt; 结构-内部成员
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

本主题介绍的内部成员的 <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> 类。 有关此类的常规信息，请参阅 <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> 参考主题。  
  
 **命名空间:** <xref:System.Runtime.CompilerServices?displayProperty=fullName>  
  
 **程序集:** mscorlib \(在 mscorlib.dll\)  
  
 由于无法在.NET Framework 中访问这些内部成员，下面的语法提供通用中间语言 \(CIL\)。  
  
## 语法  
  
```  
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncTaskMethodBuilder`1<TResult>  
       extends System.ValueType  
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder  
```  
  
## 内部成员  
  
|名称|描述|  
|--------|--------|  
|[ObjectIdForDebugger 属性](../../extensibility/debugger/asynctaskmethodbuilder-tresult-objectidfordebugger-property.md)|获取可用于唯一地标识调试器到此生成器的对象。|  
|[m\_task 字段](../../extensibility/debugger/asynctaskmethodbuilder-tresult-m-task-field.md)|表示延迟初始化的生成任务。|  
  
## 请参阅  
 <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601>   
 [适用于.NET Framework 并行扩展内幕](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)