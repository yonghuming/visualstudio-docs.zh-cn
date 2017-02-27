---
title: "IDebugPortEx2::CanTerminateProcess | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPortEx2::CanTerminateProcess"
helpviewer_keywords: 
  - "IDebugPortEx2::CanTerminateProcess"
ms.assetid: 111f65d8-5a1a-42b3-9de3-dd9bb03a33fd
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugPortEx2::CanTerminateProcess
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

确定进程是否可以停止。  
  
## 语法  
  
```cpp#  
HRESULT CanTerminateProcess(   
   IDebugProcess2* pPortProcess  
);  
```  
  
```c#  
HRESULT CanTerminateProcess(   
   IDebugProcess2 pPortProcess  
);  
```  
  
#### 参数  
 `pPortProcess`  
 \[in\] 表示处理的 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) 对象将停止。  
  
## 返回值  
 如果处理，可以停止，返回 `S_OK` ;否则，返回 `S_FALSE`。  
  
## 请参阅  
 [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)