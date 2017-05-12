---
title: "IPerPropertyBrowsing2::GetDisplayString | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IPerPropertyBrowsing2.GetDisplayString
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IPerPropertyBrowsing2::GetDisplayString"
ms.assetid: 8f75c6a9-86a9-4e2d-8cb4-74e7b1c0a524
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IPerPropertyBrowsing2::GetDisplayString
具有一个字符不是本身上查看该返回的文本是描述属性的名称，并且可以显示在调用方的用户界面的类型。  
  
## 语法  
  
```  
HRESULT GetDisplayString(  
   DISPID  dispid,  
   BSTR*  pBstr  
);  
```  
  
#### 参数  
 `dispid`  
 \[in\]时间表显示名称请求属性的标识符。  
  
 `pBstr`  
 \[out\]一个指向包含显示名称属性的 `BSTR` 的指针由标识 `dispID`。  
  
## 返回值  
 返回有效的 `HRESULT`，通常 `S_OK`。  
  
## 备注  
 该返回的字符串不是属性的一个合法的值。  它是属性的字符串显示在中。  
  
## 请参阅  
 [IPerPropertyBrowsing2 接口](../../winscript/reference/iperpropertybrowsing2-interface-1.md)