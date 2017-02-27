---
title: "IDebugMemoryContext2::Compare | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugMemoryContext2::Compare"
helpviewer_keywords: 
  - "IDebugMemoryContext2::Compare 方法"
  - "“比较”方法"
ms.assetid: c51b5128-848e-4d8e-b2e9-1161339763c3
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# IDebugMemoryContext2::Compare
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

与给定数组的每个上下文比较内存上下文以指示的方式比较标志，返回匹配第一个上下文的索引。  
  
## 语法  
  
```cpp#  
HRESULT Compare(   
   CONTEXT_COMPARE        compare,  
   IDebugMemoryContext2** rgpMemoryContextSet,  
   DWORD                  dwMemoryContextSetLen,  
   DWORD*                 pdwMemoryContext  
);  
```  
  
```c#  
int Compare(  
   enum_CONTEXT_COMPARE   compare,   
   IDebugMemoryContext2[] rgpMemoryContextSet,   
   uint                   dwMemoryContextSetLen,   
   out uint               pdwMemoryContext  
);  
```  
  
#### 参数  
 `compare`  
 \[in\] 从确定比较的类型的 [CONTEXT\_COMPARE](../../../extensibility/debugger/reference/context-compare.md) 枚举的值。  
  
 `rgpMemoryContextSet`  
 \[in\] 数组对 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) 对象进行比较。  
  
 `dwMemoryContextSetLen`  
 \[in\] 上下文数 `rgpMemoryContextSet` 数组。  
  
 `pdwMemoryContext`  
 \[out\] 返回满足该比较第一个内存上下文的索引。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  例如，如果两上下文不能比较，返回 `E_COMPARE_CANNOT_COMPARE` 。  
  
## 备注  
 调试引擎 \(DE\)不必支持比较的类型，但是，它必须支持 `CONTEXT_EQUAL`、 `CONTEXT_LESS_THAN`、至少 `CONTEXT_GREATER_THAN` 和 `CONTEXT_SAME_SCOPE`。  
  
## 请参阅  
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)   
 [CONTEXT\_COMPARE](../../../extensibility/debugger/reference/context-compare.md)