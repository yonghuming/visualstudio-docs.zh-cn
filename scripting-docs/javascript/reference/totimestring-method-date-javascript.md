---
title: "toTimeString 方法 (Date) (JavaScript) | Microsoft Docs"
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
  - "toTimeString"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "toTimeString 方法"
ms.assetid: a4a8c0f2-55a9-4e84-94c3-f0a547fb04b5
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# toTimeString 方法 (Date) (JavaScript)
以字符串值形式返回时间。  
  
## 语法  
  
```  
  
objDate. toTimeString( )  
```  
  
## 备注  
 必需的 `objDate` 引用是 `Date` 对象。  
  
 `toTimeString` 方法返回一个包含当前时区时间的字符串值。  
  
## 示例  
 在下面的示例中，将时间设置为 1970 年 1 月 1 日 UTC 午夜后经过的 2000 毫秒，然后将其写出。  
  
```javascript  
var aDate = new Date();  
     aDate.setTime(2000);  
     document.write(aDate.toTimeString());  
  
// Output depends on the time in the current time zone.  
  
```  
  
## 要求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## 请参阅  
 [toDateString 方法 \(Date\)](../../javascript/reference/todatestring-method-date-javascript.md)   
 [toLocaleTimeString 方法 \(Date\)](../../javascript/reference/tolocaletimestring-method-date-javascript.md)