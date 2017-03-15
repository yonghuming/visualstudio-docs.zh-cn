---
title: "IDebugAddress2 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugAddress2
helpviewer_keywords:
- IDebugAddress2 interface
ms.assetid: b150e0ed-4ac0-4f8c-9732-4b3e54b9d243
caps.latest.revision: 10
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
ms.openlocfilehash: 005911465f7ba78a3a6dcdf8249a96443cd12355
ms.lasthandoff: 02/22/2017

---
# <a name="idebugaddress2"></a>IDebugAddress2
此接口提供由该接口表示访问拥有其地址的对象的进程 ID。  
  
## <a name="syntax"></a>语法  
  
```  
IDebugAddress2 : IDebugAddress  
```  
  
## <a name="notes-for-implementers"></a>实施者注意事项  
 符号提供程序实现的相同对象上实现此接口[IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)接口。 此接口提供对拥有的对象，该地址与相关的进程的 ID 的访问。  
  
## <a name="notes-for-callers"></a>调用方的说明  
 使用[QueryInterface](/visual-cpp/atl/queryinterface)以获取此接口从[IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)接口。  
  
## <a name="methods-in-vtable-order"></a>Vtable 顺序中的方法  
 除了从继承的方法[IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)接口，此接口实现了以下方法︰  
  
|方法|说明|  
|------------|-----------------|  
|[GetProcessID](../../../extensibility/debugger/reference/idebugaddress2-getprocessid.md)|检索表示此接口的对象拥有的进程的 ID。|  
  
## <a name="requirements"></a>要求  
 标头︰ sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 程序集︰ Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另请参阅  
 [符号提供程序接口](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
