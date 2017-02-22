---
title: "IDebugBinder3::GetTypeArguments | Microsoft Docs"
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
  - "IDebugBinder3::GetTypeArguments"
helpviewer_keywords: 
  - "IDebugBinder3::GetTypeArguments 方法"
ms.assetid: fa0c37a7-327f-463e-9a9d-bb3f534584cb
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugBinder3::GetTypeArguments
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此方法检索类型参数列表与此对象关联的。  
  
## 语法  
  
```cpp  
HRESULT GetTypeArguments(  
   UINT          skip,  
   UINT          count,  
   IDebugField** ppFields,  
   UINT*         pFetched  
);  
```  
  
```c#  
int GetTypeArguments(  
   uint          skip,  
   uint          count,  
   IDebugField[] ppFields,  
   out uint      pFetched  
);  
```  
  
#### 参数  
 `skip`  
 \[in\]跳过的字段数。获取参数之前键入。  
  
 `count`  
 \[in\] 参数的数字字段返回 \(还指定 `ppFields` 数组的大小\)。  
  
 `ppFields`  
 \[in, out\] 将填充的数组字段返回此方法。  
  
 `pFetched`  
 \[out\] \(可选\) 参数类型的数字字段实际返回。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 备注  
 参数类型的数量可能需要获取与 [GetTypeArgumentCount](../Topic/IDebugBinder3::GetTypeArgumentCount.md)。  
  
## 请参阅  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)   
 [GetTypeArgumentCount](../Topic/IDebugBinder3::GetTypeArgumentCount.md)