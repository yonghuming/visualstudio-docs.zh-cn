---
title: "IDebugProcessEx2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProcessEx2"
helpviewer_keywords: 
  - "IDebugProcessEx2 接口"
ms.assetid: 44e309ba-1d6f-499b-aa7e-9b34858a6d57
caps.latest.revision: 21
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 21
---
# IDebugProcessEx2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此接口允许会议调试管理器 \(SDM\)通知处理它附加到或从进程中分离。  
  
## 语法  
  
```  
IDebugProcessEx2 : IUnknown  
```  
  
## 实现者说明  
 自定义端口提供程序实现在对象的此接口和 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) 接口相同为:  
  
-   support 跟踪会话连接到进程  
  
-   support 跨多个自动附加调试引擎  
  
 ，则选择，自定义端口提供程序可以实现此接口。  
  
## 调用方的说明  
  
-   SDM 调用 `IDebugProcess2` 接口的 [QueryInterface](/visual-cpp/atl/queryinterface) 获取此接口。  
  
## 方法按 Vtable 顺序  
 下表显示 `IDebugProcessEx2`方法。  
  
|方法|说明|  
|--------|--------|  
|[Attach](../../../extensibility/debugger/reference/idebugprocessex2-attach.md)|通知处理会话现在调试进程。|  
|[Detach](../../../extensibility/debugger/reference/idebugprocessex2-detach.md)|通知处理会话不再调试进程。|  
|[AddImplicitProgramNodes](../../../extensibility/debugger/reference/idebugprocessex2-addimplicitprogramnodes.md)|添加列表的程序节点调试引擎。|  
  
## 备注  
 此接口是私有的。 SDM 和处理之间。  
  
## 要求  
 标题:Portpriv.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [核心接口](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)