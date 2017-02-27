---
title: "IDebugProperty2::SetValueAsString | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProperty2::SetValueAsString"
helpviewer_keywords: 
  - "IDebugProperty2::SetValueAsString"
ms.assetid: 9e6a5054-41b7-4223-b509-b93689d366a5
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProperty2::SetValueAsString
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

设置属性的值从特定字符串的。  
  
## 语法  
  
```cpp#  
HRESULT SetValueAsString (   
   LPCOLESTR pszValue,  
   UINT      nRadix,  
   DWORD     dwTimeout  
);  
```  
  
```c#  
int SetValueAsString (   
   string pszValue,  
   uint   nRadix,  
   uint   dwTimeout  
);  
```  
  
#### 参数  
 `pszValue`  
 \[in\] 包含值的字符串将被设置为。  
  
 `nRadix`  
 \[in\] 用于解释任何数字信息基数。  这可能是尝试的 0 自动确定基数。  
  
 `dwTimeout`  
 \[in\] 以毫秒为单位指定最长时间，因此，在返回等待来自此方法。  使用 `INFINITE` 会无限期地等待。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则返回错误代码。  下表显示其他可能的值。  
  
|值|说明|  
|-------|--------|  
|`E_SETVALUE_VALUE_CANNOT_BE_SET`|该字符串不能转换为属性值，或属性值不能设置。|  
|`E_SETVALUE_VALUE_IS_READONLY`|该属性是只读的。|  
  
## 请参阅  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)