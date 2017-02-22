---
title: "IDebugProgramNodeAttach2 | Microsoft Docs"
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
  - "IDebugProgramNodeAttach2"
helpviewer_keywords: 
  - "IDebugProgramNodeAttach2 接口"
ms.assetid: 46b37ac9-a026-4ad3-997b-f19e2f8deb73
caps.latest.revision: 3
caps.handback.revision: 3
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProgramNodeAttach2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

允许程序节点得到通知尝试附加到关联的程序。  
  
## 语法  
  
```  
IDebugProgramNodeAttach2 : IUnknown  
```  
  
## 实现者说明  
 此接口。 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) 实现接口以便接收附加操作通知和提供取消附加操作的同一个类中实现。  
  
## 调用方的说明  
 通过调用 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) 对象的 `QueryInterface` 方法获取此接口。  [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) 方法，对程序节点的可能性。 [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) 方法停止附加过程之前，必须调用。  
  
## 方法按 Vtable 顺序  
 此接口执行以下方法:  
  
|方法|说明|  
|--------|--------|  
|[OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)|附加到关联的程序或延迟附加处理 [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) 方法。|  
  
## 备注  
 此接口是首选替代方法已弃用 [Attach\_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md) 方法。  所有调试引擎。 `CoCreateInstance` 函数始终加载，也就是说，它们正在调试的程序的地址空间以外实例化。  
  
 如果 `IDebugProgramNode2::Attach_V7` 方法的一个以前的实现将被调试的程序的 `GUID` ，则只 [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) 方法需要执行。  
  
 如果 `IDebugProgramNode2::Attach_V7` 方法的一个以前的实现使用了提供的回调接口，则函数需要移到 [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) 方法和 `IDebugProgramNodeAttach2` 接口的实现不必实现。  
  
## 要求  
 标题:Msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [核心接口](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [Attach\_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)