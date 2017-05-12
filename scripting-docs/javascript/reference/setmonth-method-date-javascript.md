---
title: "setMonth 方法 (Date) (JavaScript) | Microsoft Docs"
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
  - "setMonth"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Month 方法"
  - "setMonth 方法"
ms.assetid: 4f5be295-d536-46c0-b3a4-ad06457efe82
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# setMonth 方法 (Date) (JavaScript)
使用当地时间设置 `Date` 对象中的月份值。  
  
## 语法  
  
```  
  
dateObj. setMonth(numMonth[, dateVal])   
```  
  
## 参数  
 `dateObj`  
 必需。  任意 `Date` 对象。  
  
 `numMonth`  
 必需。  一个等于月份的数值。  一月的值为 0，其他月份值依次递增。  
  
 `dateVal`  
 可选。  一个表示一个月中某一日的数值。  如果没有提供这一值，将使用调用 `getDate` 方法得到的值。  
  
## 备注  
 若要使用协调通用时间 \(UTC\) 设置月值，请使用 `setUTCMonth` 方法。  
  
 如果 `numMonth` 的值大于 11（数值 0 表示一月）或为负，那么所存储的年份将相应地得到修改。  例如，如果所存储的日期是“Jan 5, 1996”，并且调用了 **setMonth\(14\)**，则该日期将变为“Mar 5, 1997”。  
  
 **setFullYear** 方法可用于设置年、月、日。  
  
## 示例  
 下面的示例阐释了 `setMonth` 方法的用法。  
  
```javascript  
date = new Date('1/1/1990');  
date.setMonth(14);  
document.write(date);  
  
// Output: Fri Mar 1 00:00:00 PST 1991  
// Note that the time zone corresponds to the time zone on the local computer.  
  
```  
  
## 要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **适用于**：[Date 对象](../../javascript/reference/date-object-javascript.md)  
  
## 请参阅  
 [getMonth 方法 \(Date\)](../../javascript/reference/getmonth-method-date-javascript.md)   
 [getUTCMonth 方法 \(Date\)](../../javascript/reference/getutcmonth-method-date-javascript.md)   
 [setUTCMonth 方法 \(Date\)](../../javascript/reference/setutcmonth-method-date-javascript.md)