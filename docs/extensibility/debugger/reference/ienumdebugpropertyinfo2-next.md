---
title: "IEnumDebugPropertyInfo2::Next | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugPropertyInfo2::Next"
helpviewer_keywords: 
  - "IEnumDebugPropertyInfo2::Next"
ms.assetid: 4eb8c7c3-aadf-4187-abee-c0620308a3eb
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IEnumDebugPropertyInfo2::Next
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

返回下一组枚举中的元素。  
  
## 语法  
  
```cpp#  
HRESULT Next(  
   ULONG                 celt,  
   DEBUG_PROPERTY_INFO** rgelt,  
   ULONG*                pceltFetched  
);  
```  
  
```c#  
int Next(  
   uint                  celt,  
   DEBUG_PROPERTY_INFO[] rgelt,  
   ref uint              pceltFetched  
);  
```  
  
#### 参数  
 `celt`  
 \[in\] 检索的元素的数目。  并指定 `rgelt` 数组的最大大小。  
  
 `rgelt`  
 \[in, out\] 数组将填充的 [DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md) 元素。  
  
 `pceltFetched`  
 \[out\] 返回在 `rgelt`实际上返回的元素的数目。  
  
## 返回值  
 如果成功，则返回 `S_OK`。  ，如果小于元素的请求的数目可能返回，则返回; `S_FALSE` 否则，返回错误代码。  
  
## 请参阅  
 [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)   
 [DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md)