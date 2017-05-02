---
title: "setUTCSeconds 方法 (Date) (JavaScript) | Microsoft Docs"
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
  - "setUTCSeconds"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "日期, UTC"
  - "seconds 方法"
  - "setUTCSeconds 方法"
  - "UTC 时间, 设置"
ms.assetid: e035e282-b39d-4d1d-8771-c17542fd6493
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# setUTCSeconds 方法 (Date) (JavaScript)
使用协调通用时间 \(UTC\) 设置 `Date` 对象中的秒钟值。  
  
## 语法  
  
```  
  
dateObj.setUTCSeconds(numSeconds[, numMilli])   
```  
  
## 参数  
 `dateObj`  
 必需。  任意 `Date` 对象。  
  
 *numSeconds*  
 必需。  一个等于秒值的数值。  
  
 `numMilli`  
 可选。  一个等于毫秒值的数值。  
  
## 备注  
 如果您没有指定可选参数，那么所有采用可选参数的 **set** 方法都将使用相应的 **get** 方法返回的值。  例如，如果未指定 `numMilli` 参数，则 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 将使用从 `getUTCMilliseconds` 方法返回的值。  
  
 若要使用当地时间设置秒值，请使用 `setSeconds` 方法。  
  
 如果参数值大于其范围或为负数，则其他存储的值都将得到相应的修改。  例如，如果存储的日期是“Jan 5, 1996 00:00:00.00”，而且调用了函数 **setSeconds\(150\)**，日期将变为“Jan 5, 1996 00:02:30.00”。  
  
 **setUTCHours** 方法可用于设置小时、分钟、秒和毫秒。  
  
## 示例  
 下面的示例阐释了 `setUTCSeconds` 方法的用法。  
  
```javascript  
function SetUTCSecondsDemo(nsec){  
// Create Date object.  
    var d = new Date();       
// Set UTC seconds.  
    d.setUTCSeconds(nsec);    
    var s = "Current setting is ";  
    s += d.toUTCString();  
// Return new setting.  
    return(s);                
}  
```  
  
## 要求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **适用于**：[Date 对象](../../javascript/reference/date-object-javascript.md)  
  
## 请参阅  
 [getSeconds 方法 \(Date\)](../../javascript/reference/getseconds-method-date-javascript.md)   
 [getUTCSeconds 方法 \(Date\)](../../javascript/reference/getutcseconds-method-date-javascript.md)   
 [setSeconds 方法 \(Date\)](../../javascript/reference/setseconds-method-date-javascript.md)