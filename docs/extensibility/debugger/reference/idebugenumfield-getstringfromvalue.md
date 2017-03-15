---
title: "IDebugEnumField::GetStringFromValue | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEnumField::GetStringFromValue"
helpviewer_keywords: 
  - "IDebugEnumField::GetStringFromValue 方法"
ms.assetid: 5f95fd0c-fdce-497f-9f54-2ad8749494e9
caps.latest.revision: 5
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 5
---
# IDebugEnumField::GetStringFromValue
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此方法获取给定的枚举常量的名称其值。  
  
## 语法  
  
```cpp#  
HRESULT GetStringFromValue(  
   ULONGLONG value,  
   BSTR*     pbstrValue  
);  
```  
  
```c#  
int GetStringFromValue(  
   ulong      value,  
   out string pbstrValue  
);  
```  
  
#### 参数  
 `value`  
 \[in\] 值获取枚举常量的名称。  
  
 `pbstrValue`  
 \[out\] 返回枚举常量的名称。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回 `S_FALSE` ，如果该值没有关联的名称，或者返回错误代码。  
  
## 备注  
 如果有多个名称与相同的值，在枚举中定义的名称将返回。  
  
## 请参阅  
 [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)