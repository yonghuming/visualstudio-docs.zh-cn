---
title: "getUTCMonth 方法 (Date) (JavaScript) | Microsoft Docs"
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
  - "getUTCMonth"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "日期，UTC"
  - "UTC 日期，返回"
  - "Month 方法"
  - "getUTCMonth 方法"
ms.assetid: eabae139-4da0-4e4a-a4cb-608e6375fc9e
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# getUTCMonth 方法 (Date) (JavaScript)
使用协调通用时间\(utc\)，获取 `Date` 对象中的月份。  
  
## 语法  
  
```  
  
dateObj.getUTCMonth()   
```  
  
#### 参数  
 必需的 `dateObj` 引用 `Date` 对象。  
  
## 返回值  
 返回在 0（一月）和 11（十二月）之间的整数。  
  
## 备注  
 若要获取用当地时间表示的月份，请使用 **getMonth** 方法。  
  
## 示例  
 下面的示例演示如何使用 `getUTCMonth` 方法。  
  
```javascript  
var date = new Date("2/2/2002");  
document.write(date.getUTCMonth());  
  
// Output: 1  
  
```  
  
## 要求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Applies To**: [Date 对象](../../javascript/reference/date-object-javascript.md)  
  
## 请参阅  
 [getMonth 方法 \(Date\)](../../javascript/reference/getmonth-method-date-javascript.md)   
 [setMonth 方法 \(Date\)](../../javascript/reference/setmonth-method-date-javascript.md)   
 [setUTCMonth 方法 \(Date\)](../../javascript/reference/setutcmonth-method-date-javascript.md)