---
title: "setFullYear 方法 (Date) (JavaScript) | Microsoft Docs"
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
  - "setFullYear"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Year 方法"
  - "setFullYear 方法"
  - "日期，设置"
ms.assetid: 635e4f5a-0210-4c01-8152-b0da4146f6ff
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# setFullYear 方法 (Date) (JavaScript)
使用当地时间设置， `Date` 对象中的年份。  
  
## 语法  
  
```  
  
dateObj.setFullYear(numYear[, numMonth[, numDate]])   
```  
  
## 参数  
 `dateObj`  
 必选。  任意 `Date` 对象。  
  
 `numYear`  
 必选。  一个数值中。  
  
 `numMonth`  
 可选。  一个从零开始的数值表示月\(0年一月，十一月到12月\)。  必须指定 `numDate` 是否指定。  
  
 `numDate`  
 可选。  一个数值等于在日。  
  
## 备注  
 如果未指定可选参数，那么所有采用可选参数的 set 方法都将使用相应的 get 方法返回的数值。  例如，因此，如果 `numMonth` 参数是可选的，但是，未指定，则将从 **getMonth** 方法返回的 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 使用。  
  
 此外，在中，如果参数的值大于其日历大小大于还是为负，则该日期向前和向后滚动根据需要。  
  
 若要设置中使用协调协调的时间\(utc\)，使用 `setUTCFullYear` 方法。  
  
 在1970年前后，在date对象支持的年份的大小约为285,616。  
  
## 示例  
 下面的示例阐释了 `setFullYear` 方法的用法：  
  
```javascript  
var date1 = new Date("1/1/2001");  
date1.setFullYear(2007);  
  
var date2 = new Date("1/1/2001");  
date2.setFullYear(2008, 10, 3);   
  
document.write (date1.toLocaleString());  
document.write ("<br />");  
document.write (date2.toLocaleString());  
  
// Output:  
// Monday, January 01, 2007 12:00:00 AM  
// Monday, November 03, 2008 12:00:00 AM  
  
```  
  
## 要求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Applies To**: [Date 对象](../../javascript/reference/date-object-javascript.md)  
  
## 请参阅  
 [getFullYear 方法 \(Date\)](../../javascript/reference/getfullyear-method-date-javascript.md)   
 [getUTCFullYear 方法 \(Date\)](../../javascript/reference/getutcfullyear-method-date-javascript.md)   
 [setUTCFullYear 方法 \(Date\)](../../javascript/reference/setutcfullyear-method-date-javascript.md)