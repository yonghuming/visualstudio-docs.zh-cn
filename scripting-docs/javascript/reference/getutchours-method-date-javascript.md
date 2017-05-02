---
title: "getUTCHours 方法 (Date) (JavaScript) | Microsoft Docs"
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
  - "getUTCHours"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "小时"
  - "UTC 时间，返回"
  - "getUTCHours 方法"
ms.assetid: 7c9825dd-4b3a-4614-8e09-f40df123b630
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# getUTCHours 方法 (Date) (JavaScript)
使用协调通用时间\(utc\)，获取在 `Date` 对象中的小时值。  
  
## 语法  
  
```  
  
dateObj.getUTCHours()   
```  
  
#### 参数  
 必需的 `dateObj` 引用 `Date` 对象。  
  
## 返回值  
 返回以指示小时数0和23之间的整数自午夜。  ，如果时间为1:00之前，零返回: 00 AM。  如果 `Date` 对象创建的，而无需指定时，默认情况下为0小时UTC时间。  这个可能是非零在其他时区。  
  
## 备注  
 若要使用当地时间获取自午夜之后经过的小时数，请使用 `getHours` 方法。  
  
## 示例  
 下面的示例演示 `getUTCHours` 方法的用法。  
  
```javascript  
var date = new Date("1/1/2001");  
document.write(date.getUTCHours());  
document.write("<br/>");  
  
var date2 = new Date("1/1/2001 11:22:33");  
document.write(datee.getUTCHours());  
  
// Output (in the PST time zone):  
// 8  
// 19  
  
```  
  
## 要求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Applies To**: [Date 对象](../../javascript/reference/date-object-javascript.md)  
  
## 请参阅  
 [getHours 方法 \(Date\)](../../javascript/reference/gethours-method-date-javascript.md)   
 [setHours 方法 \(Date\)](../../javascript/reference/sethours-method-date-javascript.md)   
 [setUTCHours 方法 \(Date\)](../../javascript/reference/setutchours-method-date-javascript.md)