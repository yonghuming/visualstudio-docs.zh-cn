---
title: "getUTCDate 方法 (Date) (JavaScript) | Microsoft Docs"
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
  - "getUTCDate"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Date 对象"
  - "日期，UTC"
  - "UTC 日期，返回"
  - "getUTCDate 方法"
ms.assetid: 9e4c763f-c94c-44c9-9684-cb632d75b62e
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# getUTCDate 方法 (Date) (JavaScript)
使用协调通用时间 \(UTC\) 获取一个月第几天的值。  
  
## 语法  
  
```  
  
dateObj.getUTCDate()   
```  
  
#### 参数  
 必需的 `dateObj` 引用是 `Date` 对象。  
  
## 返回值  
 返回一个介于 1 和 31 之间的整数，表示一个月第几天。  
  
## 备注  
 若要使用当地时间获取一个月第几天，请使用 `getDate` 方法。  
  
## 示例  
 下面的示例演示如何使用 `getUTCDate` 方法。  
  
```javascript  
var date = new Date("1/23/2001");  
document.write(date.getUTCDate());  
  
// Output: 23  
  
```  
  
## 要求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **适用于**：[Date 对象](../../javascript/reference/date-object-javascript.md)  
  
## 请参阅  
 [getDate 方法 \(Date\)](../../javascript/reference/getdate-method-date-javascript.md)   
 [setDate 方法 \(Date\)](../../javascript/reference/setdate-method-date-javascript.md)   
 [setUTCDate 方法 \(Date\)](../../javascript/reference/setutcdate-method-date-javascript.md)