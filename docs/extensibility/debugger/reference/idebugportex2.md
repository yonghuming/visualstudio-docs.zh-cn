---
title: "IDebugPortEx2 | Microsoft Docs"
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
  - "IDebugPortEx2"
helpviewer_keywords: 
  - "IDebugPortEx2 接口"
ms.assetid: 144724d0-38ee-4c9b-87ca-8a504371182b
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugPortEx2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此接口允许会议调试管理器 \(SDM\)控件程序和进程运行在端口。  
  
## 语法  
  
```  
IDebugPortEx2 : IUnknown  
```  
  
## 实现者说明  
 自定义端口提供程序实现在同一对象的此接口实现 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)。  
  
## 调用方的说明  
 SDM 调用 `IDebugPort2` 接口的 [QueryInterface](/visual-cpp/atl/queryinterface) 获取此接口。  
  
## 方法按 Vtable 顺序  
 下表显示 `IDebugPortEx2`方法。  
  
|方法|说明|  
|--------|--------|  
|[LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md)|生成可执行文件。|  
|[ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md)|回收进程的执行。|  
|[CanTerminateProcess](../../../extensibility/debugger/reference/idebugportex2-canterminateprocess.md)|确定进程是否可以停止。|  
|[TerminateProcess](../../../extensibility/debugger/reference/idebugportex2-terminateprocess.md)|停止处理。|  
|[GetPortProcessId](../../../extensibility/debugger/reference/idebugportex2-getportprocessid.md)|获取端口的进程 ID。|  
|[GetProgram](../../../extensibility/debugger/reference/idebugportex2-getprogram.md)|获取程序与程序节点。|  
  
## 备注  
 此接口通常是专用在 SDM 和自定义端口提供程序之间。  
  
 如果需要，调试引擎 \(DE\)可以位于 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) 接口的此接口传递给 [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) 和使用 [LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md) 启动程序。  这不是必需的，但是和 DE 可以执行将需要执行启动请求程序。  
  
## 要求  
 标题:portpriv.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [核心接口](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)