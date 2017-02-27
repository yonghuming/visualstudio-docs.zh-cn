---
title: "IEnumDebugErrorBreakpoints2::Next | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugErrorBreakpoints2::Next"
helpviewer_keywords: 
  - "IEnumDebugErrorBreakpoints2::Next"
ms.assetid: 6a3dee11-5267-4d77-9e28-6a38413ba70b
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IEnumDebugErrorBreakpoints2::Next
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

返回下一组枚举中的元素。  
  
## 语法  
  
```cpp#  
HRESULT Next(  
   ULONG                    celt,  
   IDebugErrorBreakpoint2** rgelt,  
   ULONG*                   pceltFetched  
);  
```  
  
```c#  
int Next(  
   uint                     celt,  
   IDebugErrorBreakpoint2[] rgelt,  
   ref uint                 pceltFetched  
);  
```  
  
#### 参数  
 `celt`  
 \[in\] 检索的元素的数目。  并指定 `rgelt` 数组的最大大小。  
  
 `rgelt`  
 \[in, out\] 数组将填充的 [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) 元素。  
  
 `pceltFetched`  
 \[out\] 返回在 `rgelt`实际上返回的元素的数目。  
  
## 返回值  
 如果成功，则返回 `S_OK`。  ，如果小于元素的请求的数目可能返回，则返回; `S_FALSE` 否则，返回错误代码。  
  
## 请参阅  
 [IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)   
 [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)