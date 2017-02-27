---
title: "IDebugField::Equal | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugField::Equal"
helpviewer_keywords: 
  - "IDebugField::Equal 方法"
ms.assetid: 75369fe6-ddd3-497d-80d1-2488e6100e9f
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugField::Equal
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此方法此字段与相等的指定字段比较。  
  
## 语法  
  
```cpp#  
HRESULT Equal(   
   IDebugField* pField  
);  
```  
  
```c#  
int Equal(  
   IDebugField pField  
);  
```  
  
#### 参数  
 `pField`  
 \[in\] 比较的字段都添加到一个。  
  
## 返回值  
 如果字段是相同的，返回 `S_OK`。  如果字段是不同的，否则返回 `S_FALSE.` ，返回错误代码。  
  
## 请参阅  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)