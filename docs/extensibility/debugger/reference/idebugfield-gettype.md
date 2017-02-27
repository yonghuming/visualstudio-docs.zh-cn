---
title: "IDebugField::GetType | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugField::GetType"
helpviewer_keywords: 
  - "IDebugField::GetType 方法"
ms.assetid: b3cdec9f-ef7b-44d0-a775-d17ef7eae968
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugField::GetType
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此方法获取域的类型。  
  
## 语法  
  
```cpp#  
HRESULT GetType(   
   IDebugField** ppType  
);  
```  
  
```c#  
int GetType(  
   out IDebugField ppType  
);  
```  
  
#### 参数  
 `ppType`  
 \[out\] 返回字段类型作为另一 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 对象。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 请参阅  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)