---
title: "getSeconds 方法 (Date) (JavaScript) | Microsoft Docs"
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
  - "getSeconds"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "seconds 方法"
  - "GetSeconds 方法"
ms.assetid: 97b10674-af0b-4681-a846-38f972196501
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# getSeconds 方法 (Date) (JavaScript)
使用当地时间，获取 `Date` 对象中的秒钟，。  
  
## 语法  
  
```  
  
dateObj.getSeconds()   
```  
  
#### 参数  
 必需的 `dateObj` 引用 `Date` 对象。  
  
## 返回值  
 返回介于0和59之间的整数。  ，当时间小于一秒到当前分钟时，返回零。  如果 `Date` 对象创建的，而无需指定时，默认情况下秒钟值为0。  
  
## 备注  
 秒钟值使用协调通用时间获取\(utc\)，使用 `getUTCSeconds` 方法。  
  
## 示例  
 下面的示例演示如何使用 `getSeconds` 方法。  
  
```javascript  
var date = new Date("1/1/2001");  
document.write(date.getSeconds());  
document.write("<br/>");  
  
date.setSeconds(5);  
document.write(date.getSeconds());  
  
// Output:  
// 0  
// 5  
  
```  
  
## 要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **适用于**: [Date 对象](../../javascript/reference/date-object-javascript.md)  
  
## 请参阅  
 [getUTCSeconds 方法 \(Date\)](../../javascript/reference/getutcseconds-method-date-javascript.md)   
 [setSeconds 方法 \(Date\)](../../javascript/reference/setseconds-method-date-javascript.md)   
 [setUTCSeconds 方法 \(Date\)](../../javascript/reference/setutcseconds-method-date-javascript.md)