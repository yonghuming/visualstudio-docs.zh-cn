---
title: "IDebugPropertyDestroyEvent2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPropertyDestroyEvent2"
helpviewer_keywords: 
  - "IDebugPropertyDestroyEvent2 接口"
ms.assetid: 301b7a75-ecfa-46f1-9131-66cf3e4be147
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugPropertyDestroyEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

调试引擎 \(DE\)发送此接口添加到该会话调试管理器 \(SDM\)，在与中的属性特定文件将被销毁。  
  
## 语法  
  
```  
IDebugPropertyDestroyEvent2 : IUnknown  
```  
  
## 实现者说明  
 DE implements 报告此的接口销毁了 "。  在对象必须实现 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) 接口和此接口相同。  SDM 使用 [QueryInterface](/visual-cpp/atl/queryinterface) 访问 `IDebugEvent2` 接口。  DE，如果以前创建了一个属性与脚本，此接口实现;在销毁 " 从 IDE 中移除该关联的脚本。  
  
## 调用方的说明  
 DE 创建和发送此事件对象报告销毁了 "。  事件发送通过使用 SDM 提供的 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 回调函数，则附加到正在调试时的过程。  
  
## 方法按 Vtable 顺序  
 下表显示 `IDebugPropertyDestroyEvent2`方法。  
  
|方法|说明|  
|--------|--------|  
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugpropertydestroyevent2-getdebugproperty.md)|获取属性销毁。|  
  
## 备注  
 为 [IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md) 参见备注有关的原因的详细信息使用这些事件。  
  
## 要求  
 标题:msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [核心接口](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md)