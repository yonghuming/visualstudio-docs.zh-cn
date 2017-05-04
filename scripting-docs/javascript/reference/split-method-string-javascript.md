---
title: "split 方法 (String) (JavaScript) | Microsoft Docs"
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
  - "split"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "split 方法"
ms.assetid: 7f093336-c887-4efb-b91f-819b6d18a181
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# split 方法 (String) (JavaScript)
使用指定的分隔符将一个字符串拆分为多个子字符串，并将其以数组形式返回。  
  
## 语法  
  
```  
  
stringObj.split([separator[, limit]])  
```  
  
## 参数  
 `stringObj`  
 必选。  要拆分的 `String` 对象或字符串。  **split** 方法将不修改此对象。  
  
 `separator`  
 可选。  一个字符串或**正则表达式**对象，标识用于分隔字符串的一个或多个字符。  如果忽略该参数，则将返回包含整个字符串的单元素数组。  
  
 `limit`  
 可选。  一个用于限制数组中返回的元素数量的值。  
  
## 返回值  
 **split** 方法的结果是在 `stringObj` 中出现 `separator` 的每个位置分隔字符串后产生的字符串数组。  `separator` 将不作为任何数组元素的一部分返回。  
  
## 示例  
 下面的示例阐释了 **split** 方法的用法。  
  
```javascript  
var s = "The quick brown fox jumps over the lazy dog.";  
var ss = s.split(" ");  
for (var i in ss) {  
    document.write(ss[i]);  
    document.write("<br/>");  
}  
  
// Output:   
// The  
// quick  
// brown  
// fox  
// jumps  
// over  
// the  
// lazy  
// dog.  
  
```  
  
## 要求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **适用对象**：[String 对象](../../javascript/reference/string-object-javascript.md)  
  
## 请参阅  
 [concat 方法（字符串）](../../javascript/reference/concat-method-string-javascript.md)   
 [RegExp 对象](../../javascript/reference/regexp-object-javascript.md)   
 [正则表达式对象](../../javascript/reference/regular-expression-object-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/zh-cn/ab0766e1-7037-45ed-aa23-706f58358c0e)   
 [滚动、平移和缩放示例应用程序](http://code.msdn.microsoft.com/ie/Scrolling-panning-and-6834aaf9)