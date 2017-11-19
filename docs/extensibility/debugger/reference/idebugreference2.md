---
title: "IDebugReference2 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugReference2
helpviewer_keywords: IDebugReference2 interface
ms.assetid: 3cfed312-f532-4bce-84a5-1677c14567d7
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 27e880dbf5b602c1bd0b98c6ce5ccc2fdf88e37a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="idebugreference2"></a>IDebugReference2
此接口表示一个堆栈帧属性或某些其他属性的引用。  
  
> [!NOTE]
>  `IDebugReference2`留待将来使用，以及所有其方法应返回`E_NOTIMPL`。  
  
## <a name="syntax"></a>语法  
  
```  
IDebugReference2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>实施者注意事项  
 DE 实现此接口可表示对特定类型的值的引用。 例如，此值可以是一个数字值作为表达式计算，用于显示内存或寄存器及其值的列表的内存上下文结果。  
  
## <a name="notes-for-callers"></a>调用方的说明  
 调用[GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md)获取此接口。 [GetParent](../../../extensibility/debugger/reference/idebugreference2-getparent.md)和[GetDerivedMostReference](../../../extensibility/debugger/reference/idebugreference2-getderivedmostreference.md)还返回此接口。  
  
## <a name="methods-in-vtable-order"></a>Vtable 顺序中的方法  
 下表显示的方法`IDebugReference2`。  
  
|方法|描述|  
|------------|-----------------|  
|[GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)|获取[DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)描述此引用的结构。|  
|[SetValueAsString](../../../extensibility/debugger/reference/idebugreference2-setvalueasstring.md)|设置此引用从字符串的值。|  
|[SetValueAsReference](../../../extensibility/debugger/reference/idebugreference2-setvalueasreference.md)|设置从另一个引用此引用的值。|  
|[EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)|枚举的子级的此引用。|  
|[GetParent](../../../extensibility/debugger/reference/idebugreference2-getparent.md)|获取此引用的父级。|  
|[GetDerivedMostReference](../../../extensibility/debugger/reference/idebugreference2-getderivedmostreference.md)|获取此引用派生程度最高的引用。|  
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md)|获取此引用所引用的内存字节。|  
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md)|获取此引用内存上下文。|  
|[GetSize](../../../extensibility/debugger/reference/idebugreference2-getsize.md)|获取大小，以字节为单位，此引用。|  
|[SetReferenceType](../../../extensibility/debugger/reference/idebugreference2-setreferencetype.md)|设置此引用类型。|  
|[Compare](../../../extensibility/debugger/reference/idebugreference2-compare.md)|比较此引用与另一个。|  
  
## <a name="remarks"></a>备注  
  
> [!NOTE]
>  "Property"的这种用法不应混淆与该这意味着类的成员变量尽管`IDebugReference2`可以表示这样的实体。  
  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)表示的属性，而`IDebugReference2`表示属性，通常对正在调试的程序中的某个对象的引用的引用。  
  
 属性和对作为引用之间的主要区别在于而引用是指未命名的实例，将属性指一个对象，对象的命名实例。 例如，属性可能引用的程序的堆中对象`"a.b"`。 与相同的对象可能引用另一个属性`"c.d"`。 引用此属性的方法需要`"a.b"`或`"c.d"`处于范围之内。 对此相同的对象的引用是无名称;可以为引用的对象，前提是该对象的内存有效。  
  
 `IDebugProperty2`接口可以认为是为具有名称、 类型和地址的值。 `IDebugReference2`、 一端另一方面，可以被想象成类型和地址。  
  
## <a name="requirements"></a>要求  
 标头： msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 程序集： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另请参阅  
 [核心接口](../../../extensibility/debugger/reference/core-interfaces.md)   
 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md)