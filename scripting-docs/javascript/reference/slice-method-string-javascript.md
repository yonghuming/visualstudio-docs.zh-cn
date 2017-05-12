---
title: "slice 方法 (String) (JavaScript) | Microsoft Docs"
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
  - "slice"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "slice 方法"
  - "字符串 [Visual Studio], 返回字符"
ms.assetid: 80cd77a6-3718-492e-8e96-f909d8721d91
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# slice 方法 (String) (JavaScript)
返回字符串的片段。  
  
## 语法  
  
```  
  
stringObj.slice(start, [end])   
```  
  
## 参数  
 `stringObj`  
 必需。  一个 `String` 对象或字符串。  
  
 `start`  
 必需。  指向 `stringObj` 指定部分的开头的索引。  
  
 `end`  
 可选。  指向 `stringObj` 指定部分的结尾的索引。  子字符串包括 `end` 所指示的字符（不包括该字符）前面的字符。  如果没有指定该值，则子字符串将延续到 `stringObj` 的结尾。  
  
## 备注  
 `slice` 方法返回一个 `String` 对象，该对象包含 `stringObj` 的指定部分。  
  
 `slice` 方法一直复制到 `end` 所指示的字符，但是不包括该字符。  
  
 如果 `start` 为负，则将其视为 *length* \+ `start`，此处 *length* 为字符串的长度。  如果 `end` 为负，则会将其视为 *length* \+ `end`。  如果省略 `end`，则将一直复制到 `stringObj` 的结尾。  如果 `end` 出现在 `start` 之前，则不会将任何字符复制到新字符串中。  
  
## 示例  
 在第一个示例中，`slice` 方法返回整个字符串。  在第二个示例中，`slice` 方法返回整个字符串（最后一个字符除外）。  
  
```javascript  
var str1 = "all good boys do fine";  
  
var slice1 = str1.slice(0);  
var slice2 = str1.slice(0,-1);  
var slice3 = str1.slice(4);  
var slice4 = str1.slice(4, 8);  
  
document.write(slice1 + "<br/>");  
document.write(slice2 + "<br/>");  
document.write(slice3 + "<br/>");  
document.write(slice4);  
  
// Output:  
// all good boys do fine  
// all good boys do fin  
// good boys do fine  
// good  
  
```  
  
## 要求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **应用于**：[String 对象](../../javascript/reference/string-object-javascript.md)  
  
## 请参阅  
 [slice 方法（数组）](../../javascript/reference/slice-method-array-javascript.md)