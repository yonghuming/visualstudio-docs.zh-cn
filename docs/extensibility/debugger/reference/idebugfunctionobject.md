---
title: "IDebugFunctionObject |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugFunctionObject
helpviewer_keywords: IDebugFunctionObject interface
ms.assetid: 8d94e97c-a9d1-400c-8a98-a44b5385b33a
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 69b0556712ddea8570b2a06fba09538649a06e9c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="idebugfunctionobject"></a>IDebugFunctionObject
> [!IMPORTANT]
>  在 Visual Studio 2015 中，已弃用这种方式实施表达式计算器。 有关实现 CLR 表达式计算器的信息，请参阅[CLR 表达式计算器](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)和[托管表达式计算器示例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 此接口表示一个函数。  
  
## <a name="syntax"></a>语法  
  
```  
IDebugFunctionObject : IDebugObject  
```  
  
## <a name="notes-for-implementers"></a>实施者注意事项  
 表达式计算器实现此接口来表示一个函数。  
  
## <a name="notes-for-callers"></a>调用方的说明  
 此接口是专用化[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)接口，并使用获取[QueryInterface](/cpp/atl/queryinterface)上`IDebugObject`接口。  
  
## <a name="methods-in-vtable-order"></a>Vtable 顺序中的方法  
 除了从继承的方法[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)、`IDebugFunctionObject`接口公开以下方法。  
  
|方法|描述|  
|------------|-----------------|  
|[CreatePrimitiveObject](../../../extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject.md)|创建一个基元数据对象。|  
|[CreateObject](../../../extensibility/debugger/reference/idebugfunctionobject-createobject.md)|创建使用构造函数的对象。|  
|[CreateObjectNoConstructor](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md)|使用没有构造函数创建的对象。|  
|[CreateArrayObject](../../../extensibility/debugger/reference/idebugfunctionobject-createarrayobject.md)|创建一个数组对象。|  
|[CreateStringObject](../../../extensibility/debugger/reference/idebugfunctionobject-createstringobject.md)|创建一个字符串对象。|  
|[评估](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md)|调用函数并返回一个对象作为生成的值。|  
  
## <a name="remarks"></a>备注  
 此接口允许表达式计算器才能表示分析树中的函数。 `Create`中此接口的方法用于构造对象表示对方法的输入的参数。 然后可以通过调用执行函数[评估](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md)方法，返回一个对象，该对象表示函数的返回值。  
  
## <a name="requirements"></a>要求  
 标头： ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 程序集： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另请参阅  
 [表达式评估接口](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)