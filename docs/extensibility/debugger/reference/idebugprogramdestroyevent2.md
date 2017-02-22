---
title: "IDebugProgramDestroyEvent2 | Microsoft Docs"
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
  - "IDebugProgramDestroyEvent2"
helpviewer_keywords: 
  - "IDebugProgramDestroyEvent2"
ms.assetid: ddf127ca-c4a5-4071-90ca-68faf2f57dbd
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProgramDestroyEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

，当程序已完成运行时，调试引擎 \(DE\)发送此接口添加到该会话调试管理器 \(SDM\)。  
  
## 语法  
  
```  
IDebugProgramDestroyEvent2 : IUnknown  
```  
  
## 实现者说明  
 DE 或自定义端口提供程序实现此接口提供程序将停止并用于调试不再可用。  在对象必须实现 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) 接口和此接口相同。  SDM 使用 [QueryInterface](/visual-cpp/atl/queryinterface) 访问 `IDebugEvent2` 接口。  
  
## 调用方的说明  
 DE 或自定义端口提供创建和发送此事件对象报告程序终止。  DE 发送此事件使用 SDM 提供的 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 回调函数，则附加到正在调试的程序。  使用 [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) 接口，自定义端口提供程序发送此事件。  
  
## 方法按 Vtable 顺序  
 下表显示 `IDebugProgramDestroyEvent2`方法。  
  
|方法|说明|  
|--------|--------|  
|[GetExitCode](../Topic/IDebugProgramDestroyEvent2::GetExitCode.md)|获取程序的退出代码。|  
  
## 要求  
 标题:msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [核心接口](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)