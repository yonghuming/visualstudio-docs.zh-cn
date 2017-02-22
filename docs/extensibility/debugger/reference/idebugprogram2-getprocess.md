---
title: "IDebugProgram2::GetProcess | Microsoft Docs"
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
  - "IDebugProgram2::GetProcess"
helpviewer_keywords: 
  - "IDebugProgram2::GetProcess"
ms.assetid: 1d602485-ebaf-451c-9165-f2e226f20a90
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProgram2::GetProcess
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

获取此过程运行的进程。  
  
## 语法  
  
```cpp  
HRESULT GetProcess(  
   IDebugProcess2** ppProcess  
);  
```  
  
```c#  
int GetProcess(  
   out IDebugProcess2 ppProcess  
);  
```  
  
#### 参数  
 `ppProcess`  
 \[out\] 返回表示处理的 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) 接口。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 备注  
 除非调试引擎 \(DE\) [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md) 实现接口，则此方法的 DE 的实现应始终返回 `E_NOTIMPL` ，因为、不确定的过程运行它并不能满足此方法的实现。  
  
 实现接口 `IDebugEngineLaunch2` 意味着 DE 必须知道如何创建处理;因此， [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) 接口的 DE 的实现可以知道进程运行它。  
  
## 请参阅  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)