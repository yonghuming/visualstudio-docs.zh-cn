---
title: "getMilliseconds 方法 (Date) (JavaScript) | Microsoft Docs"
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
  - "getMilliseconds"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "毫秒"
  - "getMilliseconds 方法"
ms.assetid: 1b512146-1e8a-44a4-89da-6cc5338d15cb
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# getMilliseconds 方法 (Date) (JavaScript)
使用当地时间获取 Date 的毫秒数。  
  
## 语法  
  
```  
  
dateObj.getMilliseconds()   
```  
  
#### 参数  
 必需的 `dateObj` 引用是 `Date` 对象。  
  
## 返回值  
 返回日期的毫秒数。  该值的范围可为 0 到 999。  如果在未指定毫秒数的情况下构造了日期，则返回的值为 0。  
  
## 备注  
 若要获取用协调通用时间 \(UTC\) 表示的毫秒数，请使用 `getUTCMilliseconds` 方法。  
  
## 示例  
 下面的示例演示如何使用 **getMilliseconds** 方法。  
  
```javascript  
var date = new Date("1/1/2001");  
document.write(date.getMilliseconds());  
document.write("<br/>");  
  
date.setMilliseconds(5);  
document.write(date.getMilliseconds());  
// Output:   
// 0  
// 5  
  
```  
  
## 要求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **适用于**：[Date 对象](../../javascript/reference/date-object-javascript.md)  
  
## 请参阅  
 [getUTCMilliseconds 方法 \(Date\)](../../javascript/reference/getutcmilliseconds-method-date-javascript.md)   
 [setMilliseconds 方法 \(Date\)](../../javascript/reference/setmilliseconds-method-date-javascript.md)   
 [setUTCMilliseconds 方法 \(Date\)](../../javascript/reference/setutcmilliseconds-method-date-javascript.md)