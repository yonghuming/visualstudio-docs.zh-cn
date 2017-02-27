---
title: "IDebugEngineLaunch2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngineLaunch2"
helpviewer_keywords: 
  - "IDebugEngineLaunch2 接口"
ms.assetid: 5eaf2ad8-3fbf-446e-b48b-5327ad3f5255
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugEngineLaunch2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

用于使调试引擎 \(DE\)启动和停止程序。  
  
## 语法  
  
```  
IDebugEngineLaunch2 : IDebugEngine2  
```  
  
## 实现者说明  
 此接口由自定义 DE 实现，如果有生成不能由一个自定义端口完全的进程的特殊要求。  这通常是这样，因此 DE 是解释器中的一部分，而且正在调试的进程是脚本:解释器需要首先生成，该脚本然后加载并开始。  端口可能生成解释器，但是，该脚本可能需要为的特定进程 \(DE 有一个角色\) 的位置。  此接口由实现，只有在启动一个自定义端口不能处理程序的唯一要求。  
  
## 调用方的说明  
 此接口由该会话调用调试管理器 \(SDM\)，如果 SDM 可以从获取 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) 接口的此接口 \(使用 QI\)。  如果此接口可用， SDM 了解、有特殊要求并调用此接口启动程序而不是端口启动它。  
  
## 方法按 Vtable 顺序  
 下表显示 `IDebugEngineLaunch2`方法。  
  
|方法|说明|  
|--------|--------|  
|[LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)|通过、生成过程。|  
|[ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)|进程继续执行。|  
|[CanTerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-canterminateprocess.md)|确定进程是否可以停止。|  
|[TerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-terminateprocess.md)|停止处理。|  
  
## 要求  
 标题:Msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)