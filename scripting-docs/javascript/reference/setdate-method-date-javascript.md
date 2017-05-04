---
title: "setDate 方法 (Date) (JavaScript) | Microsoft Docs"
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
  - "setDate"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "setDate 方法"
  - "日期，设置"
ms.assetid: a84b9b01-a6d0-489f-8a13-e7af9e9630b2
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# setDate 方法 (Date) (JavaScript)
使用当地时间设置， `Date` 对象的数值日期的月份值。  
  
## 语法  
  
```  
  
dateObj.setDate(numDate)   
```  
  
## 参数  
 `dateObj`  
 必选。  任意 `Date` 对象。  
  
 `numDate`  
 必选。  一个表示一个月中某一日的数值。  
  
## 备注  
 若要设置日期的月份值使用协调协调的时间\(utc\)，使用 `setUTCDate` 方法。  
  
 如果 `numDate` 的值大于的天数数大于月份，该日期更改为某个月和年。  例如，在中，如果存储的日期是 `setDate(32)` 一月5日， 1996和调用，到1996年二月1日的日期更改。  如果 `numDate` 是负数，则日期回滚到早期版本的月和年。  例如，在中，如果存储的日期是 `setDate(-32)` 一月5日， 1996和调用，到1995年十一月29日的日期更改。  
  
 [setFullYear 方法 \(Date\)](../../javascript/reference/setfullyear-method-date-javascript.md) 可以用于设置年、月和日。  
  
## 示例  
 下面的示例演示如何使用 `setDate` 方法。  
  
```javascript  
var date = new Date("12/15/1990");  
date.setDate(30);  
document.write(date);  
  
// Output (for the PST time zone): Sun Dec 30 00:00:00 PST 1990  
  
```  
  
## 要求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Applies To**: [Date 对象](../../javascript/reference/date-object-javascript.md)  
  
## 请参阅  
 [getDate 方法 \(Date\)](../../javascript/reference/getdate-method-date-javascript.md)   
 [setFullYear 方法 \(Date\)](../../javascript/reference/setfullyear-method-date-javascript.md)   
 [setMonth 方法 \(Date\)](../../javascript/reference/setmonth-method-date-javascript.md)   
 [setUTCDate 方法 \(Date\)](../../javascript/reference/setutcdate-method-date-javascript.md)