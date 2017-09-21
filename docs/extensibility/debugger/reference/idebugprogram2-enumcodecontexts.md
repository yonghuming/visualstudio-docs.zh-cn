---
title: "IDebugProgram2::EnumCodeContexts | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgram2::EnumCodeContexts"
helpviewer_keywords: 
  - "IDebugProgram2::EnumCodeContexts"
ms.assetid: 478e06a2-07bb-4841-8887-deab0f42ebd0
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProgram2::EnumCodeContexts
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

检索代码上下文中列出给定位置的源文件。  
  
## 语法  
  
```cpp#  
HRESULT EnumCodeContexts(   
   IDebugDocumentPosition2*  pDocPos,  
   IEnumDebugCodeContexts2** ppEnum  
);  
```  
  
```c#  
int EnumCodeContexts(   
   IDebugDocumentPosition2     pDocPos,  
   out IEnumDebugCodeContexts2 ppEnum  
);  
```  
  
#### 参数  
 `pDocPos`  
 \[in\] 表示源文件中的一 [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md) 对象抽象位置为 IDE 的地址。  
  
 `ppEnum`  
 \[out\] 返回包含代码上下文的列表 [IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md) 对象。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 备注  
 此方法允许会议调试管理器 \(SDM\)或 IDE 映射源文件位置。代码位置。  多个代码上下文返回，如果源生成多个代码块 \(例如， C\+\+ 模板\)。  
  
## 请参阅  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)   
 [IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)