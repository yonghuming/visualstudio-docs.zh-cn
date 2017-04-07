---
title: "IDebugBinder3 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugBinder3
helpviewer_keywords:
- IDebugBinder3 interface
ms.assetid: 92353a74-dc74-4f93-8762-61d6b220478c
caps.latest.revision: 12
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
ms.openlocfilehash: 47df761681525fd0c1062ae3d84be61c388282e9
ms.lasthandoff: 04/05/2017

---
# <a name="idebugbinder3"></a>IDebugBinder3
> [!IMPORTANT]
>  在 Visual Studio 2015 中，已弃用这种方式实施表达式计算器。 有关实现 CLR 表达式计算器的信息，请参阅[CLR 表达式计算器](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)和[托管表达式计算器示例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 此接口提供对类型、 别名和自定义可视化工具服务的访问。  
  
## <a name="syntax"></a>语法  
  
```  
IDebugBinder3 : IDebugBinder  
```  
  
## <a name="notes-for-implementers"></a>实施者注意事项  
 调试引擎实现此接口以支持别名、 自定义可视化工具服务和对象类型信息的访问权限。  
  
## <a name="notes-for-callers"></a>调用方的说明  
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)接口获取通过使用此接口[QueryInterface](/cpp/atl/queryinterface)。  
  
## <a name="methods-in-vtable-order"></a>Vtable 顺序中的方法  
 除了提供的方法[IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)接口，此接口实现以下︰  
  
|方法|描述|  
|------------|-----------------|  
|[GetMemoryObject](../../../extensibility/debugger/reference/idebugbinder3-getmemoryobject.md)|检索表示此对象绑定到的内存的内存对象。|  
|[GetExceptionObjectAndType](../../../extensibility/debugger/reference/idebugbinder3-getexceptionobjectandtype.md)|检索此对象 （如果有），与关联的异常|  
|[FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md)|检索在给定其名称的别名|  
|[GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md)|检索此对象的所有别名的数组|  
|[GetTypeArgumentCount](../../../extensibility/debugger/reference/idebugbinder3-gettypeargumentcount.md)|获取与此对象关联的自变量类型的数目|  
|[GetTypeArguments](../../../extensibility/debugger/reference/idebugbinder3-gettypearguments.md)|检索与此对象关联的自变量类型的列表|  
|[GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md)|获取到可视化工具服务接口|  
|[GetMemoryContext64](../../../extensibility/debugger/reference/idebugbinder3-getmemorycontext64.md)|将对象位置或 64 位内存地址转换为内存上下文。|  
  
## <a name="requirements"></a>要求  
 标头︰ ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 程序集︰ Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另请参阅  
 [表达式评估接口](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
