---
title: "IDebugEngine2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngine2"
helpviewer_keywords: 
  - "IDebugEngine2 接口"
ms.assetid: 1f0e9ac0-6dfb-461a-976c-888d82144cdb
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# IDebugEngine2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此接口表示调试引擎 \(DE\)。  它用于管理调试会话的各个方面，从创建断点。设置和清除的异常。  
  
## 语法  
  
```  
IDebugEngine2 : IUnknown  
```  
  
## 实现者说明  
 此接口由自定义 DE 实现托管调试程序。  必须由 DE 实现此接口。  
  
## 调用方的说明  
 此接口由该会话调用调试管理器 \(SDM\)管理调试会话，包括托管异常，创建断点和响应、发送的同步事件。  
  
## 方法按 Vtable 顺序  
 下表显示 `IDebugEngine2`方法。  
  
|方法|说明|  
|--------|--------|  
|[EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md)|创建、正在调试的所有过程的枚举数。|  
|[Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)|附加 DE 给过程。|  
|[CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)|在 DE 创建挂起的断点。|  
|[SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)|如果处理特定异常，如何指定 DE。|  
|[RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)|移除指定的异常，因此它由调试引擎不再处理。|  
|[RemoveAllSetExceptions](../Topic/IDebugEngine2::RemoveAllSetExceptions.md)|移除 IDE 为特定运行时结构或语言设置异常的列表。|  
|[GetEngineID](../../../extensibility/debugger/reference/idebugengine2-getengineid.md)|获取 DE 的 GUID。|  
|[DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)|通知、指定的程序非通常停止了，并且 DE 应清理所有引用。程序并发送程序销毁事件。|  
|[ContinueFromSynchronousEvent](../Topic/IDebugEngine2::ContinueFromSynchronousEvent.md)|调用 SDM 指示同步调试事件，以前发送由 DE 到 SDM，接收和处理。|  
|[SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md)|设置 DE 的区域设置。|  
|[SetRegistryRoot](../../../extensibility/debugger/reference/idebugengine2-setregistryroot.md)|设置注册表根当前正在使用由 DE。|  
|[SetMetric](../../../extensibility/debugger/reference/idebugengine2-setmetric.md)|设置指标。|  
|[CauseBreak](../../../extensibility/debugger/reference/idebugengine2-causebreak.md)|此请求、正在调试的所有过程停止自己的线程尝试执行下次正在运行。|  
  
## 要求  
 标题:Msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [Getengine 是](../../../extensibility/debugger/reference/idebugenginecreateevent2-getengine.md)