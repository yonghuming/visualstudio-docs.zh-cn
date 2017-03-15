---
title: "IEnumDebugFields::Next | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugFields::Next"
helpviewer_keywords: 
  - "IEnumDebugFields::Next 方法"
ms.assetid: 22c177a2-af81-4234-812b-f9b47be245a2
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# IEnumDebugFields::Next
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此方法返回下一组枚举中的元素。  
  
## 语法  
  
```cpp#  
HRESULT Next(  
   ULONG         celt,  
   IDebugField** rgelt,  
   ULONG*        pceltFetched  
);  
```  
  
```c#  
int Next(  
   uint          celt,  
   IDebugField[] rgelt,  
   ref uint      pceltFetched  
);  
```  
  
#### 参数  
 `celt`  
 \[in\] 检索的元素的数目。  并指定 `rgelt` 数组的最大大小。  
  
 `rgelt`  
 \[in, out\] 数组将填充的 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 元素。  
  
 `pceltFetched`  
 \[out\] 返回在 `rgelt`实际上返回的元素的数目。  
  
## 返回值  
 如果成功，则返回 `S_OK`。  ，如果小于元素的请求的数目可能返回，则返回; `S_FALSE` 否则，返回错误代码。  
  
## 请参阅  
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)