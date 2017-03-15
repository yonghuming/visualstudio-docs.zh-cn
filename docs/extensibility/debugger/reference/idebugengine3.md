---
title: "IDebugEngine3 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugEngine3
helpviewer_keywords:
- IDebugEngine3 interface
ms.assetid: 8bdf4bb7-3b5d-4991-8981-772d4f6bb656
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 293517b87b57e905e5807fa9e3f07a47d4cead4c
ms.lasthandoff: 02/22/2017

---
# <a name="idebugengine3"></a>IDebugEngine3
表示单个调试引擎 (DE)，用于控制对一个或多个模块的调试。  
  
## <a name="syntax"></a>语法  
  
```  
IDebugEngine3 : IDebugEngine2  
```  
  
## <a name="notes-for-implementers"></a>实施者注意事项  
 实现此接口是通过自定义 DE （如果它支持符号） 若要启用的 JustMyCode 状态。 如果它支持符号和 JustMyCode，DE 必须实现此接口。  
  
## <a name="notes-for-callers"></a>调用方的说明  
 此接口由会话调试管理器 (SDM) 要传递要从其加载符号的位置的用户选项的调用。 它也称为实例化时设置该引擎的 GUID （此 GUID 基于从引擎注册的时间的度量值）。 SDM 也会调用此接口可设置的 JustMyCode 状态和设置的所有调试程序对指定的状态的已知的例外情况。  
  
## <a name="methods-in-vtable-order"></a>Vtable 顺序中的方法  
 除了从继承的方法[IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)、`IDebugEngine3`接口公开下列方法。  
  
|方法|说明|  
|------------|-----------------|  
|[SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)|设置 DE 将使用搜索的调试符号的路径。|  
|[LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md)|加载所有尚未有加载其符号的模块的符号。|  
|[SetJustMyCodeState](../../../extensibility/debugger/reference/idebugengine3-setjustmycodestate.md)|告知 DE JustMyCode 信息。|  
|[SetEngineGuid](../../../extensibility/debugger/reference/idebugengine3-setengineguid.md)|从度量值设置 DE GUID。|  
|[SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md)|将当前未完成的所有异常都设置为指定的状态。|  
  
## <a name="requirements"></a>要求  
 标头︰ msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 程序集︰ Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另请参阅  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
