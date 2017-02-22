---
title: "IDebugOutputStringEvent2 | Microsoft Docs"
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
  - "IDebugOutputStringEvent2"
helpviewer_keywords: 
  - "IDebugOutputStringEvent2 接口"
ms.assetid: 86596fd1-cecc-4813-8add-dc3d70068f9b
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugOutputStringEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

调试引擎 \(DE\)发送此接口添加到该会话调试管理器 \(SDM\)输出字符串。  
  
## 语法  
  
```  
IDebugOutputStringEvent2 : IUnknown  
```  
  
## 实现者说明  
 DE implements 将字符串发送的此接口到 IDE 的 **输出** 窗口。  在对象必须实现 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) 接口和此接口相同。  SDM 使用 [QueryInterface](/visual-cpp/atl/queryinterface) 访问 `IDebugEvent2` 接口。  
  
## 调用方的说明  
 DE 创建和发送此事件对象将字符串发送到 **输出** 窗口。  事件发送通过使用 SDM 提供的 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 回调函数，则附加到正在调试时的过程。  
  
## 方法按 Vtable 顺序  
 下表显示 `IDebugOutputStringEvent2`方法。  
  
|方法|说明|  
|--------|--------|  
|[GetString](../Topic/IDebugOutputStringEvent2::GetString.md)|接收可显示的消息。|  
  
## 备注  
 例如，那么，当正在调试的程序将字符串发送到 Win32 `OutputDebugString` 函数时，在非托管代码，这是的字符串输出可能产生。  DE 截获此字符串并将其发送到 SDM 作为 `IDebugOutputStringEvent2` 事件。  
  
 使用 [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md) 发送需要一种用户响应的信息。  
  
 使用 [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md) 发送不需要响应的错误消息。  
  
## 要求  
 标题:msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md)   
 [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)