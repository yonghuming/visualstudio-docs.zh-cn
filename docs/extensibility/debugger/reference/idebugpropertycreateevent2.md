---
title: "IDebugPropertyCreateEvent2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPropertyCreateEvent2"
helpviewer_keywords: 
  - "IDebugPropertyCreateEvent2 接口"
ms.assetid: 33b3082b-a42e-488a-a1e4-dadf506f922c
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# IDebugPropertyCreateEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

调试引擎 \(DE\)发送此接口添加到该会话调试管理器 \(SDM\)，在创建与特定文件的属性时。  
  
## 语法  
  
```  
IDebugPropertyCreateEvent2 : IUnknown  
```  
  
## 实现者说明  
 DE implements 报告此接口的属性创建了。  在对象必须实现 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) 接口和此接口相同。  SDM 使用 [QueryInterface](/visual-cpp/atl/queryinterface) 访问 `IDebugEvent2` 接口。  此接口由实现，如果 DE 创建了一个属性与已加载或已创建的脚本，并且，如果该脚本需要显示在 IDE 中。  
  
## 调用方的说明  
 DE 创建和发送此事件对象的属性创建了。  事件发送通过使用 SDM 提供的 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 回调函数，则附加到正在调试时的过程。  
  
## 方法按 Vtable 顺序  
 下表显示 `IDebugPropertyCreateEvent2` 接口的方法。  
  
|方法|说明|  
|--------|--------|  
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugpropertycreateevent2-getdebugproperty.md)|获取新属性。|  
  
## 备注  
 如果特性具有特定文件或脚本与其关联， DE 可以发送此事件。 SDM 为了更新具有文档的名称的 **脚本文档** 窗口。  SDM 将调用变量 `guidDocument` 的 [GetExtendedInfo](../../../extensibility/debugger/reference/idebugproperty2-getextendedinfo.md) 检索包含 [IUnknown](/visual-cpp/atl/iunknown) 指针的 `VARIANT` 。  SDM 将调用此指针的 [QueryInterface](/visual-cpp/atl/queryinterface) 检索用于更新 **脚本文档** 窗口的 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) 接口。  
  
## 要求  
 标题:msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [核心接口](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)