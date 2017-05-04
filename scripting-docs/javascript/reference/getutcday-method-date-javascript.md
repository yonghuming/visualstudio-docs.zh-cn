---
title: "getUTCDay 方法 (Date) (JavaScript) | Microsoft Docs"
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
  - "getUTCDay"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Date 对象"
  - "日期，UTC"
  - "UTC 日期，返回"
  - "getUTCDay 方法"
ms.assetid: 2fceb5b0-6f77-4919-82c3-0877fd55bacb
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# getUTCDay 方法 (Date) (JavaScript)
使用协调通用时间 \(UTC\) 获取星期数。  
  
## 语法  
  
```  
  
dateObj.getUTCDay()   
```  
  
#### 参数  
 必需的 `dateObj` 引用是 `Date` 对象。  
  
## 返回值  
 返回一个介于 0（周日）和 6（周六）之间的整数，该整数表示星期数。  
  
## 备注  
 若要使用当地时间获取星期数，请使用 `getDate` 方法。  
  
## 示例  
 下面的示例演示如何使用 `getUTCDay` 方法。  
  
```javascript  
var date = new Date("2/6/2001");  
var day = date.getUTCDay();  
document.write(day);  
  
// Output: 2  
  
```  
  
## 要求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **适用于**：[Date 对象](../../javascript/reference/date-object-javascript.md)  
  
## 请参阅  
 [getDay 方法 \(Date\)](../../javascript/reference/getday-method-date-javascript.md)