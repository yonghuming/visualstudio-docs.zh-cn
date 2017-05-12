---
title: "getMonth 方法 (Date) (JavaScript) | Microsoft Docs"
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
  - "getMonth"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Date 对象"
  - "日期，月份值"
  - "Month 方法"
  - "GetMonth 方法"
ms.assetid: c20dd8ba-1d78-42f1-8717-ed3dfd2362dd
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# getMonth 方法 (Date) (JavaScript)
使用当地时间获取月份。  
  
## 语法  
  
```  
  
dateObj.getMonth()   
```  
  
#### 参数  
 必需的 `dateObj` 引用是 `Date` 对象。  
  
## 返回值  
 `getMonth` 方法返回一个介于 0（1 月）和 11（12 月）之间的整数。  对于使用“Jan 5, 1996”构造的 `Date`，`getMonth` 返回 0。  
  
## 备注  
 若要使用协调通用时间 \(UTC\) 获取月值，请使用 `getUTCMonth` 方法。  
  
## 示例  
 下面的示例演示如何使用 `getMonth` 方法。  
  
```javascript  
var date = new Date("1/1/2001");  
document.write(date.getMonth());  
  
// Output: 0  
```  
  
## 要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **适用于**：[Date 对象](../../javascript/reference/date-object-javascript.md)  
  
## 请参阅  
 [getUTCMonth 方法 \(Date\)](../../javascript/reference/getutcmonth-method-date-javascript.md)   
 [setMonth 方法 \(Date\)](../../javascript/reference/setmonth-method-date-javascript.md)   
 [setUTCMonth 方法 \(Date\)](../../javascript/reference/setutcmonth-method-date-javascript.md)