---
title: "getUTCSeconds 方法 (Date) (JavaScript) | Microsoft Docs"
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
  - "getUTCSeconds"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "UTC 时间，返回"
  - "seconds 方法"
  - "getUTCSeconds 方法"
ms.assetid: 2d8ea7dc-79f8-4a9b-b2ab-732db2bcd5fd
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# getUTCSeconds 方法 (Date) (JavaScript)
使用协调通用时间\(utc\)，获取 `Date` 对象中的秒钟。  
  
## 语法  
  
```  
  
dateObj.getUTCSeconds()   
```  
  
#### 参数  
 必需的 `dateObj` 引用 `Date` 对象。  
  
## 返回值  
 返回介于0和59之间的整数。  ，当时间小于一秒到当前分钟时，返回零。  如果 `Date` 对象创建的，而无需指定时，默认情况下UTC的秒钟值为0。  
  
## 备注  
 若要获取用当地时间表示的秒数，请使用 `getSeconds` 方法。  
  
## 示例  
 下面的示例演示如何使用 `getUTCSeconds` 方法。  
  
```javascript  
var date = new Date("1/1/2001");  
document.write(date. getUTCSeconds());  
  
// Output: 0  
  
```  
  
## 要求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Applies To**: [Date 对象](../../javascript/reference/date-object-javascript.md)  
  
## 请参阅  
 [getSeconds 方法 \(Date\)](../../javascript/reference/getseconds-method-date-javascript.md)   
 [setSeconds 方法 \(Date\)](../../javascript/reference/setseconds-method-date-javascript.md)   
 [setUTCSeconds 方法 \(Date\)](../../javascript/reference/setutcseconds-method-date-javascript.md)