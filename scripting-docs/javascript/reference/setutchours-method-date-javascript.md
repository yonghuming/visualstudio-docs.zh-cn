---
title: "setUTCHours 方法 (Date) (JavaScript) | Microsoft Docs"
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
  - "setUTCHours"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "日期, UTC"
  - "setUTCHours 方法"
  - "UTC 时间, 设置"
ms.assetid: 257e36fd-fb06-4a4d-8634-d66a020a1511
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# setUTCHours 方法 (Date) (JavaScript)
使用协调通用时间 \(UTC\) 设置 `Date` 对象中的小时值。  
  
## 语法  
  
```  
  
dateObj.setUTCHours(numHours[, numMin[, numSec[, numMilli]]])   
```  
  
## 参数  
 `dateObj`  
 必需。  任意 `Date` 对象。  
  
 `numHours`  
 必需。  一个等于小时值的数值。  
  
 `numMin`  
 可选。  一个等于分钟值的数值。  如果使用 `numSec` 或 `numMilli`，则必须提供此参数。  
  
 `numSec`  
 可选。  一个等于秒值的数值。  如果使用 `numMilli` 参数，则必须提供此参数。  
  
 `numMilli`  
 可选。  一个等于毫秒值的数值。  
  
## 备注  
 如果您没有指定可选参数，那么所有采用可选参数的 **set** 方法都将使用相应的 **get** 方法返回的值。  例如，如果未指定 `numMin` 参数，则 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 将使用从 `getUTCMinutes` 方法返回的值。  
  
 若要使用当地时间设置小时值，请使用 `setHours` 方法。  
  
 如果参数值大于其范围或为负数，则其他存储的值都将得到相应的修改。  例如，如果所存储的日期是“Jan 5, 1996 00:00:00.00”，并调用了 **setUTCHours\(30\)**，则日期将变为“Jan 6, 1996 06:00:00.00”。  
  
## 示例  
 下面的示例阐释了 `setUTCHours` 方法的用法。  
  
```javascript  
function SetUTCHoursDemo(nhr, nmin, nsec){     
   var d, s;                        // Declare variables.  
   d = new Date();                  // Create Date object.  
   d.setUTCHours(nhr, nmin, nsec);  // Set UTC hours, minutes, seconds.  
   s = "Current setting is " + d.toUTCString()   
   return(s);                       // Return new setting.  
}  
```  
  
## 要求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **适用于**：[Date 对象](../../javascript/reference/date-object-javascript.md)  
  
## 请参阅  
 [getHours 方法 \(Date\)](../../javascript/reference/gethours-method-date-javascript.md)   
 [getUTCHours 方法 \(Date\)](../../javascript/reference/getutchours-method-date-javascript.md)   
 [setHours 方法 \(Date\)](../../javascript/reference/sethours-method-date-javascript.md)