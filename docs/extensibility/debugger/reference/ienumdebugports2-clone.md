---
title: "IEnumDebugPorts2::Clone | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugPorts2::Clone"
helpviewer_keywords: 
  - "IEnumDebugPorts2::Clone"
ms.assetid: d5ce77e8-bb99-409a-98fa-20fe5a0de25e
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IEnumDebugPorts2::Clone
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

返回当前枚举的副本作为单独的对象。  
  
## 语法  
  
```cpp#  
HRESULT Clone(  
   IEnumDebugPorts2** ppEnum  
);  
```  
  
```c#  
int Clone(  
   out IEnumDebugPorts2 ppEnum  
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
 [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)