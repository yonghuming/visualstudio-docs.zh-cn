---
title: "IDebugMemoryBytes2 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugMemoryBytes2
helpviewer_keywords:
- IDebugMemoryBytes2 interface
ms.assetid: d7647575-0e06-4190-88f5-ca40b82209a4
caps.latest.revision: 11
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
ms.openlocfilehash: b0cb505562dd383748887a281bde619a0e790ddd
ms.lasthandoff: 02/22/2017

---
# <a name="idebugmemorybytes2"></a>IDebugMemoryBytes2
此接口表示内存字节的数。  
  
## <a name="syntax"></a>语法  
  
```  
IDebugMemoryBytes2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>实施者注意事项  
 调试引擎 (DE) 实现此接口来表示内存中的字节。  
  
## <a name="notes-for-callers"></a>调用方的说明  
 [GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md)返回此接口，以提供对系统内存的访问。 [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md)和[GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md)返回此接口，以提供对对象的字节的访问。  
  
## <a name="methods-in-vtable-order"></a>Vtable 顺序中的方法  
 下表显示的方法`IDebugMemoryBytes2`。  
  
|方法|描述|  
|------------|-----------------|  
|[ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md)|读取在给定位置开始的字节序列。|  
|[WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md)|写入`dwCount`开始的字节`pStartContext`。|  
|[GetSize](../../../extensibility/debugger/reference/idebugmemorybytes2-getsize.md)|获取的大小，以字节为单位表示通过此接口的内存。|  
  
## <a name="remarks"></a>备注  
 对于属性， [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)接口表示一个数组提供`IDebugMemoryBytes2`接口来访问该数组中的值。  
  
 Visual Studio 的**内存视图**调用[GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md)检索`IDebugMemoryBytes2`用于访问系统内存接口。 获取该地址来访问方法分析表达式作为地址输入到内存视图然后计算分析的表达式使用[EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)获取`IDebugProperty2`接口。 调用[GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md)返回[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) ，它描述内存地址。 然后，此内存上下文传递到[ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md)和[WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md)。  
  
## <a name="requirements"></a>要求  
 标头︰ msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 程序集︰ Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另请参阅  
 [核心接口](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md)   
 [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md)   
 [GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
