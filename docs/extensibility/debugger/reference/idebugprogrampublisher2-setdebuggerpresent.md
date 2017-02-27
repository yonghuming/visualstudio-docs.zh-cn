---
title: "IDebugProgramPublisher2::SetDebuggerPresent | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramPublisher2::SetDebuggerPresent"
helpviewer_keywords: 
  - "IDebugProgramPublisher2::SetDebuggerPresent"
ms.assetid: c88c3ff4-3632-4199-b5de-83c6d21bcf75
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# IDebugProgramPublisher2::SetDebuggerPresent
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

告诉程序发行者调试器存在并运行。  
  
## 语法  
  
```cpp  
HRESULT SetDebuggerPresent(  
   BOOL fDebuggerPresent  
);  
```  
  
```c#  
int SetDebuggerPresent(  
   int fDebuggerPresent  
);  
```  
  
#### 参数  
 `fDebuggerPresent`  
 \[in\] 非零 \(`TRUE`\)，如果调试器存在，零 \(0\)`FALSE`\)，则不是。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 备注  
 是否存在调试器在从 [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md) 方法返回的数据反映:返回的值是设置或清除由以前的调用 `SetDebuggerPresent` 方法。  
  
## 请参阅  
 [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)   
 [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)