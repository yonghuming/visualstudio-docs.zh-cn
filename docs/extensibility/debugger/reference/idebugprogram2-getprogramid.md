---
title: "IDebugProgram2::GetProgramId | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgram2::GetProgramId"
helpviewer_keywords: 
  - "IDebugProgram2::GetProgramId"
ms.assetid: 2c31c0aa-2b71-46c7-849c-356e237d26f8
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugProgram2::GetProgramId
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

获取此过程的 GUID。  
  
## 语法  
  
```cpp#  
HRESULT GetProgramId(   
   GUID* pguidProgramId  
);  
```  
  
```c#  
int GetProgramId(   
   out Guid pguidProgramId  
);  
```  
  
#### 参数  
 `pguidProgramId`  
 \[out\] 返回此过程的 `GUID` 。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 备注  
 调试引擎 \(DE\)必须返回程序标识符最初传递给 [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) 或 [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) 方法。  这使程序的标识。调试器组件中。  
  
## 请参阅  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)   
 [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)