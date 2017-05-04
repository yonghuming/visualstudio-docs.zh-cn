---
title: "getUTCMilliseconds 方法 (Date) (JavaScript) | Microsoft Docs"
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
  - "getUTCMilliseconds"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "毫秒"
  - "UTC 时间，返回"
  - "getUTCMilliseconds 方法"
ms.assetid: 7491d387-7b6a-40df-89e5-55c64795ef70
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# getUTCMilliseconds 方法 (Date) (JavaScript)
使用协调通用时间\(utc\)，获取 `Date` 对象中的毫秒。  
  
## 语法  
  
```  
  
dateObj.getUTCMilliseconds()   
```  
  
#### 参数  
 必需的 `dateObj` 引用 `Date` 对象。  
  
## 返回值  
 返回可以从0\-999范围中的毫秒值。  
  
## 备注  
 获取毫秒数。本地时间，使用 `getMilliseconds` 方法。  
  
## 示例  
 下面的示例演示 `getUTCMilliseconds` 方法的用法。  
  
```javascript  
var date = new Date("1/1/2001");  
document.write(date.getUTCMilliseconds());  
document.write("<br/>");  
  
date.setMilliseconds(34);  
document.writedate.getUTCMilliseconds());  
  
// Output:  
// 0   
// 34   
```  
  
## 要求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Applies To**: [Date 对象](../../javascript/reference/date-object-javascript.md)  
  
## 请参阅  
 [getMilliseconds 方法 \(Date\)](../../javascript/reference/getmilliseconds-method-date-javascript.md)   
 [setMilliseconds 方法 \(Date\)](../../javascript/reference/setmilliseconds-method-date-javascript.md)   
 [setUTCMilliseconds 方法 \(Date\)](../../javascript/reference/setutcmilliseconds-method-date-javascript.md)