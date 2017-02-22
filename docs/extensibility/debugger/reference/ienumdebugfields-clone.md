---
title: "IEnumDebugFields::Clone | Microsoft Docs"
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
  - "IEnumDebugFields::Clone"
helpviewer_keywords: 
  - "IEnumDebugFields::Clone 方法"
ms.assetid: 7ec265a8-696f-45ce-a2a2-0a83e96fee1b
caps.latest.revision: 5
caps.handback.revision: 5
ms.author: "gregvanl"
manager: "ghogen"
---
# IEnumDebugFields::Clone
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此方法返回当前枚举的副本作为单独的对象。  
  
## 语法  
  
```cpp#  
HRESULT Clone(  
   IEnumDebugFields** ppEnum  
);  
```  
  
```c#  
int Clone(  
   out IEnumDebugFields ppEnum  
);  
```  
  
#### 参数  
 `ppEnum`  
 \[out\] 返回此枚举的副本作为单独的对象。  
  
## 属性值\/返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 备注  
 ，此方法调用后，枚举的副本的状态和原始相同的。  但是，复制的值和原始的状态是独立的，并可以单独进行更改。  
  
## 请参阅  
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)