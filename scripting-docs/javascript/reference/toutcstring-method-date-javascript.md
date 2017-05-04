---
title: "toUTCString 方法 (Date) (JavaScript) | Microsoft Docs"
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
  - "toUTCString"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "toUTCString 方法"
  - "UTC 日期, 转换为字符串"
ms.assetid: eb0983ed-7884-42fa-a2cc-de92b3111207
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# toUTCString 方法 (Date) (JavaScript)
返回使用协调通用时间 \(UTC\) 转换为字符串的日期。  
  
## 语法  
  
```  
  
dateObj.toUTCString()   
```  
  
## 备注  
 必需的 `dateObj` 引用是任何 `Date` 对象。  
  
 `toUTCString` 方法返回一个 `String` 对象，此对象中包含了 UTC 惯例格式的日期，以一种简便、易读的形式表示。  
  
## 示例  
 下面的示例阐释了 `toUTCString` 方法的用法。  
  
```javascript  
function toUTCStrDemo(){  
   var d, s;                   //Declare variables.  
   d = new Date();             //Create Date object.  
   s = "Current setting is ";  
   s += d.toUTCString();       //Convert to UTC string.  
   return(s);                  //Return UTC string.  
}  
```  
  
## 要求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **适用于**：[Date 对象](../../javascript/reference/date-object-javascript.md)  
  
## 请参阅  
 [toGMTString 方法 \(Date\)](../../javascript/reference/togmtstring-method-date-javascript.md)