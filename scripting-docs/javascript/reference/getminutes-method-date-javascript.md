---
title: "getMinutes 方法 (Date) (JavaScript) | Microsoft Docs"
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
  - "getMinutes"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "GetMinutes 方法"
  - "minutes 方法"
ms.assetid: d4139b5d-04e1-474c-9a83-e9d40597243a
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# getMinutes 方法 (Date) (JavaScript)
使用当地时间获取 `Date` 对象的分钟值。  
  
## 语法  
  
```  
  
dateObj.getMinutes()   
```  
  
#### 参数  
 必需的 `dateObj` 引用是 `Date` 对象。  
  
## 返回值  
 返回一个介于 0 和 59 之间的整数。  在当前一小时内的时间小于一分钟时返回 0。  如果在未指定时间的情况下创建了 `Date` 对象，则默认情况下分钟值为 0。  
  
## 备注  
 若要使用协调通用时间 \(UTC\) 获取分钟值，请使用 `getUTCMinutes` 方法。  
  
## 示例  
 下面的示例演示如何使用 `getMinutes` 方法。  
  
```javascript  
var date = new Date("1/1/2001");  
document.write(date.getMinutes());  
document.write("<br/>");  
  
date.setMinutes(5);  
document.write(date.getMinutes());  
  
// Output:  
// 0  
// 5  
  
```  
  
## 要求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **适用于**：[Date 对象](../../javascript/reference/date-object-javascript.md)  
  
## 请参阅  
 [getUTCMinutes 方法 \(Date\)](../../javascript/reference/getutcminutes-method-date-javascript.md)   
 [setMinutes 方法 \(Date\)](../../javascript/reference/setminutes-method-date-javascript.md)   
 [setUTCMinutes 方法 \(Date\)](../../javascript/reference/setutcminutes-method-date-javascript.md)