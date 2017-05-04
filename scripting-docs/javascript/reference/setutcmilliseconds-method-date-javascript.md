---
title: "setUTCMilliseconds 方法 (Date) (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "setUTCMilliseconds"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "日期, UTC"
  - "毫秒"
  - "setUTCMilliseconds 方法"
  - "UTC 时间, 设置"
ms.assetid: ed8e4486-d4b2-4b73-836b-dd1d3bb991a0
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# setUTCMilliseconds 方法 (Date) (JavaScript)
使用协调通用时间 \(UTC\) 设置 `Date` 对象中的毫秒值。  
  
## 语法  
  
```  
  
dateObj.setUTCMilliseconds(numMilli)   
```  
  
## 参数  
 `dateObj`  
 必需。  任意 `Date` 对象。  
  
 `numMilli`  
 必需。  一个等于毫秒值的数值。  
  
## 备注  
 若要使用当地时间设置毫秒值，请使用 `setMilliseconds` 方法。  
  
 如果 `numMilli` 的值大于 999 或为负，则所存储的秒数（以及分钟、小时等，如有必要）将增加适当的数量。  
  
## 示例  
 下面的示例阐释了 `setUTCMilliseconds` 方法的用法。  
  
```javascript  
function SetUTCMSecDemo(nmsec){     
// Create Date object.  
   var d = new Date();             
// Set UTC milliseconds.  
   d.setUTCMilliseconds(nmsec);    
  
   var s = "Current setting is ";  
   s += d.toUTCString();  
   s += " and " + d.getUTCMilliseconds();  
   s += " milliseconds"  
   return(s);  
}  
```  
  
## 要求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **适用于**：[Date 对象](../../javascript/reference/date-object-javascript.md)  
  
## 请参阅  
 [getMilliseconds 方法 \(Date\)](../../javascript/reference/getmilliseconds-method-date-javascript.md)   
 [getUTCMilliseconds 方法 \(Date\)](../../javascript/reference/getutcmilliseconds-method-date-javascript.md)   
 [setMilliseconds 方法 \(Date\)](../../javascript/reference/setmilliseconds-method-date-javascript.md)