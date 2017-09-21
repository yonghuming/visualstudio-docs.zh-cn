---
title: "IEnumDebugBoundBreakpoints2::GetCount | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugBoundBreakpoints2::GetCount"
helpviewer_keywords: 
  - "IEnumDebugBoundBreakpoints2::GetCount"
ms.assetid: 5a572eeb-beb7-4fc7-8259-792d277069be
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IEnumDebugBoundBreakpoints2::GetCount
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

返回元素数在枚举的。  
  
## 语法  
  
```cpp#  
HRESULT GetCount(  
   ULONG* pcelt  
);  
```  
  
```c#  
int GetCount(  
   out uint pcelt  
);  
```  
  
#### 参数  
 `pcelt`  
 \[out\] 返回元素数在枚举的。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 备注  
 此方法不属于指定习惯的 COM 枚举接口的一部分 `Next`、 `Clone`、 `Skip`并仅 `Reset` 方法需要执行。  
  
## 请参阅  
 [IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md)