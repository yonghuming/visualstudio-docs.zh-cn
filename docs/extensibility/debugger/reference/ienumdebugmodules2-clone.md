---
title: "IEnumDebugModules2::Clone | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugModules2::Clone"
helpviewer_keywords: 
  - "IEnumDebugModules2::Clone"
ms.assetid: fd6d3abc-20d9-4f6f-9c8e-5bd29f68d47d
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IEnumDebugModules2::Clone
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

返回当前枚举的副本作为单独的对象。  
  
## 语法  
  
```cpp#  
HRESULT Clone(  
   IEnumDebugModules2** ppEnum  
);  
```  
  
```c#  
int Clone(  
   out IEnumDebugModules2 ppEnum  
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
 [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)