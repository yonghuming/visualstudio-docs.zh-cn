---
title: "indexOf 方法 (String) (JavaScript) | Microsoft Docs"
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
  - "indexOf"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "IndexOf 方法, string"
  - "string, IndexOf 方法"
ms.assetid: a17372fa-669b-471b-9240-46927a265152
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# indexOf 方法 (String) (JavaScript)
返回子字符串首次出现的位置。  
  
## 语法  
  
```  
  
strObj. indexOf(subString[, startIndex])  
```  
  
## 参数  
 `strObj`  
 必选。  一个 `String` 对象或字符串。  
  
 `subString`  
 必选。  要在字符串中搜索的子字符串  
  
 `startIndex`  
 可选。  用于开始搜索 `String` 对象的索引。  如果省略此参数，则搜索将从字符串的起始处开始。  
  
## 备注  
 **indexOf** 方法返回 `String` 对象中的子字符串的开头。  如果未找到子字符串，则返回 \-1。  
  
 如果 `startindex` 为负，则 `startindex` 将被视为零。  如果它大于最大索引，则将其视为最大索引。  
  
 搜索将从左向右执行。  否则，此方法与 **lastIndexOf** 相同。  
  
## 示例  
 下面的示例阐释 **indexOf** 方法的用法。  
  
```javascript  
var str = "original equipment manufacturer";  
  
var s = "equip is at position " + str.indexOf("equip");  
s += "<br />";  
s += "abc is at position " + str.indexOf("abc");  
  
document.write(s);  
  
// Output:  
// equip is at position 9  
// abc is at position -1  
```  
  
## 要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **适用对象**：[String 对象](../../javascript/reference/string-object-javascript.md)  
  
## 请参阅  
 [lastIndexOf 方法（字符串）](../../javascript/reference/lastindexof-method-string-javascript.md)   
 [滚动、平移和缩放示例应用程序](http://code.msdn.microsoft.com/ie/Scrolling-panning-and-6834aaf9)