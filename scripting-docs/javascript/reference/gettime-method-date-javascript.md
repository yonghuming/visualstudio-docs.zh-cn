---
title: "getTime 方法 (Date) (JavaScript) | Microsoft Docs"
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
  - "getTime"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "GetTime 方法"
  - "时间方法"
ms.assetid: f0da1d4e-337c-497d-9205-093defbc6d3d
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# getTime 方法 (Date) (JavaScript)
获取超时值（以毫秒为单位）。  
  
## 语法  
  
```  
  
dateObj.getTime()   
```  
  
#### 参数  
 必需的 `dateObj` 引用是 `Date` 对象。  
  
## 返回值  
 返回 1970 年 1 月 1 日午夜与 `Date` 对象中的时间值之间的毫秒数。  日期范围在 1970 年 1 月 1 日的午夜前后都有大约 285,616 年。  负数指示 1970 年之前的日期。  
  
## 备注  
 在进行多种日期和时间的换算时，您可能需要定义一些与一天、一小时或一分钟内的毫秒数相等的变量。  例如：  
  
```javascript  
var minute = 1000 * 60;  
var hour = minute * 60;  
var day = hour * 24;  
```  
  
 有关如何使用 `getTime` 方法的更多信息，请参见[计算日期和时间 \(JavaScript\)](../../javascript/calculating-dates-and-times-javascript.md)。  
  
## 示例  
 下面的示例演示如何使用 `getTime` 方法。  
  
```javascript  
var minute = 1000 * 60;  
var hour = minute * 60;  
var day = hour * 24;  
  
date = new Date("1/1/2001");  
var time = date.getTime();  
  
document.write(Math.round(time / day) + " days from 1/1/1970 to 1/1/2001");  
  
// Output: 11323 days from 1/1/1970 to 1/1/2001  
  
```  
  
## 要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **适用于**：[Date 对象](../../javascript/reference/date-object-javascript.md)  
  
## 请参阅  
 [setTime 方法 \(Date\)](../../javascript/reference/settime-method-date-javascript.md)