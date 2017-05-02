---
title: "substr 方法 (String) (JavaScript) | Microsoft Docs"
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
  - "substr"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "substr 方法"
ms.assetid: f12541c1-2623-482e-941d-2e22bc3c4a4a
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# substr 方法 (String) (JavaScript)
获取一个从指定位置开始并具有指定长度的子字符串。  
  
## 语法  
  
```  
  
stringvar.substr(start [, length ])   
```  
  
## 参数  
 `stringvar`  
 必需。  从中提取子字符串的字符串文本或 `String` 对象。  
  
 `start`  
 必需。  所需的子字符串的起始位置。  字符串中第一个字符的索引为 0。  
  
 `length`  
 可选。  返回的子字符串中包含的字符数。  
  
## 备注  
 如果 `length` 为 0 或负数，则返回一个空字符串。  如果没有指定该参数，则子字符串将延续到 `stringvar` 的结尾。  
  
## 示例  
 下面的示例阐释了 `substr` 方法的用法。  
  
```javascript  
var s = "The quick brown fox jumps over the lazy dog.";  
var ss = s.substr(10, 5);    
document.write("[" + ss + "] <br>");  
  
ss = s.substr(10);  
document.write("[" + ss + "] <br>");  
  
ss = s.substr(10, -5);  
document.write("[" + ss + "] <br>");  
  
// Output:  
// [brown]   
// [brown fox jumps over the lazy dog.]   
// []  
```  
  
## 要求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **适用于**：[String 对象](../../javascript/reference/string-object-javascript.md)  
  
## 请参阅  
 [substring 方法 \(String\)](../../javascript/reference/substring-method-string-javascript.md)