---
title: "Date.now 函数 (JavaScript) | Microsoft Docs"
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
  - "now 方法"
ms.assetid: 41beda89-1a40-4fb1-88b0-38c090af739b
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# Date.now 函数 (JavaScript)
获取当前日期和时间。  
  
## 语法  
  
```  
  
Date.now()  
```  
  
## 返回值  
 1970 年 1 月 1日午夜与当前日期和时间之间的毫秒数。  
  
## 备注  
 [getTime 方法](../../javascript/reference/gettime-method-date-javascript.md)返回 1970 年 1 月 1日与指定日期之间的毫秒数。  
  
 有关如何计算运行时间和比较日期的信息，请参见 [计算日期和时间 \(JavaScript\)](../../javascript/calculating-dates-and-times-javascript.md)。  
  
## 示例  
 下面的示例演示 `now` 方法的用法。  
  
```javascript  
var start = Date.now();  
var response = prompt("What is your name?", "");  
var end = Date.now();  
var elapsed = (end - start) / 1000;  
document.write("You took " + elapsed + " seconds" + " to type: " + response);  
  
// Output:  
// You took <seconds> seconds to type: <name>  
```  
  
## 要求  
 在早于 Internet Explorer 9 的安装版本中不受支持。  但是，在以下文档模式中受到支持：Quirks、Internet Explorer 6 标准、Internet Explorer 7 标准、Internet Explorer 8 标准、Internet Explorer 9 标准和 Internet Explorer 10 标准。  在 [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] 应用程序中也受支持。  
  
## 请参阅  
 [getTime 方法 \(Date\)](../../javascript/reference/gettime-method-date-javascript.md)   
 [Date 对象](../../javascript/reference/date-object-javascript.md)   
 [计算日期和时间 \(JavaScript\)](../../javascript/calculating-dates-and-times-javascript.md)   
 [JavaScript 方法](../../javascript/reference/javascript-methods.md)