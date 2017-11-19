---
title: "IDebugBinder |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugBinder
helpviewer_keywords: IDebugBinder interface
ms.assetid: d1f31e5b-c6e2-4e02-8959-b3e86041b29c
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 614133a72e05f8bd412216d466bbfc90a197ff07
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="idebugbinder"></a>IDebugBinder
> [!IMPORTANT]
>  在 Visual Studio 2015 中，已弃用这种方式实施表达式计算器。 有关实现 CLR 表达式计算器的信息，请参阅[CLR 表达式计算器](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)和[托管表达式计算器示例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 此接口将绑定符号提供程序，到内存上下文或包含符号的当前值的对象通常返回的符号字段。  
  
## <a name="syntax"></a>语法  
  
```  
IDebugBinder : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>实施者注意事项  
 此接口支持表达式计算，必须实现的调试引擎 (DE)。  
  
## <a name="notes-for-callers"></a>调用方的说明  
 此接口用于表达式计算的过程中，通常使用的实现中[EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)和[EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)。  
  
## <a name="methods-in-vtable-order"></a>Vtable 顺序中的方法  
 下表显示的方法`IDebugBinder`。  
  
|方法|描述|  
|------------|-----------------|  
|[绑定](../../../extensibility/debugger/reference/idebugbinder-bind.md)|获取内存上下文或对象，其中包含符号的当前值。|  
|[ResolveRuntimeType](../../../extensibility/debugger/reference/idebugbinder-resolveruntimetype.md)|确定对象的运行时类型。|  
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugbinder-getmemorycontext.md)|将对象位置或内存地址转换为内存上下文。|  
|[GetFunctionObject](../../../extensibility/debugger/reference/idebugbinder-getfunctionobject.md)|获取[IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)用于创建函数参数的对象。|  
|[ResolveDynamicType](../../../extensibility/debugger/reference/idebugbinder-resolvedynamictype.md)|获取变量的确切类型。|  
  
## <a name="remarks"></a>备注  
 此接口返回对象使用的表达式计算器分析树。 表达式计算器分析表达式使用符号提供程序将在表达式中的符号转换为的实例[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)，用于描述根据其类型和位置的源代码中的每个符号。 [绑定](../../../extensibility/debugger/reference/idebugbinder-bind.md)方法将`IDebugField`对象添加到[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)连接或绑定符号的对象类型转换为内存中的实际值。 这些`IDebugObject`对象然后存储在以供以后计算分析树。  
  
## <a name="requirements"></a>要求  
 标头： ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 程序集： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另请参阅  
 [表达式评估接口](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)   
 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)   
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)