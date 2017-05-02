---
title: "charAt 方法 (String) (JavaScript) | Microsoft Docs"
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
  - "charAt"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "String 对象，返回字符"
  - "charAt 方法"
  - "字符,返回部分"
ms.assetid: 63173e15-17f6-47c5-8f94-98ef1eb04c1a
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# charAt 方法 (String) (JavaScript)
返回指定索引位置处的字符。  
  
## 语法  
  
```  
  
strObj. charAt(index)  
```  
  
## 参数  
 `strObj`  
 必需。  任何 `String` 对象或字符串。  
  
 `index`  
 必需。  所需字符的从零开始的索引。  
  
## 备注  
 `charAt` 方法返回一个字符值，该字符值等于指定 `index` 位置的字符。  一个字符串中的第一个字符位于索引位置 0，第二个字符位于索引位置 1，依此类推。  超出范围的 `index` 返回空字符串。  
  
## 示例  
 下面的示例阐释了 `charAt` 方法的用法：  
  
```javascript  
var str = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";  
document.write(str.charAt(str.length - 1));  
  
// Output: Z  
  
```  
  
## 要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **适用于**：[String 对象](../../javascript/reference/string-object-javascript.md)  
  
## 请参阅  
 [String 对象](../../javascript/reference/string-object-javascript.md)