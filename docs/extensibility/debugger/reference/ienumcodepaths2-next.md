---
title: "IEnumCodePaths2::Next | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumCodePaths2::Next"
helpviewer_keywords: 
  - "IEnumCodePaths2::Next"
ms.assetid: c7a8fe97-2abc-4cee-8aef-64f1daa93b5c
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# IEnumCodePaths2::Next
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

返回下一组枚举中的元素。  
  
## 语法  
  
```cpp#  
HRESULT Next(  
   ULONG       celt,  
   CODE_PATH** rgelt,  
   ULONG*      pceltFetched  
);  
```  
  
```c#  
int Next(  
   uint        celt,  
   CODE_PATH[] rgelt,  
   ref uint    pceltFetched  
);  
```  
  
#### 参数  
 `celt`  
 \[in\] 检索的元素的数目。  并指定 `rgelt` 数组的最大大小。  
  
 `rgelt`  
 \[in, out\] 数组将填充的 [CODE\_PATH](../../../extensibility/debugger/reference/code-path.md) 元素。  
  
 `pceltFetched`  
 \[out\] 返回在 `rgelt`实际上返回的元素的数目。  
  
## 返回值  
 如果成功，则返回 `S_OK`。  ，如果小于元素的请求的数目可能返回，则返回; `S_FALSE` 否则，返回错误代码。  
  
## 请参阅  
 [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)   
 [CODE\_PATH](../../../extensibility/debugger/reference/code-path.md)