---
title: "getUTCMinutes 方法 (Date) (JavaScript) | Microsoft Docs"
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
  - "getUTCMinutes"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "分钟"
  - "UTC 时间，返回"
  - "getUTCMinutes 方法"
ms.assetid: b6d92543-b285-4e46-8f47-bba36e53fabd
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# getUTCMinutes 方法 (Date) (JavaScript)
使用协调通用时间\(utc\)，获取 `Date` 对象的记录。  
  
## 语法  
  
```  
  
dateObj.getUTCMinutes()   
```  
  
#### 参数  
 必需的 `dateObj` 引用 `Date` 对象。  
  
## 返回值  
 返回介于0和59之间的整数。  零小于一分钟返回时是在小时后。  如果 `Date` 对象创建的，而无需指定时，默认情况下UTC分钟值为0。  但是，在其他时区可能是不同的。  
  
## 备注  
 若要获取用当地时间存储的分钟数，请使用 `getMinutes` 方法。  
  
## 示例  
 下面的示例演示 `getUTCMinutes` 方法的用法。  
  
```javascript  
var date = new Date("1/1/2001");  
document.write(date.getUTCMinutes());  
document.write("<br/>");  
  
date.setMinutes(5);  
document.write(date.getUTCMinutes());  
  
// Output:   
// 0  
// 5  
  
```  
  
## 要求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Applies To**: [Date 对象](../../javascript/reference/date-object-javascript.md)  
  
## 请参阅  
 [getMinutes 方法 \(Date\)](../../javascript/reference/getminutes-method-date-javascript.md)   
 [setMinutes 方法 \(Date\)](../../javascript/reference/setminutes-method-date-javascript.md)   
 [setUTCMinutes 方法 \(Date\)](../../javascript/reference/setutcminutes-method-date-javascript.md)