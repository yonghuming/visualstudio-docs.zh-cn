---
title: "IDebugProgramNodeAttach2::OnAttach | Microsoft Docs"
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
  - "IDebugProgramNodeAttach2::OnAttach"
helpviewer_keywords: 
  - "IDebugProgramNodeAttach2::OnAttach"
ms.assetid: 5fe52761-a508-4ab5-abdb-334fb6590334
caps.latest.revision: 3
caps.handback.revision: 3
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProgramNodeAttach2::OnAttach
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

附加到关联的程序或延迟附加处理 [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) 方法。  
  
## 语法  
  
```cpp#  
HRESULT OnAttach(  
   [in] REFGUID guidProgramId  
);  
```  
  
```c#  
int OnAttach(  
   ref Guid guidProgramId  
};  
```  
  
#### 参数  
 `guidProgramId`  
 \[in\] 分配的 `GUID` 到关联的程序。  
  
## 返回值  
 如果成功，则返回 `S_OK`。  ，如果 [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) 方法不应调用，返回 `S_FALSE` 。  否则，返回错误代码。  
  
## 备注  
 ，在 [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) 调用方法之前，此方法调用其他过程。  `OnAttach` 方法可以执行其他处理 \(在中，此方法返回 `S_FALSE`\) 情况下或延迟附加处理 `IDebugEngine2::Attach` 方法 \( `OnAttach` 方法返回 `S_OK`\)。  在任何情况下， `OnAttach` 方法可以设置正在调试对特定 `GUID`程序的 `GUID` 。  
  
## 请参阅  
 [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)