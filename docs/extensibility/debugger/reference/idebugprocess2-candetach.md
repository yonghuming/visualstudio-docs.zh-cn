---
title: "IDebugProcess2::CanDetach | Microsoft Docs"
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
  - "IDebugProcess2::CanDetach"
helpviewer_keywords: 
  - "IDebugProcess2::CanDetach"
ms.assetid: 2830f7c3-69fb-474a-97b8-5b869e38d546
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProcess2::CanDetach
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

确定会话是否调试管理器 \(SDM\)可分离进程。  
  
## 语法  
  
```cpp#  
HRESULT CanDetach(  
   void  
);  
```  
  
```c#  
int CanDetach();  
```  
  
## 返回值  
 如果成功，则返回 `S_OK.` 返回 `S_FALSE` ，如果调试器无法从进程中分离。  否则，返回错误代码。  
  
## 请参阅  
 [CanDetach](../Topic/IDebugProgram2::CanDetach.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)