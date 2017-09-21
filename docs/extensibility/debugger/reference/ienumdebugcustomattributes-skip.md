---
title: "IEnumDebugCustomAttributes::Skip | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumCustomAttributes::Skip"
helpviewer_keywords: 
  - "IEnumDebugCustomAttributes::Skip"
ms.assetid: 54c72e23-cd4c-4746-935c-abea8057dd1b
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IEnumDebugCustomAttributes::Skip
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

跳过自定义特性指定数目的枚举序列的。  
  
## 语法  
  
```cpp#  
HRESULT Skip (   
   ULONG celt  
);  
```  
  
```c#  
int Skip(  
   uint celt  
);  
```  
  
#### 参数  
 `celt`  
 \[in\] 跳过的元素数。  
  
## 返回值  
 如果成功，则返回 `S_OK`。  返回 `S_FALSE` ，如果 `celt` 比其余元素的数量大于;否则，返回错误代码。  
  
## 备注  
 如果 `celt` 比剩余的元素数指定值，枚举设置为末尾，并 `S_FALSE` 返回。  
  
## 请参阅  
 [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)