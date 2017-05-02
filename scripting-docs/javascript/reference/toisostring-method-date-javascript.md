---
title: "toISOString 方法 (Date) (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "toISOString 方法 [JavaScript]"
ms.assetid: 58577d8f-3ae8-4887-8687-26233ea79ff6
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# toISOString 方法 (Date) (JavaScript)
以字符串值的形式返回采用 ISO 格式的日期。  
  
## 语法  
  
```javascript  
  
objDate.toISOString()  
```  
  
## 返回值  
 采用国际标准化组织 \(ISO\) 格式的日期的字符串表示形式。  
  
## 异常  
 如果 `objDate` 不包含有效日期，则将引发 `RangeError` 异常。  
  
## 备注  
 ISO 格式是 ISO 8601 格式的简化形式。  有关更多信息，请参见[日期和时间字符串](../../javascript/date-and-time-strings-javascript.md)。  
  
 时区始终为 UTC，在输出中由后缀 Z 表示。  
  
## 示例  
 下面的示例阐释了 `toISOString` 方法的用法。  
  
```javascript  
var dt = new Date("30 July 2010 15:05 UTC");  
document.write(dt.toISOString());  
document.write("<br />");  
document.write(dt.toUTCString());  
  
// Output:  
//  2010-07-30T15:05:00.000Z  
//  Fri, 30 Jul 2010 15:05:00 UTC  
  
```  
  
## 要求  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## 请参阅  
 [Date 对象](../../javascript/reference/date-object-javascript.md)   
 [日期和时间字符串](../../javascript/date-and-time-strings-javascript.md)