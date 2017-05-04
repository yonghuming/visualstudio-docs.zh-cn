---
title: "Date.parse 函数 (JavaScript) | Microsoft Docs"
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
  - "parse"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Date.parse 函数 [JavaScript]"
  - "parse 函数 [JavaScript]"
ms.assetid: ed737e50-6398-4462-8779-2af3c03f8325
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# Date.parse 函数 (JavaScript)
分析一个包含日期的字符串，并返回该日期与 1970 年 1 月 1 日午夜之间相差的毫秒数。  
  
## 语法  
  
```  
Date.parse(dateVal)   
```  
  
## 备注  
 必需的 `dateVal` 参数是包含日期的字符串或从 ActiveX 对象或其他对象检索到的 VT\_DATE 值。  有关 `Date.parse` 函数可解析的日期字符串的信息，请参阅 [日期和时间字符串](../../javascript/date-and-time-strings-javascript.md)。  
  
 `Date.parse` 函数返回一个整数值，此整数表示 `dateVal` 中所提供的日期与 1970 年 1 月 1 日午夜之间相差的毫秒数。  
  
## 示例  
 下面的示例说明了 `Date.parse` 函数的用法。  
  
```javascript  
var dateString = "November 1, 1997 10:15 AM";  
var mSec = Date.parse(dateString);  
document.write(mSec);  
// Output: 878404500000  
```  
  
## 示例  
 以下示例返回提供的日期与 1\/1\/1970 之间的差异。  
  
```javascript  
var minMilli = 1000 * 60;  
var hrMilli = minMilli * 60;  
var dyMilli = hrMilli * 24;  
  
var testDate = new Date("June 1, 1990");  
var ms = Date.parse(testDate);  
var days = Math.round(ms / dyMilli);  
  
var dateStr = "";  
dateStr += "There are " + days + " days ";  
dateStr += "between 01/01/1970 and " + testDate;  
document.write(dateStr);  
  
// Output: There are 7456 days between 01/01/1970 and Fri Jun 1 00:00:00 PDT 1990  
  
```  
  
## 要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 请参阅  
 [getDate 方法 \(Date\)](../../javascript/reference/getdate-method-date-javascript.md)