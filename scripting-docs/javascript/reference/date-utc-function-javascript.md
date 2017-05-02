---
title: "Date.UTC 函数 (JavaScript) | Microsoft Docs"
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
  - "UTC"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "UTC 函数 [JavaScript]"
  - "UTC 日期，返回"
  - "Date.UTC 函数 [JavaScript]"
ms.assetid: c0d67ce1-a47e-4dfd-bbf4-21619c406a0f
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# Date.UTC 函数 (JavaScript)
返回协调通用时间 \(UTC\)（或 GMT）1970 年 1 月 1 日午夜与所指定的日期之间相差的毫秒数。  
  
## 语法  
  
```  
Date.UTC(year, month, day[, hours[, minutes[, seconds[,ms]]]])   
```  
  
## 参数  
 `year`  
 必需。  为了确保跨世纪日期的精确性，需要指定完整的年份。  如果 `year` 处于 0 到 99 之间，则 `year` 就被假定为 1900 \+ `year`。  
  
 `month`  
 必需。  月份，用从 0 到 11 的整数表示（1 月至 12 月）。  
  
 `day`  
 必需。  日期，用从 1 到 31 的整数表示。  
  
 `hours`  
 可选。  如果提供了 `minutes`，则必须提供此参数。  一个指定小时的，从 0 到 23 的整数（午夜到 11pm）。  
  
 `minutes`  
 可选。  如果提供了 `seconds`，则必须提供此参数。  一个指定分钟的，从 0 到 59 的整数。  
  
 `seconds`  
 可选。  如果提供了 `milliseconds`，则必须提供此参数。  一个指定秒的，从 0 到 59 的整数。  
  
 `ms`  
 可选。  一个指定毫秒的，从 0 到 999 的整数。  
  
## 备注  
 `Date.UTC` 函数返回从 UTC 1970 年 1 月 1 日午夜到所提供日期之间的毫秒数。  此返回值可用在 `setTime` 方法和 `Date` 对象构造函数中。  如果参数值大于其范围或为负数，则其他存储的值都将得到相应的修改。  例如，如果指定 150 秒，则 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 将该数字重新定义为 2 分 30 秒。  
  
 `Date.UTC` 函数和接受日期的 `Date` 对象构造函数之间的差别在于：`Date.UTC` 函数采用 UTC，而 `Date` 对象构造函数采用当地时间。  
  
## 示例  
 下面的示例阐释了 `Date.UTC` 函数的用法。  
  
```javascript  
// Determine the milliseconds per day.  
 var MinMilli = 1000 * 60;  
var HrMilli = MinMilli * 60;  
var DyMilli = HrMilli * 24;  
  
var date = new Date("June 1, 1990");  
var year = date.getFullYear();  
var month = date.getMonth();  
var day = date.getDay();  
  
var newDay = new Date("January 16, 2020");  
var yeartoday = newDay.getUTCFullYear();  
var monthtoday = newDay.getUTCMonth();  
var dayofmonthtoday = newDay.getUTCDate();  
  
// Get the milliseconds since 1/1/1970 UTC.  
var t1 = Date.UTC(year, month - 1, day)  
var t2 = Date.UTC(yeartoday, monthtoday, dayofmonthtoday);  
  
// Determine the difference in days.  
var days = (t2 - t1) / DyMilli;  
  
document.write(days);  
// Output: 10848  
```  
  
## 要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 请参阅  
 [setTime 方法 \(Date\)](../../javascript/reference/settime-method-date-javascript.md)