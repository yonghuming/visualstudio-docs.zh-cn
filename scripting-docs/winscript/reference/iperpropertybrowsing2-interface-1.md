---
title: "IPerPropertyBrowsing2 接口 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IPerPropertyBrowsing2
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IPerPropertyBrowsing2 接口"
ms.assetid: 1e50b3f7-cc1c-495a-93c7-3ee03aea0b8a
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IPerPropertyBrowsing2 接口
访问对象提供的属性页的信息。  
  
## Vtable 顺序中的方法  
  
|方法|说明|  
|--------|--------|  
|`GetDisplayString`|返回描述所指定的属性的文本字符串。|  
|`MapPropertyToPage`|返回一个允许用户指定的属性的进程属性页的CLSID。|  
|`GetPredefinedStrings`|返回列表所指定的属性可以接受允许值声明的计数的字符串数组\(`LPOLESTR` 指针\)。|  
|`SetPredefinedValue`|将属性的值设置为标记 `dwCookie.`确定该预定义的值|  
  
## 要求  
 标头:dbgprop.h