---
title: "IDebugBinder | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBinder"
helpviewer_keywords: 
  - "IDebugBinder 接口"
ms.assetid: d1f31e5b-c6e2-4e02-8959-b3e86041b29c
caps.latest.revision: 16
caps.handback.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugBinder
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  在 Visual Studio 2015 中，这种实现表达式计算器不推荐使用。 有关实现 CLR 表达式计算器的信息，请参阅 [CLR 表达式计算器](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 和 [托管表达式计算器示例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 此接口将绑定符号字段中，通常由符号提供程序，对于内存上下文或对象，其中包含符号的当前值返回。  
  
## 语法  
  
```  
IDebugBinder : IUnknown  
```  
  
## 实施者注意事项  
 此接口支持表达式求值，必须通过调试引擎 \(DE\) 实现。  
  
## 调用方的说明  
 此接口在表达式计算过程中使用，通常使用的实现中 [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) 和 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)。  
  
## Vtable 顺序中的方法  
 下表显示的方法 `IDebugBinder`。  
  
|方法|描述|  
|--------|--------|  
|[将绑定](../../../extensibility/debugger/reference/idebugbinder-bind.md)|获取内存上下文或对象，其中包含符号的当前值。|  
|[ResolveRuntimeType](../../../extensibility/debugger/reference/idebugbinder-resolveruntimetype.md)|确定一个对象的运行时类型。|  
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugbinder-getmemorycontext.md)|将对象的位置或内存地址转换为内存上下文。|  
|[GetFunctionObject](../Topic/IDebugBinder::GetFunctionObject.md)|获取 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) 用来创建函数的参数对象。|  
|[ResolveDynamicType](../../../extensibility/debugger/reference/idebugbinder-resolvedynamictype.md)|获取变量的确切类型。|  
  
## 备注  
 此接口返回的表达式计算器使用的对象的分析树。 表达式计算器分析表达式使用符号提供程序将在表达式中的符号转换为的实例 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md), ，用于描述依据其类型和位置在源代码中的每个符号。[将绑定](../../../extensibility/debugger/reference/idebugbinder-bind.md) 方法转换为 `IDebugField` 对象添加到 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 连接或绑定符号的对象类型转换为实际值在内存中。 这些 `IDebugObject` 对象随后存储在分析树，以供以后计算。  
  
## 要求  
 标头︰ ee.h  
  
 命名空间 ︰ Microsoft.VisualStudio.Debugger.Interop  
  
 程序集 ︰ Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [表达式计算接口](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)   
 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)   
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)