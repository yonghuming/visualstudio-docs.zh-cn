---
title: "IDebugModuleLoadEvent2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugModuleLoadEvent2"
helpviewer_keywords: 
  - "IDebugModuleLoadEvent2 接口"
ms.assetid: 7d26fb23-5d49-4ba7-b7c5-3aed4d7be81e
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugModuleLoadEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

，当模块加载或卸载时，调试引擎 \(DE\)发送此接口添加到该会话调试管理器 \(SDM\)。  
  
## 语法  
  
```  
IDebugModuleLoadEvent2 : IUnknown  
```  
  
## 实现者说明  
 DE implements 报告此接口的模块加载或卸载。  在对象必须实现 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) 接口和此接口相同。  SDM 使用 [QueryInterface](/visual-cpp/atl/queryinterface) 访问 `IDebugEvent2` 接口。  
  
## 调用方的说明  
 DE 创建和发送此事件对象、模块加载或卸载。  事件发送通过使用 SDM 提供的 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 回调函数，则附加到正在调试时的过程。  
  
## 方法按 Vtable 顺序  
 下表显示 `IDebugModuleLoadEvent2`方法。  
  
|方法|说明|  
|--------|--------|  
|[GetModule](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md)|获取加载或卸载的模块。|  
  
## 备注  
 Visual Studio 使用此事件 **模块** 窗口保持最新。  
  
## 要求  
 标题:msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [核心接口](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)