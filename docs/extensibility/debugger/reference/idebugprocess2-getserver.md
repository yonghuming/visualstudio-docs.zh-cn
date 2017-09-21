---
title: "IDebugProcess2::GetServer | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProcess2::GetServer"
helpviewer_keywords: 
  - "IDebugProcess2::GetServer"
ms.assetid: 8f73c530-cceb-4f1f-8c63-1cc0ccd4a310
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugProcess2::GetServer
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

获取此过程运行的服务器。  
  
## 语法  
  
```cpp#  
HRESULT GetServer(   
   IDebugCoreServer2** ppServer  
);  
```  
  
```c#  
int GetServer(   
   out IDebugCoreServer2 ppServer  
);  
```  
  
#### 参数  
 `ppServer`  
 \[out\] 返回表示服务器此过程运行的 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) 对象。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 备注  
 多个服务器上运行在一台计算机。  
  
## 请参阅  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)