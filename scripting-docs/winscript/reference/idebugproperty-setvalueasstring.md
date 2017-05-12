---
title: "IDebugProperty::SetValueAsString | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugProperty.SetValueAsString
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugProperty::SetValueAsString"
ms.assetid: cad8d7b2-19a5-4a29-9000-cafdecdc238b
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugProperty::SetValueAsString
设置属性的值从特定字符串的。  
  
## 语法  
  
```  
HRESULT SetValueAsString (  
   LPCOLESTR pszValue,  
   UINT nRadix,  
);  
```  
  
#### 参数  
 `pszValue`  
 \[in\]要设置的值。  
  
 `nRadix`  
 \[in\]用于解释任何数字信息基数。  
  
## 返回值  
 返回有效的 `HRESULT`，通常 `S_OK`。  
  
## 请参阅  
 [IDebugProperty 接口](../../winscript/reference/idebugproperty-interface.md)