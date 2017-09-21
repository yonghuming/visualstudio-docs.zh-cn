---
title: "IDebugEngine3::SetJustMyCodeState | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngine3::SetJustMyCodeState"
helpviewer_keywords: 
  - "IDebugEngine3::SetJustMyCodeState"
ms.assetid: 8ec17fbf-df93-424a-b2ed-fd1e5ee51256
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugEngine3::SetJustMyCodeState
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此方法通知 JustMyCode 状态信息的调试引擎。  
  
## 语法  
  
```cpp  
HRESULT SetJustMyCodeState(  
   BOOL           fUpdate,  
   DWORD          dwModules,  
   JMC_CODE_SPEC* rgJMCSpec  
);  
```  
  
```c#  
int SetJustMyCodeState(  
   int             fUpdate,   
   uint            dwModules,   
   JMC_CODE_SPEC[] rgJMCSpec  
);  
```  
  
#### 参数  
 `fUpdate`  
 \[in\] 非零 \(`TRUE`\) 更新当前信息，零 \(0\)`FALSE`\) 重置所有信息 \(忽略之前设置的任何内容\)。  
  
 `dwModules`  
 \[in\] 信息结构数。 `rgJMCSpec.`的  
  
 `rgJMCSpec`  
 \[in\] 某些使用的 [JMC\_CODE\_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md) 结构。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 备注  
 JustMyCode 是调试属于用户并忽略所有中间代码 \(如代码均匀的系统仅的代码的概念，如果源代码对该系统代码可用。  
  
## 请参阅  
 [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)   
 [JMC\_CODE\_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md)