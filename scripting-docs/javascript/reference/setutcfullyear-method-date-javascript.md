---
title: "setUTCFullYear 方法 (Date) (JavaScript) | Microsoft Docs"
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
  - "setUTCFullYear"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "日期, UTC"
  - "setUTCFullYear 方法"
  - "UTC 日期, 设置"
ms.assetid: e6c51b49-0149-4f9a-aa74-c73c0306f98e
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# setUTCFullYear 方法 (Date) (JavaScript)
使用协调通用时间 \(UTC\) 设置 `Date` 对象中的年份值。  
  
## 语法  
  
```  
  
dateObj.setUTCFullYear(numYear[, numMonth[, numDate]])   
```  
  
## 参数  
 `dateObj`  
 必需。  任意 `Date` 对象。  
  
 `numYear`  
 必需。  一个等于年份的数值。  
  
 `numMonth`  
 可选。  一个等于月份的数值。  一月的值为 0，其他月份值依次递增。  如果提供了 *numDate*，则必须提供此参数。  
  
 *numDate*  
 可选。  一个表示一个月中某一日的数值。  
  
## 备注  
 如果您没有指定可选参数，那么所有采用可选参数的 **set** 方法都将使用相应的 **get** 方法返回的值。  例如，如果未指定 `numMonth` 参数，则 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 将使用从 `getUTCMonth` 方法返回的值。  
  
 此外，如果参数的值大于其取值范围或者是负数，则其他存储的值都将得到相应的修改。  
  
 若要使用当地时间设置年份，请使用 `setFullYear` 方法。  
  
 `Date` 对象中所支持的年份范围大约是 1970 年前后 285,616 年。  
  
## 示例  
 下面的示例阐释了 `setUTCFullYear` 方法的用法。  
  
```javascript  
var dtFirst = new Date();  
dtFirst.setUTCFullYear(2007);  
  
var dtSecond = new Date();  
// 10 is the value for November.   
dtSecond.setUTCFullYear(2008, 10, 3);   
  
document.write (dtFirst.toUTCString());  
document.write ("<br />");  
document.write (dtSecond.toUTCString());  
```  
  
## 要求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **适用于**：[Date 对象](../../javascript/reference/date-object-javascript.md)  
  
## 请参阅  
 [getFullYear 方法 \(Date\)](../../javascript/reference/getfullyear-method-date-javascript.md)   
 [getUTCFullYear 方法 \(Date\)](../../javascript/reference/getutcfullyear-method-date-javascript.md)   
 [setFullYear 方法 \(Date\)](../../javascript/reference/setfullyear-method-date-javascript.md)