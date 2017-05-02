---
title: "setUTCMonth 方法 (Date) (JavaScript) | Microsoft Docs"
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
  - "setUTCMonth"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "日期, UTC"
  - "Month 方法"
  - "setUTCMonth 方法"
  - "UTC 日期, 设置"
ms.assetid: cdac5f64-c4fd-44cc-ba3a-9a8dd3dd3fad
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# setUTCMonth 方法 (Date) (JavaScript)
使用协调通用时间 \(UTC\) 设置 `Date` 对象中的月份值。  
  
## 语法  
  
```  
  
dateObj.setUTCMonth(numMonth[, dateVal])   
```  
  
## 参数  
 `dateObj`  
 必需。  任意 `Date` 对象。  
  
 `numMonth`  
 必需。  一个等于月份的数值。  一月的值为 0，其他月份值依次递增。  
  
 `dateVal`  
 可选。  一个表示一个月中某一日的数值。  如果没有提供这个值，将使用调用 `getUTCDate` 方法得到的值。  
  
## 备注  
 若要使用当地时间设置月份值，请使用 `setMonth` 方法。  
  
 如果 `numMonth` 的值大于 11（月份 0 代表一月）或者是负数，那么所存储的年份也将相应地得到增加或减少。  例如，如果所存储的日期是“Jan 5, 1996 00:00:00.00”，并且调用了 **setUTCMonth\(14\)**，则该日期就变为“Mar 5, 1997 00:00:00.00”。  
  
 **setUTCFullYear** 方法可用于设置年、月、日。  
  
## 示例  
 下面的示例阐释了 `setUTCMonth` 方法的用法。  
  
```javascript  
function SetUTCMonthDemo(newmonth){  
   var d, s;                       // Declare variables.  
   d = new Date();                 // Create Date object.  
   d.setUTCMonth(newmonth);        // Set UTC month.  
   s = "Current setting is ";  
   s += d.toUTCString();   
   return(s);                      // Return new setting.  
}  
```  
  
## 要求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **适用于**：[Date 对象](../../javascript/reference/date-object-javascript.md)  
  
## 请参阅  
 [getMonth 方法 \(Date\)](../../javascript/reference/getmonth-method-date-javascript.md)   
 [getUTCMonth 方法 \(Date\)](../../javascript/reference/getutcmonth-method-date-javascript.md)   
 [setMonth 方法 \(Date\)](../../javascript/reference/setmonth-method-date-javascript.md)