---
title: "IDebugField |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugField
helpviewer_keywords:
- IDebugField interface
ms.assetid: adecdd1c-b1b9-4027-92da-74cbe910636f
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: e272f7b5e314e09d111ca3996870f5131ebdc3d0
ms.lasthandoff: 02/22/2017

---
# <a name="idebugfield"></a>IDebugField
此接口表示的字段，符号或类型的说明。  
  
## <a name="syntax"></a>语法  
  
```  
IDebugField : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>实施者注意事项  
 符号提供程序实现此接口作为基类的所有字段。  
  
## <a name="notes-for-callers"></a>调用方的说明  
 此接口是所有字段的类的基类。 基于的返回值[GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)，此接口可能会返回更多专用的接口，通过使用[QueryInterface](/visual-cpp/atl/queryinterface)。 此外，许多接口返回`IDebugField`来自各种方法的对象。  
  
## <a name="methods-in-vtable-order"></a>Vtable 顺序中的方法  
 下表显示的方法`IDebugField`。  
  
|方法|说明|  
|------------|-----------------|  
|[GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)|获取有关符号或类型可显示信息。|  
|[GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)|获取字段的类型。|  
|[GetType](../../../extensibility/debugger/reference/idebugfield-gettype.md)|获取字段的类型。|  
|[GetContainer](../../../extensibility/debugger/reference/idebugfield-getcontainer.md)|获取字段的容器。|  
|[GetAddress](../../../extensibility/debugger/reference/idebugfield-getaddress.md)|获取字段的地址。|  
|[GetSize](../../../extensibility/debugger/reference/idebugfield-getsize.md)|获取字段中，以字节为单位的大小。|  
|[GetExtendedInfo](../../../extensibility/debugger/reference/idebugfield-getextendedinfo.md)|获取扩展字段的信息。|  
|[等于](../../../extensibility/debugger/reference/idebugfield-equal.md)|比较两个域。|  
|[GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)|获取有关符号或类型独立于类型的信息。|  
  
## <a name="remarks"></a>备注  
 类型等效于 C 语言`typedef`。  
  
 在下面的 c + + 语言示例，`weather`是类类型，和`sunny`和`stormy`符号︰  
  
```cpp#  
class weather;  
weather sunny;  
weather stormy;  
```  
  
 字段表示符号，还是可以通过调用确定类型[GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)和检查[FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md)结果。 如果`FIELD_KIND_TYPE`设置位，该字段是类型，并且如果`FIELD_KIND_SYMBOL`设置位，它是一种符号。  
  
## <a name="requirements"></a>要求  
 标头︰ sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 程序集︰ Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另请参阅  
 [符号提供程序接口](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
