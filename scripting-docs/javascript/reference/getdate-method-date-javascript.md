---
title: "getDate 方法 (Date) (JavaScript) | Microsoft Docs"
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
  - "getDate"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Date 对象"
  - "日期，返回月中的第几日"
  - "getDate 方法"
ms.assetid: 67e7f07c-dd46-4b42-82d6-e53e4bd33703
caps.latest.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 20
---
# getDate 方法 (Date) (JavaScript)
使用当地时间获取一个月第几天的值。  
  
## 语法  
  
```  
  
dateObj.getDate()   
```  
  
#### 参数  
 必需的 `dateObj` 引用是 `Date` 对象。  
  
## 返回值  
 一个介于 1 和 31 之间的整数，表示一个月第几天。  
  
## 备注  
 若要使用协调通用时间 \(UTC\) 获取一个月的第几天的值，请使用 `getUTCDate` 方法。  
  
## 示例  
 下面的示例阐释了 `getDate` 方法的用法。  
  
```javascript  
var date = new Date("Jan 01, 2001");  
var str = "Today's date is: ";  
   str += (date.getMonth() + 1) + "/";  
   str += date.getDate() + "/";  
   str += date.getFullYear();  
document.write(str);  
  
// Output: Today's date is: 1/1/2001  
  
```  
  
## 要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **适用于**：[Date 对象](../../javascript/reference/date-object-javascript.md)  
  
## 请参阅  
 [getUTCDate 方法 \(Date\)](../../javascript/reference/getutcdate-method-date-javascript.md)   
 [setDate 方法 \(Date\)](../../javascript/reference/setdate-method-date-javascript.md)   
 [setUTCDate 方法 \(Date\)](../../javascript/reference/setutcdate-method-date-javascript.md)