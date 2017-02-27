---
title: "IDebugReference2::SetValueAsString | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugReference2::SetValueAsString"
helpviewer_keywords: 
  - "IDebugReference2::SetValueAsString"
ms.assetid: 9a508ced-fd54-44f5-bb42-ec15c80384d7
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugReference2::SetValueAsString
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

设置引用的值从字符串的。  保留供将来使用。  
  
## 语法  
  
```cpp#  
HRESULT SetValueAsString (   
   LPCOLESTR pszValue,  
   DWORD     dwRadix,  
   DWORD     dwTimeout  
);  
```  
  
```c#  
int SetValueAsString (   
   string pszValue,  
   uint   dwRadix,  
   uint   dwTimeout  
);  
```  
  
#### 参数  
 `pszValue`  
 \[in\] 值作为字符串。  
  
 `dwRadix`  
 \[in\] 格式化任何数值信息基数。  
  
 `dwTimeout`  
 \[in\] 最长时间，以毫秒为单位，在返回等待来自此方法。  使用 `INFINITE` 会无限期地等待。  
  
## 返回值  
 始终返回 `E_NOTIMPL`。  
  
## 请参阅  
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)