---
title: "IDebugAddress2::GetProcessID | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugAddress2::GetProcessID"
helpviewer_keywords: 
  - "IDebugAddress2::GetProcessID 方法"
ms.assetid: 2c18889d-074a-4b95-87b4-bf1a067f44ed
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# IDebugAddress2::GetProcessID
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

检索拥有此 [IDebugAddress2](../../../extensibility/debugger/reference/idebugaddress2.md) 接口表示的对象进程的 ID。  
  
## 语法  
  
```cpp  
HRESULT GetProcessID (  
   DWORD* pProcID  
);  
```  
  
```c#  
int GetProcessID (  
   out uint pProcID  
);  
```  
  
#### 参数  
 `pProcID`  
 \[out\] 进程 ID.  
  
## 返回值  
 如果成功，则返回 S\_OK;否则，返回错误代码。  
  
## 请参阅  
 [IDebugAddress2](../../../extensibility/debugger/reference/idebugaddress2.md)