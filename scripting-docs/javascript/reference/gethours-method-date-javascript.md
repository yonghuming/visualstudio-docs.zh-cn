---
title: "getHours 方法 (Date) (JavaScript) | Microsoft Docs"
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
  - "getHours"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Date 对象"
  - "GetHours 方法"
  - "Hours 方法"
ms.assetid: c3936496-a213-4d15-b308-d53926ed310c
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# getHours 方法 (Date) (JavaScript)
使用当地时间获取日期的小时值。  
  
## 语法  
  
```  
  
dateObj.getHours()   
```  
  
#### 参数  
 必需的 `dateObj` 引用是 `Date` 对象。  
  
## 返回值  
 一个介于 0 和 23 之间的整数，指示自午夜起经过的小时数。  如果时间在 1:00:00 am 之前，则返回 0。  如果在未指定时间的情况下创建了 `Date` 对象，则默认情况下小时值为 0。  
  
## 备注  
 若要使用协调通用时间 \(UTC\) 获取小时值，请使用 `getUTCHours` 方法。  
  
## 示例  
 下面的示例演示如何使用 `getHours` 方法。  
  
```javascript  
var date = new Date("1/1/2001");  
document.write(date.getHours());  
document.write("<br/>");  
  
date.setTime(50000000);  
document.write(date.getHours());  
  
// Output:  
// 0   
// 5  
  
```  
  
## 要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **适用于**：[Date 对象](../../javascript/reference/date-object-javascript.md)  
  
## 请参阅  
 [getUTCHours 方法 \(Date\)](../../javascript/reference/getutchours-method-date-javascript.md)   
 [setHours 方法 \(Date\)](../../javascript/reference/sethours-method-date-javascript.md)   
 [setUTCHours 方法 \(Date\)](../../javascript/reference/setutchours-method-date-javascript.md)