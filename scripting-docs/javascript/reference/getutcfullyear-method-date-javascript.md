---
title: "getUTCFullYear 方法 (Date) (JavaScript) | Microsoft Docs"
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
  - "getUTCFullYear"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "getUTCFullYear 方法"
  - "Date 对象"
  - "UTCFullYear 方法"
  - "日期，UTC"
  - "UTC 日期，返回"
  - "Full Year 方法"
  - "UTC 日期，获取"
ms.assetid: f11e5363-ef8a-48dd-9d56-4ee7290c7c48
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# getUTCFullYear 方法 (Date) (JavaScript)
使用协调通用时间 \(UTC\) 获取年份。  
  
## 语法  
  
```  
  
dateObj.getUTCFullYear()   
```  
  
#### 参数  
 必需的 `dateObj` 引用是 `Date` 对象。  
  
## 返回值  
 返回由四位数字表示的年份。  在 `Date` 构造函数或 `setFullYear` 中指定为两位数字的年份被假定处于 20 世纪，因此，对于给定的“5\/14\/12”，`getUTCFullYear` 将返回“1912”。  
  
## 备注  
 若要使用当地时间获取年份，请使用 `getFullYear` 方法。  
  
## 示例  
 下面的示例演示如何使用 `getUTCFullYear` 方法。  
  
```javascript  
var date = new Date("1/9/36");  
document.write(date.getUTCFullYear());  
  
// Output: 1936  
  
```  
  
## 要求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **适用于**：[Date 对象](../../javascript/reference/date-object-javascript.md)  
  
## 请参阅  
 [getFullYear 方法 \(Date\)](../../javascript/reference/getfullyear-method-date-javascript.md)   
 [setFullYear 方法 \(Date\)](../../javascript/reference/setfullyear-method-date-javascript.md)   
 [setUTCFullYear 方法 \(Date\)](../../javascript/reference/setutcfullyear-method-date-javascript.md)