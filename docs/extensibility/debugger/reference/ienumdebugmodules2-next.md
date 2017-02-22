---
title: "IEnumDebugModules2::Next | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugModules2::Next"
helpviewer_keywords: 
  - "IEnumDebugModules2::Next"
ms.assetid: 46b7ccad-b07b-4ec0-b3ce-13981ffab7e8
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# IEnumDebugModules2::Next
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

返回下一组枚举中的元素。  
  
## 语法  
  
```cpp#  
HRESULT Next(  
   ULONG           celt,  
   IDebugModule2** rgelt,  
   ULONG*          pceltFetched  
);  
```  
  
```c#  
int Next(  
   uint            celt,  
   IDebugModule2[] rgelt,  
   ref uint        pceltFetched  
);  
```  
  
#### 参数  
 `celt`  
 \[in\] 检索的元素的数目。  并指定 `rgelt` 数组的最大大小。  
  
 `rgelt`  
 \[in, out\] 数组将填充的 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) 元素。  
  
 `pceltFetched`  
 \[out\] 返回在 `rgelt`实际上返回的元素的数目。  
  
## 返回值  
 如果成功，则返回 `S_OK`。  ，如果小于元素的请求的数目可能返回，则返回; `S_FALSE` 否则，返回错误代码。  
  
## 请参阅  
 [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)   
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)