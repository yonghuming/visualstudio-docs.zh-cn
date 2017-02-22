---
title: "IEnumDebugBoundBreakpoints2::Clone | Microsoft Docs"
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
  - "IEnumDebugBoundBreakpoints2::Clone"
helpviewer_keywords: 
  - "IEnumDebugBoundBreakpoints2::Clone"
ms.assetid: c6ce01a2-7da3-46ec-9837-855042fa7244
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IEnumDebugBoundBreakpoints2::Clone
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

返回当前枚举的副本作为单独的对象。  
  
## 语法  
  
```cpp#  
HRESULT Clone(  
   IEnumDebugBoundBreakpoints2** ppEnum  
);  
```  
  
```c#  
int Clone(  
   out IEnumDebugBoundBreakpoints2 ppEnum  
);  
```  
  
#### 参数  
 `ppEnum`  
 \[out\] 返回此枚举的副本作为单独的对象。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 备注  
 ，此方法调用后，枚举的副本的状态和原始相同的。  但是，复制的值和原始的状态是独立的，并可以单独进行更改。  
  
## 请参阅  
 [IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md)