---
title: "AsyncVoidMethodBuilder 结构-内部成员 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "调试引擎，AsyncVoidMethodBuilder 结构 [.NET Framework]"
  - "AsyncVoidMethodBuilder 结构 [.NET Framework 的调试引擎]"
ms.assetid: fe2970ab-d4c5-4355-a8e4-772ee0a57178
caps.latest.revision: 4
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 4
---
# AsyncVoidMethodBuilder 结构-内部成员
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

本主题介绍的内部成员的 <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder> 类。 有关此类的常规信息，请参阅 <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder> 参考主题。  
  
 **命名空间:** <xref:System.Runtime.CompilerServices?displayProperty=fullName>  
  
 **程序集:** mscorlib \(在 mscorlib.dll\)  
  
 由于无法在.NET Framework 中访问这些内部成员，下面的语法提供通用中间语言 \(CIL\)。  
  
## 语法  
  
```  
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncVoidMethodBuilder  
       extends System.ValueType  
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder  
```  
  
## 内部成员  
  
|名称|描述|  
|--------|--------|  
|[ObjectIdForDebugger 属性](../../extensibility/debugger/asyncvoidmethodbuilder-objectidfordebugger-property.md)|获取可用于唯一地标识调试器到此生成器的对象。|  
|[m\_objectIdForDebugger 字段](../../extensibility/debugger/asyncvoidmethodbuilder-m-objectidfordebugger-field.md)|表示调试器用于唯一标识此生成器的延迟初始化的对象。|  
  
## 请参阅  
 <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder>   
 [适用于.NET Framework 并行扩展内幕](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)