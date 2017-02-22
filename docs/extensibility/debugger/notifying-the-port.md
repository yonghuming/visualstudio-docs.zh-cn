---
title: "通知端口 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "通知端口"
ms.assetid: f9fce48e-7d4e-4627-a0fb-77b75428146a
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# 通知端口
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

在启动程序之后，必须通知端口，如下所示:  
  
1.  当端口接收新的程序节点时，它将一个过程了事件。调试会话。  事件具有与其表示程序的接口。  
  
2.  调试会话查询可以附加调试引擎 \(DE\)的标识符的过程。  
  
3.  调试会话检查、是否在允许的 DES 列表该程序中。  调试会话获取从解决方案中的事件程序设置列表，最初传递给它的调试包。  
  
     DE 必须在允许列表，或者 DE 不依赖于程序。  
  
 编程，那么，当端口首先得到一个新的程序节点时，它将创建一 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) 接口表示程序。  
  
> [!NOTE]
>  不应与调试引擎 \(DE\)之后创建的 `IDebugProgram2` 接口混淆。  
  
 端口将一个 [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) 程序了事件。该会话通过 COM `IConnectionPoint` 接口调试管理器 \(SDM\)。  
  
> [!NOTE]
>  不应与 `IDebugProgramCreateEvent2` 接口混淆。， DE 后发送。  
  
 与事件接口。，端口发送 [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)， [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)，并且， [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) 接口，表示端口，处理和过程，它们。  SDM 调用 [IDebugProgram2:: GetEngineInfo](../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md) 获取能调试程序 DE 的 GUID。  GUID 从 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) 接口最初获得。  
  
 SDM 检查、是否在允许的 DES 列表。  SDM 获取从解决方案中的事件程序设置列表，最初传递给它的调试包。  DE 必须在允许列表，也不依赖于程序。  
  
 一次 DE 的标识知道， SDM 准备附加到程序。  
  
## 请参阅  
 [下启动程序](../../extensibility/debugger/launching-a-program.md)   
 [启动后附加](../../extensibility/debugger/attaching-after-a-launch.md)   
 [调试任务](../../extensibility/debugger/debugging-tasks.md)