---
title: "IDebugProgramPublisher2::UnpublishProgram | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramPublisher2::UnpublishProgram"
helpviewer_keywords: 
  - "IDebugProgramPublisher2::UnpublishProgram"
ms.assetid: 627e7d38-b2ac-4873-9a40-37ff7f47cd1d
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugProgramPublisher2::UnpublishProgram
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

某程序未提供进行调试。  
  
## 语法  
  
```cpp  
HRESULT UnpublishProgram(  
   IUnknown* pDebuggeeInterface  
);  
```  
  
```c#  
int UnpublishProgram(  
   object pDebuggeeInterface  
);  
```  
  
#### 参数  
 `pDebuggeeInterface`  
 \[in\] 对程序的一 `IUnknown` 接口。  这是相同的值提供给 [PublishProgram](../Topic/IDebugProgramPublisher2::PublishProgram.md) 方法和唯一标识移除的程序 \(即它用作 cookie\)。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 备注  
 若要使程序提供调试引擎和会话调试管理器，请使用 [PublishProgram](../Topic/IDebugProgramPublisher2::PublishProgram.md) 方法。  
  
## 请参阅  
 [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)   
 [PublishProgram](../Topic/IDebugProgramPublisher2::PublishProgram.md)