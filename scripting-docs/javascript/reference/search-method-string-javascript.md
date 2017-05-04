---
title: "search 方法 (String) (JavaScript) | Microsoft Docs"
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
  - "search"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "search 方法"
ms.assetid: 1cae0fbc-3319-4327-ba4e-d5fa2c4a9ba0
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# search 方法 (String) (JavaScript)
查找正则表达式搜索中第一个子字符串匹配项。  
  
## 语法  
  
```  
  
stringObj.search(rgExp)   
```  
  
## 参数  
 `stringObj`  
 必需。  对其执行搜索的 `String` 对象或字符串文本。  
  
 `rgExp`  
 必需。  包含正则表达式模式和适用标志的 **Regular Expression** 对象的实例。  
  
## 返回值  
 如果找到一个匹配项，则 **search** 方法将返回一个整数值，该值指示距出现第一个匹配项的字符串的开头的偏移量。  如果没有找到匹配项，则返回 \-1。  
  
## 备注  
 还可以设置 `i` 标志，该标志会导致搜索不区分大小写。  
  
## 示例  
 下面的示例阐释了 **search** 方法的用法。  
  
```javascript  
var src = "is but a Dream within a dream";  
var re = /dream/;  
var pos = src.search(re);  
document.write(pos);  
document.write("<br/>");  
  
re = /dream/i;  
pos = src.search(re);  
document.write(pos);  
  
// Output:   
// 24   
// 9  
  
```  
  
## 要求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **适用于**：[String 对象](../../javascript/reference/string-object-javascript.md)  
  
## 请参阅  
 [exec 方法（正则表达式）](../../javascript/reference/exec-method-regular-expression-javascript.md)   
 [match 方法 \(String\)](../../javascript/reference/match-method-string-javascript.md)   
 [正则表达式对象](../../javascript/reference/regular-expression-object-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/zh-cn/ab0766e1-7037-45ed-aa23-706f58358c0e)   
 [replace 方法 \(String\)](../../javascript/reference/replace-method-string-javascript.md)   
 [test 方法（正则表达式）](../../javascript/reference/test-method-regular-expression-javascript.md)   
 [Regular Expression Programming \(JavaScript\)](http://msdn.microsoft.com/zh-cn/3b62e27c-4f07-4726-a95b-6e841807bfaf)