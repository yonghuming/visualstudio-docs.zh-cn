---
title: "IPerPropertyBrowsing2::GetPredefinedStrings | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IPerPropertyBrowsing2.GetPredefinedStrings
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IPerPropertyBrowsing2::GetPredefinedStrings"
ms.assetid: d2fa30f7-a566-4dbd-8b47-ffdc00419771
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IPerPropertyBrowsing2::GetPredefinedStrings
允许调用方使用计数的一些表示此属性的可能值的字符串指针填充列表框。  
  
## 语法  
  
```  
HRESULT GetPredefinedStrings(  
   DISPID  dispid,  
   CALPOLESTR*  pCaStrings,  
   CADWORD*  pCaCookies  
);  
```  
  
#### 参数  
 `dispid`  
 \[in\]时间表调用方请求该字符串列表属性的标识符。  
  
 `pCaStrings`  
 \[out\]一个指向包含方法分配的某些元素数和地址字符串指针的调用方分配的，计数的结构数组的指针。  如果方法失败，没有分配内存，因此，结构的内容是未定义的。  
  
 `pCaCookies`  
 \[out\]一个指向包含一个方法分配的数组元素数和地址DWORDs的调用方分配的，计数的结构数组的指针。  如果方法失败，没有分配内存，因此，结构的内容是未定义的。  
  
## 返回值  
 返回有效的 `HRESULT`，通常 `S_OK`。  
  
## 请参阅  
 [IPerPropertyBrowsing2 接口](../../winscript/reference/iperpropertybrowsing2-interface-1.md)