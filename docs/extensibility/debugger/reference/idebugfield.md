---
title: "IDebugField |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugField
helpviewer_keywords: IDebugField interface
ms.assetid: adecdd1c-b1b9-4027-92da-74cbe910636f
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b13b14bcbc44bc74b044bcecb8aad99dff2d323a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="idebugfield"></a>IDebugField
此接口表示的字段，符号或类型的说明。  
  
## <a name="syntax"></a>语法  
  
```  
IDebugField : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>实施者注意事项  
 符号提供程序实现此接口为所有字段的基本类。  
  
## <a name="notes-for-callers"></a>调用方的说明  
 此接口是所有字段的基类。 基于的返回值[GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)，此接口可能会返回专用化程度的接口使用[QueryInterface](/cpp/atl/queryinterface)。 此外，许多接口返回`IDebugField`从各种方法的对象。  
  
## <a name="methods-in-vtable-order"></a>Vtable 顺序中的方法  
 下表显示的方法`IDebugField`。  
  
|方法|描述|  
|------------|-----------------|  
|[GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)|获取符号或类型的可显示信息。|  
|[GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)|获取的字段的类型。|  
|[GetType](../../../extensibility/debugger/reference/idebugfield-gettype.md)|获取字段的类型。|  
|[GetContainer](../../../extensibility/debugger/reference/idebugfield-getcontainer.md)|获取的字段的容器。|  
|[GetAddress](../../../extensibility/debugger/reference/idebugfield-getaddress.md)|获取的字段的地址。|  
|[GetSize](../../../extensibility/debugger/reference/idebugfield-getsize.md)|获取一个字段，以字节为单位的大小。|  
|[GetExtendedInfo](../../../extensibility/debugger/reference/idebugfield-getextendedinfo.md)|获取扩展有关的某个字段的信息。|  
|[等于](../../../extensibility/debugger/reference/idebugfield-equal.md)|比较两个字段。|  
|[GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)|获取有关符号或类型的独立于类型的信息。|  
  
## <a name="remarks"></a>备注  
 类型等效于 C 语言`typedef`。  
  
 在下面的 c + + 语言示例，`weather`是类类型，和`sunny`和`stormy`符号：  
  
```cpp  
class weather;  
weather sunny;  
weather stormy;  
```  
  
 字段表示符号，还是可以通过调用中确定类型[GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)并检查[FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md)结果。 如果`FIELD_KIND_TYPE`设置位，该字段是一种类型，并且如果`FIELD_KIND_SYMBOL`设置位，它是一个符号。  
  
## <a name="requirements"></a>要求  
 标头： sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 程序集： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另请参阅  
 [符号提供程序接口](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)