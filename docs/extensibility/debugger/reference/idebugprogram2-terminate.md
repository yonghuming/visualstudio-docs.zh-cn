---
title: "IDebugProgram2::Terminate | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgram2::Terminate"
helpviewer_keywords: 
  - "IDebugProgram2::Terminate"
ms.assetid: 4d3127d3-b1e9-4b28-ac22-2f2eea255f86
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugProgram2::Terminate
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

停止程序。  
  
## 语法  
  
```cpp#  
HRESULT Terminate(   
   void   
);  
```  
  
```c#  
int Terminate();  
```  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 备注  
 如果可能，程序进程将停止并卸载;否则，调试引擎 \(DE\)会执行所有必要的清理。  
  
 此方法或 [终止](../../../extensibility/debugger/reference/idebugprocess2-terminate.md) 方法由 IDE 调用，通常是为了响应暂停所有调试的用户。  此方法的实现应，在理想情况下，终止进程中的程序。  如果无法实现这一点， DE 应防止程序运行该过程 \(和执行所有必要的清理\)。  如果 `IDebugProcess2::Terminate` 方法由 IDE 调用，整个过程某些时将停止，在 `IDebugProgram2::Terminate` 调用方法之后。  
  
## 请参阅  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [终止](../../../extensibility/debugger/reference/idebugprocess2-terminate.md)