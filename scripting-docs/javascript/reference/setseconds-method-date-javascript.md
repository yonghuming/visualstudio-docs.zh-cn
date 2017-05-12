---
title: "setSeconds 方法 (Date) (JavaScript) | Microsoft Docs"
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
  - "setSeconds"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "seconds 方法"
  - "setSeconds 方法"
ms.assetid: 986ffa54-1db6-4af2-ab8b-8353f64f0b57
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# setSeconds 方法 (Date) (JavaScript)
使用当地时间设置 `Date` 对象中的秒钟值。  
  
## 语法  
  
```  
  
dateObj  
.setSeconds(  
numSeconds[, numMilli])   
```  
  
## 参数  
 `dateObj`  
 必需。  任意 `Date` 对象。  
  
 *numSeconds*  
 必需。  一个等于秒值的数值。  
  
 `numMilli`  
 可选。  一个等于毫秒值的数值。  
  
## 备注  
 如果您没有指定可选参数，那么所有采用可选参数的 **set** 方法都将使用相应的 **get** 方法返回的值。  例如，如果未指定 `numMilli` 参数，则 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 将使用从 **getMilliseconds** 方法返回的值。  
  
 若要使用协调通用时间 \(UTC\) 设置秒值，请使用 `setUTCSeconds` 方法。  
  
 如果参数值大于其范围或为负数，则其他存储的值都将得到相应的修改。  例如，如果存储的日期是“Jan 5, 1996 00:00:00”，而且调用了函数 **setSeconds\(150\)**，日期将变为“Jan 5, 1996 00:02:30”。  
  
 `setHours` 方法可用于设置小时、分钟、秒和毫秒。  
  
## 示例  
 下面的示例阐释了 `setSeconds` 方法的用法。  
  
```javascript  
function SetSecondsDemo(nsec){  
   var d = new Date();         //Create Date object.  
   d.setSeconds(nsec);         //Set seconds.  
   var s = "Current setting is ";  
   s += d.toLocaleString();  
   return(s);                  //Return new setting.  
}  
```  
  
## 要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **适用于**：[Date 对象](../../javascript/reference/date-object-javascript.md)  
  
## 请参阅  
 [getSeconds 方法 \(Date\)](../../javascript/reference/getseconds-method-date-javascript.md)   
 [getUTCSeconds 方法 \(Date\)](../../javascript/reference/getutcseconds-method-date-javascript.md)   
 [setUTCSeconds 方法 \(Date\)](../../javascript/reference/setutcseconds-method-date-javascript.md)