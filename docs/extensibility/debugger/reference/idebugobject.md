---
title: "IDebugObject |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugObject
helpviewer_keywords:
- IDebugObject interface
ms.assetid: 05cd8bf4-c9ee-4b49-b782-2263c33067d6
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: ca7c86466fa23fb21a932f26dc24e37c71cf29b4
ms.openlocfilehash: 4707784dcccfa85f0edee277bc40ed19013509b5
ms.lasthandoff: 04/05/2017

---
# <a name="idebugobject"></a>IDebugObject
> [!IMPORTANT]
>  在 Visual Studio 2015 中，已弃用这种方式实施表达式计算器。 有关实现 CLR 表达式计算器的信息，请参阅[CLR 表达式计算器](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)和[托管表达式计算器示例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 此接口表示联编程序创建封装符号和表达式的值的对象。  
  
## <a name="syntax"></a>语法  
  
```  
IDebugObject : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>实施者注意事项  
 表达式计算器实现此接口可表示的对象。  
  
## <a name="notes-for-callers"></a>调用方的说明  
 此接口是表达式计算器分析表达式中使用的所有对象的基类。 返回通过调用[绑定](../../../extensibility/debugger/reference/idebugbinder-bind.md)方法。 [QueryInterface](/cpp/atl/queryinterface)此接口中获取的专用化程度的接口。  
  
## <a name="methods-in-vtable-order"></a>Vtable 顺序中的方法  
 下表显示的方法`IDebugObject`。  
  
|方法|说明|  
|------------|-----------------|  
|[GetSize](../../../extensibility/debugger/reference/idebugobject-getsize.md)|获取对象的大小。|  
|[GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)|作为一系列连续字节中获取对象的值。|  
|[SetValue](../../../extensibility/debugger/reference/idebugobject-setvalue.md)|设置对象的值从一系列连续的字节。|  
|[SetReferenceValue](../../../extensibility/debugger/reference/idebugobject-setreferencevalue.md)|设置此对象的引用值。|  
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugobject-getmemorycontext.md)|获取表示对象的值的地址的内存上下文。|  
|[GetManagedDebugObject](../../../extensibility/debugger/reference/idebugobject-getmanageddebugobject.md)|创建的调试引擎的地址空间中的托管对象的副本。|  
|[IsNullReference](../../../extensibility/debugger/reference/idebugobject-isnullreference.md)|测试此对象是否为空引用。|  
|[IsEqual](../../../extensibility/debugger/reference/idebugobject-isequal.md)|将此对象进行比较。|  
|[IsReadOnly](../../../extensibility/debugger/reference/idebugobject-isreadonly.md)|确定此对象是否为只读的。|  
|[IsProxy](../../../extensibility/debugger/reference/idebugobject-isproxy.md)|确定对象是否为透明的代理。|  
  
## <a name="remarks"></a>备注  
 表达式计算器使用的基类为此接口来表示分析树中的对象。  
  
## <a name="requirements"></a>要求  
 标头︰ ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 程序集︰ Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另请参阅  
 [表达式评估接口](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md)   
 [绑定](../../../extensibility/debugger/reference/idebugbinder-bind.md)
