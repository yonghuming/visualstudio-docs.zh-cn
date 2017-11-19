---
title: "IDebugProperty2 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProperty2
helpviewer_keywords: IDebugProperty2 interface
ms.assetid: a7d5c70f-a1a5-4120-9f70-184e01c25bff
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 45ad3a6c0d250136d0ab3e1becb088ea140b42e8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="idebugproperty2"></a>IDebugProperty2
此接口表示一个堆栈帧属性、 程序文档属性或某些其他属性。 属性通常是表达式计算的结果。  
  
> [!NOTE]
>  "Property"的这种用法不应混淆与该这意味着类的成员变量尽管`IDebugProperty2`可以表示这样的实体。  
  
## <a name="syntax"></a>语法  
  
```  
IDebugProperty2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>实施者注意事项  
 DE 实现此接口来表示特定类型的值。 例如，此值可以是一个数字值作为表达式计算，用于显示内存或寄存器及其值的列表的内存上下文结果。  
  
## <a name="notes-for-callers"></a>调用方的说明  
 调用[EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)或[EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)以获取此接口，它表示计算的结果。 `IDebugExpression2::EvaluateAsync`返回此接口通过发送[IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) SDM，后者反过来调用接口[GetResult](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md)要检索其属性。  
  
 [GetDebugProperty](../../../extensibility/debugger/reference/idebugpropertycreateevent2-getdebugproperty.md)返回此接口可提供关联的脚本文档。  
  
 [GetReturnValue](../../../extensibility/debugger/reference/idebugreturnvalueevent2-getreturnvalue.md)返回此接口来表示函数的返回值。  
  
 [GetDebugProperty](../../../extensibility/debugger/reference/idebugprogram2-getdebugproperty.md)返回此接口来表示例如名称或内存上下文的程序的各种属性。  
  
 [GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md)返回此接口来表示如本地变量的堆栈帧的各种属性。  
  
## <a name="methods-in-vtable-order"></a>Vtable 顺序中的方法  
 下表显示的方法`IDebugProperty2`。  
  
|方法|描述|  
|------------|-----------------|  
|[GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)|在填充[DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)描述的属性的结构。|  
|[SetValueAsString](../../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md)|从字符串中设置的属性的值。|  
|[SetValueAsReference](../../../extensibility/debugger/reference/idebugproperty2-setvalueasreference.md)|从给定的引用的值设置的属性的值。|  
|[EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)|枚举的子级的属性。|  
|[GetParent](../../../extensibility/debugger/reference/idebugproperty2-getparent.md)|返回属性的父级。|  
|[GetDerivedMostProperty](../../../extensibility/debugger/reference/idebugproperty2-getderivedmostproperty.md)|返回描述的属性的派生程度最高属性的属性。|  
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md)|返回的内存字节数构成的属性的值。|  
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md)|返回属性值的内存上下文。|  
|[GetSize](../../../extensibility/debugger/reference/idebugproperty2-getsize.md)|返回的大小，以字节为单位的属性值。|  
|[GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md)|返回对该属性的值的引用。|  
|[GetExtendedInfo](../../../extensibility/debugger/reference/idebugproperty2-getextendedinfo.md)|返回一个属性的扩展的信息。|  
  
## <a name="remarks"></a>备注  
 属性，由表示`IDebugProperty2`接口，可视为具有名称、 类型和地址的值。 在更多常规术语中，`IDebugProperty2`可以表示任何内容已具有父项和子节点的分层结构。  
  
 属性是通常是暂时的例如只相当于当前的堆栈帧，持续。 另一方面的参考，由表示[IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)接口，持续的时间，只要值保留在内存中。  
  
 可以使用 IDE`IDebugProperty2`接口，以使用户可以浏览和修改在运行时属性。  
  
## <a name="requirements"></a>要求  
 标头： msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 程序集： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另请参阅  
 [核心接口](../../../extensibility/debugger/reference/core-interfaces.md)   
 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)