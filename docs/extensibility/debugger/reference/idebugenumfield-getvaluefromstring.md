---
title: "IDebugEnumField::GetValueFromString | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEnumField::GetValueFromString"
helpviewer_keywords: 
  - "IDebugEnumField::GetValueFromString 方法"
ms.assetid: 1ef8ac5e-a3e0-4078-b876-7f5615aedcbb
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# IDebugEnumField::GetValueFromString
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此方法返回值与枚举常量的名称。  
  
## 语法  
  
```cpp#  
HRESULT GetValueFromString(  
   LPCOLESTR  pszValue,  
   ULONGLONG* pvalue  
);  
```  
  
```c#  
int GetValueFromString(  
   string    pszValue,  
   out ulong pValue  
);  
```  
  
#### 参数  
 `pszValue`  
 \[in\] 指定名称的字符串获取值。  请注意 C\+\+ 中，这是宽字符字符串。  
  
 `pValue`  
 \[out\] 返回一个关联的数值。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回 `S_FALSE`，因此，如果该名称不是枚举的一部分，或错误代码。  
  
## 备注  
 此方法区分大小写。  如果不区分大小写的搜索需要的 \(例如，在一种语言 \(如名称不区分大小写\) 的 Visual Basic 中，使用 [GetValueFromStringCaseInsensitive](../Topic/IDebugEnumField::GetValueFromStringCaseInsensitive.md)。  
  
## 请参阅  
 [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)   
 [GetValueFromStringCaseInsensitive](../Topic/IDebugEnumField::GetValueFromStringCaseInsensitive.md)