---
title: "lastIndexOf 方法 (String) (JavaScript) | Microsoft Docs"
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
  - "lastIndexOf"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "lastIndexOf 方法，字符串"
  - "字符串，lastIndexOf 方法"
ms.assetid: 1ed36ccd-0f0b-4f16-be45-0567207670af
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# lastIndexOf 方法 (String) (JavaScript)
返回字符串中子字符串最后出现的位置。  
  
## 语法  
  
```  
  
strObj.lastIndexOf(substring[, startindex])  
```  
  
## 参数  
 `strObj`  
 必需。  一个 `String` 对象或字符串。  
  
 `substring`  
 必需。  要搜索的子字符串。  
  
 `startindex`  
 可选。  开始搜索的索引位置。  若省略此参数，则搜索将从字符串的结尾开始。  
  
## 备注  
 **lastIndexOf** 方法返回一个整数值，该整数值指示 `String` 对象内子字符串的开始位置。  如果未找到子字符串，则返回 \-1。  
  
 如果 `startindex` 为负，则 `startindex` 将被视为零。  如果它大于最大字符位置索引，则将它视为可能的最大索引。  
  
 搜索将从字符串中的最后一个字符开始执行。  否则，该方法和 **indexOf** 相同。  
  
 下面的示例阐释了 **lastIndexOf** 方法的用法。  
  
```javascript  
var str = "time, time";  
  
var s = "";  
s += "time is at position " + str.lastIndexOf("time");  
s += "<br />";  
s += "abc is at position " + str.lastIndexOf("abc");  
  
document.write(s);  
  
// Output:  
// time is at position 6  
// abc is at position -1  
```  
  
## 要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **适用于**：[String 对象](../../javascript/reference/string-object-javascript.md)  
  
## 请参阅  
 [indexOf 方法 \(String\)](../../javascript/reference/indexof-method-string-javascript.md)