---
title: "IDebugProgramEx2 | Microsoft Docs"
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
  - "IDebugProgramEx2"
helpviewer_keywords: 
  - "IDebugProgramEx2 接口"
ms.assetid: 663359ed-635a-4539-addb-0cc52f19d1bd
caps.latest.revision: 18
caps.handback.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProgramEx2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此接口允许会议调试管理器 \(SDM\)附加到程序，并程序节点与程序的访问。  
  
## 语法  
  
```  
IDebugProgramEx2 : IUnknown  
```  
  
## 实现者说明  
 自定义端口提供程序实现在同一 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) 接口以便允许 SDM 附加到程序的对象的此接口，当同时允许端口提供程序跟踪所有会话附加到程序中。  ，则选择，自定义端口提供程序可以实现此接口。  
  
## 调用方的说明  
 SDM 调用 `IDebugProgram2` 接口的 [QueryInterface](/visual-cpp/atl/queryinterface) 获取此接口跟踪附加到程序的会话。  
  
## 方法按 Vtable 顺序  
 下表显示 `IDebugProgramEx2`方法。  
  
|方法|说明|  
|--------|--------|  
|[Attach](../../../extensibility/debugger/reference/idebugprogramex2-attach.md)|附加程序对会话。|  
|[GetProgramNode](../../../extensibility/debugger/reference/idebugprogramex2-getprogramnode.md)|获取程序节点与程序。|  
  
## 备注  
 此接口是私有的。 SDM 和程序之间。  
  
## 要求  
 标题:Portpriv.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [核心接口](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)