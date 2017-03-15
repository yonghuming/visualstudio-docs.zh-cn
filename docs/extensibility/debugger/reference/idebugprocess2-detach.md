---
title: "IDebugProcess2::Detach | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProcess2::Detach"
helpviewer_keywords: 
  - "IDebugProcess2::Detach"
ms.assetid: ee2b9084-2db1-4e49-a1d9-387284b7c3f8
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProcess2::Detach
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

分离此的调试器通过分离所有进程在处理过程。  
  
## 语法  
  
```cpp#  
HRESULT Detach(   
   void   
);  
```  
  
```c#  
int Detach();  
```  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 备注  
 所有程序和处理继续运行，但是，不再是调试会话的一部分。  在分离操作完成后，而不调试此事件处理 \(及其程序\) 将发送。  
  
## 请参阅  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)