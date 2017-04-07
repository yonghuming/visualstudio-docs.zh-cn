---
title: "IDebugObject2 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugObject2
helpviewer_keywords:
- IDebugObject2 interface
ms.assetid: ef640967-8adb-4793-994d-ae1736510891
caps.latest.revision: 15
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
ms.openlocfilehash: dd3a3bed1e6994ff3c5fd32ded40a61929f4ca19
ms.lasthandoff: 04/05/2017

---
# <a name="idebugobject2"></a>IDebugObject2
> [!IMPORTANT]
>  在 Visual Studio 2015 中，已弃用这种方式实施表达式计算器。 有关实现 CLR 表达式计算器的信息，请参阅[CLR 表达式计算器](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)和[托管表达式计算器示例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 此接口提供的对象有关的其他信息。  
  
## <a name="syntax"></a>语法  
  
```  
IDebugObject2 : IDebugObject  
```  
  
## <a name="notes-for-implementers"></a>实施者注意事项  
 表达式计算器实现此接口可提供对别名和有关对象的信息的访问权限支持。  
  
## <a name="notes-for-callers"></a>调用方的说明  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)接口可以通过使用来获取此接口[QueryInterface](/cpp/atl/queryinterface)。 此外， [GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md)返回此接口。  
  
## <a name="methods-in-vtable-order"></a>Vtable 顺序中的方法  
 除了上的方法[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)接口，`IDebugObject2`接口实现以下︰  
  
|方法|描述|  
|------------|-----------------|  
|[GetBackingFieldForProperty](../../../extensibility/debugger/reference/idebugobject2-getbackingfieldforproperty.md)|获取的字段或变量 （如果有），可能支持此对象表示的属性。|  
|[GetICorDebugValue](../../../extensibility/debugger/reference/idebugobject2-geticordebugvalue.md)|获取表示此对象的值的托管的代码对象。|  
|[CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md)|创建此对象的唯一 ID 或返回现有别名。|  
|[GetAlias](../../../extensibility/debugger/reference/idebugobject2-getalias.md)|如果有的话，请获取与此对象关联的别名。|  
|[GetField](../../../extensibility/debugger/reference/idebugobject2-getfield.md)|获取此对象的类型。|  
|[IsUserData](../../../extensibility/debugger/reference/idebugobject2-isuserdata.md)|确定此对象是否表示用户数据。|  
|[IsEncOutdated](../../../extensibility/debugger/reference/idebugobject2-isencoutdated.md)|确定是否的编辑并继续状态将不再有效。<br /><br /> 自定义表达式计算器不实现此方法 (它应始终返回`E_NOTIMPL`)。|  
  
## <a name="remarks"></a>备注  
 请参阅[IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)有关别名的讨论。  
  
## <a name="requirements"></a>要求  
 标头︰ ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 程序集︰ Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另请参阅  
 [表达式评估接口](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)   
 [GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md)
