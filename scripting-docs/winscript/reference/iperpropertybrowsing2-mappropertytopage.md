---
title: "IPerPropertyBrowsing2::MapPropertyToPage | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IPerPropertyBrowsing2.MapPropertyToPage
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IPerPropertyBrowsing2::MapPropertyToPage"
ms.assetid: e6418a8e-500b-42e1-9b5a-52e6f7567f99
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IPerPropertyBrowsing2::MapPropertyToPage
返回可用来编辑此属性页的CLSID。  
  
## 语法  
  
```  
HRESULT MapPropertyToPage(  
   DISPID  dispid,  
   CLSID*  pClsidPropPage  
);  
```  
  
#### 参数  
 `dispid`  
 \[in\]时间表属性的标识符相关。  
  
 `pClsidPropPage`  
 \[out\]一个指向标识属性页的CLSID的指针与属性。  如果此方法失败，\*`pClsidPropPage` 设置为CLSID\_NULL。  
  
## 返回值  
 返回有效的 `HRESULT`，通常 `S_OK`。  
  
## 请参阅  
 [IPerPropertyBrowsing2 接口](../../winscript/reference/iperpropertybrowsing2-interface-1.md)