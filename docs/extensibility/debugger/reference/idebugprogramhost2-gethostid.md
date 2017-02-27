---
title: "IDebugProgramHost2::GetHostId | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramHost2::GetHostId"
helpviewer_keywords: 
  - "IDebugProgramHost2::GetHostId"
ms.assetid: 7702e221-feb1-446b-a224-cb46c420987e
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProgramHost2::GetHostId
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

获取承载此程序的进程的进程标识符。  
  
## 语法  
  
```cpp#  
HRESULT GetHostId(   
   AD_PROCESS_ID* pdwId  
);  
```  
  
```c#  
int GetHostId(   
   AD_PROCESS_ID[] pdwId  
);  
```  
  
#### 参数  
 `pdwId`  
 \[in, out\] 使用进程标识符信息填充的 [AD\_PROCESS\_ID](../../../extensibility/debugger/reference/ad-process-id.md) 结构。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 请参阅  
 [IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)   
 [AD\_PROCESS\_ID](../../../extensibility/debugger/reference/ad-process-id.md)