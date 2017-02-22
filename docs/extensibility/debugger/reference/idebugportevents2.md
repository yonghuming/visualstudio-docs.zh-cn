---
title: "IDebugPortEvents2 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPortEvents2"
helpviewer_keywords: 
  - "IDebugPortEvents2 接口"
ms.assetid: 2c017094-3ba2-4067-83f9-147df1d96bce
caps.latest.revision: 18
caps.handback.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugPortEvents2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此接口在特定端口通知侦听器 \(会议通常调试管理器 SDM \[\] 或调试引擎处理和过程创作和毁坏。  此信息可用于提供一个实时查看过程和运行于端口的过程。  
  
## 语法  
  
```  
IDebugPortEvents2 : IUnknown  
```  
  
## 实现者说明  
 Visual Studio 通常实现此接口接收有关程序创作和析构的通知。  调试引擎还可以实现此接口端口侦听此事件。  
  
## 调用方的说明  
 所有 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) 接口可用于 <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> 接口中查询。  然后 `IDebugPortEvents2` 的 <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.FindConnectionPoint%2A> 方法在 <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> 接口调用来获取 <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> 接口。  最后，在 <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> 接口的 <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A> 方法调用通过 [事件](../../../extensibility/debugger/reference/idebugportevents2-event.md) 方法发送事件。  
  
## 方法按 Vtable 顺序  
 下表显示 `IDebugPortEvents2`方法。  
  
|方法|说明|  
|--------|--------|  
|[事件](../../../extensibility/debugger/reference/idebugportevents2-event.md)|发送描述，以创建和销毁处理和位于端口的程序的事件。|  
  
## 备注  
 `IDebugPortEvents2` 由 SDM 还可用于调试进程中运行已调试的程序。  
  
 端口事件传递给 SDM 此接口。  
  
## 要求  
 标题:msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [核心接口](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)