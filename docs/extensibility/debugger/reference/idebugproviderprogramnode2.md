---
title: "IDebugProviderProgramNode2 | Microsoft Docs"
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
  - "IDebugProviderProgramNode2"
helpviewer_keywords: 
  - "IDebugProviderProgramNode2"
ms.assetid: f0bca1cc-afbe-44cf-b5aa-d078aa685d24
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProviderProgramNode2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此接口具有相关的计划接口的进程边界。  
  
## 语法  
  
```  
IDebugProviderProgramNode2 : IUnknown  
```  
  
## 实现者说明  
 调试引擎 \(DE\)实现在同一对象的此接口实现支持的 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) 线接口的进程边界。  
  
## 调用方的说明  
 调用 `IDebugProgramNode2` 接口的 [QueryInterface](/visual-cpp/atl/queryinterface) 获取此接口。  如果此接口未能获得， DE 不支持将接口。  
  
## 方法按 Vtable 顺序  
 此接口执行以下方法:  
  
|方法|说明|  
|--------|--------|  
|[UnmarshalDebuggeeInterface](../../../extensibility/debugger/reference/idebugproviderprogramnode2-unmarshaldebuggeeinterface.md)|获取一个指定的接口进程边界。|  
  
## 备注  
 ，当 DE 在单独的进程中运行从正在调试时，程序的空间此接口实现:例如，那么，当 DE 在 Visual Studio 中运行进程空间而不是正在调试的程序的进程空间中。  
  
## 要求  
 标题:msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [核心接口](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)