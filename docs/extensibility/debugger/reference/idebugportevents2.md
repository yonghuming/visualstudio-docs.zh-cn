---
title: "IDebugPortEvents2 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugPortEvents2
helpviewer_keywords: IDebugPortEvents2 interface
ms.assetid: 2c017094-3ba2-4067-83f9-147df1d96bce
caps.latest.revision: "18"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 75e0b83b81c0d0d80b29c6b9ab32826402fcec99
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="idebugportevents2"></a>IDebugPortEvents2
此接口通知的过程和程序创建和析构特定端口上的侦听器 （通常会话调试管理器 [SDM] 或调试引擎）。 此信息可以用于显示的进程和在端口上运行的程序的实时视图。  
  
## <a name="syntax"></a>语法  
  
```  
IDebugPortEvents2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>实施者注意事项  
 Visual Studio 通常实现此接口可接收有关程序创建和析构的通知。 调试引擎还可以实现此接口可侦听此类端口事件。  
  
## <a name="notes-for-callers"></a>调用方的说明  
 所有[IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)接口可以查询有关<xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer>接口。 则<xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.FindConnectionPoint%2A>方法`IDebugPortEvents2`中称为<xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer>要获取接口<xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint>接口。 最后，<xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A>中的方法<xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint>接口调用以通过将事件发送[事件](../../../extensibility/debugger/reference/idebugportevents2-event.md)方法。  
  
## <a name="methods-in-vtable-order"></a>Vtable 顺序中的方法  
 下表显示的方法`IDebugPortEvents2`。  
  
|方法|描述|  
|------------|-----------------|  
|[Event](../../../extensibility/debugger/reference/idebugportevents2-event.md)|将发送描述的创建和析构的进程和程序的端口上的事件。|  
  
## <a name="remarks"></a>备注  
 `IDebugPortEvents2`此外可通过 SDM 调试正在调试的进程中运行的程序。  
  
 此接口由传递给 SDM 端口事件。  
  
## <a name="requirements"></a>要求  
 标头： msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 程序集： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另请参阅  
 [核心接口](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)