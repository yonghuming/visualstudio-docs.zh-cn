---
title: "IDebugActivateDocumentEvent2 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugActivateDocumentEvent2
helpviewer_keywords: IDebugActivateDocumentEvent2 interface
ms.assetid: 6f37edd7-a48c-4b41-b160-dff9be63a284
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9f21648f9b019fbb765290d969b1a6c68fe5ce2f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="idebugactivatedocumentevent2"></a>IDebugActivateDocumentEvent2
调试引擎 (DE) 使用此接口来请求要加载的文档。  
  
## <a name="syntax"></a>语法  
  
```  
IDebugActivateDocumentEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>实施者注意事项  
 当它需要要打开的源文件时，DE 实现此接口。 只能通过使用或属于脚本的解释程序的调试引擎实现此接口。 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)接口必须实现该接口对同一个对象 (SDM 使用[QueryInterface](/cpp/atl/queryinterface)访问`IDebugEvent2`接口)。  
  
## <a name="notes-for-callers"></a>调用方的说明  
 DE 创建，并需要有源文件在打开时发送此事件对象。 通过使用发送事件[IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) SDM 时将其附加到正在调试的程序所提供的回调函数。  
  
## <a name="methods-in-vtable-order"></a>Vtable 顺序中的方法  
 下表显示的方法`IDebugActivateDocumentEvent2`。  
  
|方法|描述|  
|-------------|-----------------|  
|[GetDocument](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocument.md)|获取要激活的文档。|  
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocumentcontext.md)|获取用于描述文档中的位置的文档上下文。|  
  
## <a name="remarks"></a>备注  
 在其中使用此接口的典型情况是如果在 HTML 页上的脚本代码中发生分析错误，脚本 DE 此接口会向发送 SDM 以显示文档使用了分析错误。  
  
## <a name="requirements"></a>要求  
 标头： msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 程序集： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另请参阅  
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)