---
title: "IPerPropertyBrowsing2::SetPredefinedValue | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IPerPropertyBrowsing2.SetPredefinedValue
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IPerPropertyBrowsing2::SetPredefinedValue"
ms.assetid: 3aff5300-c5a4-4d9b-9d47-a75b64014ac4
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IPerPropertyBrowsing2::SetPredefinedValue
设置 `dispID`指定的属性的值。  该预定义的值由标记 `dwCookie.`定位  
  
## 语法  
  
```  
HRESULT SetPredefinedValue(  
   DISPID  dispid,  
   DWORD  dwCookie  
);  
```  
  
#### 参数  
 `dispid`  
 \[in\]时间表预定义值设置属性的标识符。  
  
 `dwCookie`  
 \[in\]标识值的标记设置。  
  
## 返回值  
 返回有效的 `HRESULT`，通常 `S_OK`。  
  
## 请参阅  
 [IPerPropertyBrowsing2 接口](../../winscript/reference/iperpropertybrowsing2-interface-1.md)