---
title: "IDebugStopCompleteEvent2 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IDebugStopCompleteEvent2 interface
ms.assetid: ff3e89f4-61bb-489d-901c-447260100218
caps.latest.revision: 6
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
ms.openlocfilehash: 55061440f4690c9b9f9b7a90dc5474391f908046
ms.lasthandoff: 02/22/2017

---
# <a name="idebugstopcompleteevent2"></a>IDebugStopCompleteEvent2
程序已停止时，调试引擎 (DE) 可以向会话调试管理器 (SDM) 发送此可选事件。  
  
## <a name="syntax"></a>语法  
  
```  
IDebugStopCompleteEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>实施者注意事项  
 这是新接口[!INCLUDE[vsprvslong](../../../code-quality/includes/vsprvslong_md.md)]。 以前的版本不支持异步停止。  
  
 [停止](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md)由多进程或多程序方案中 SDM 调用。 当一个程序将停止事件发送到 SDM 时，SDM 请求停止，太其他程序。  
  
 它用来以异步方式通知程序已经停止 SDM。 这可用于解释器调试引擎，其中有时不运行任何代码在调试的程序，因此[停止](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md)未以同步方式完成。 如果调试引擎想要使用此异步通知时，它必须返回`S_ASYNC_STOP`从[停止](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md)。  
  
## <a name="requirements"></a>要求  
 标头︰ msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 程序集︰ Microsoft.VisualStudio.Debugger.Interop.dll
