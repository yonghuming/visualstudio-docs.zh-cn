---
title: "AsyncTaskMethodBuilder 结构-内部成员 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "调试引擎，AsyncTaskMethodBuilder 结构 [.NET Framework]"
  - "AsyncTaskMethodBuilder 结构 [.NET Framework 的调试引擎]"
ms.assetid: f32f5857-7ef8-45fd-8b5a-7f644eb98b11
caps.latest.revision: 5
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 5
---
# AsyncTaskMethodBuilder 结构-内部成员
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

本主题介绍的内部成员的 <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> 类。 有关此类的常规信息，请参阅 <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> 参考主题。  
  
 **命名空间:** <xref:System.Runtime.CompilerServices?displayProperty=fullName>  
  
 **程序集:** mscorlib \(在 mscorlib.dll\)  
  
 由于无法在.NET Framework 中访问这些内部成员，下面的语法提供通用中间语言 \(CIL\)。  
  
## 语法  
  
```  
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncTaskMethodBuilder  
       extends System.ValueType  
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder  
```  
  
## 内部成员  
  
|名称|描述|  
|--------|--------|  
|[ObjectIdForDebugger 属性](../../extensibility/debugger/asynctaskmethodbuilder-objectidfordebugger-property.md)|获取可用于唯一地标识调试器到此生成器的对象。|  
|[m\_builder 字段](../../extensibility/debugger/asynctaskmethodbuilder-m-builder-field.md)|表示此非泛型实例委托的泛型生成器对象。|  
  
## 请参阅  
 <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder>   
 [适用于.NET Framework 并行扩展内幕](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)