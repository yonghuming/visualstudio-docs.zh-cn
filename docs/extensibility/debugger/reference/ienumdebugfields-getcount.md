---
title: "IEnumDebugFields::GetCount | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugFields::GetCount"
helpviewer_keywords: 
  - "IEnumDebugFields::GetCount 方法"
ms.assetid: 3f471b40-4db3-49f7-b504-58b2476eef74
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# IEnumDebugFields::GetCount
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此方法返回元素数在枚举的。  
  
## 语法  
  
```cpp#  
HRESULT GetCount(  
   [out] ULONG* pcelt  
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
 此方法不是仅指定接下来，克隆、跳过并重置需要实现习惯的 COM 枚举接口的一部分。  
  
## 请参阅  
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)