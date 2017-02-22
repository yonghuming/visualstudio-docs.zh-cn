---
title: "IDebugProcessEx2::Detach | Microsoft Docs"
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
  - "IDebugProcessEx2::Detach"
helpviewer_keywords: 
  - "IDebugProcessEx2::Detach 方法"
ms.assetid: 66d54c2c-9302-47c8-9975-f30ed988ab29
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProcessEx2::Detach
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此方法通知进程内会话不再调试进程。  
  
## 语法  
  
```cpp#  
HRESULT Detach(   
   IDebugSession2* pSession  
);  
```  
  
```c#  
int Detach(  
   IDebugSession2 pSession  
);  
```  
  
#### 参数  
 `pSession`  
 \[in\] 唯一标识该会话分离此的值的过程。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 备注  
 在 `pSession` 传递的接口将只视为 cookie，唯一标识该会话调试管理器最初附加到此过程的值;在提供的接口的任何方法都不起作用。  
  
## 请参阅  
 [IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)