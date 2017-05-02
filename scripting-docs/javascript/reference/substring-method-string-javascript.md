---
title: "substring 方法 (String) (JavaScript) | Microsoft Docs"
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
  - "substring"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "子字符串"
  - "substring 方法"
ms.assetid: 9cf9a005-cbe3-42fd-828b-57a39f54224c
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# substring 方法 (String) (JavaScript)
返回位于 `String` 对象中的指定位置的子字符串。  
  
## 语法  
  
```  
  
      strVariable. substring(start [, end])  
"String Literal".substring(start [, end])   
```  
  
## 参数  
 `start`  
 必需。  从 0 开始的索引整数，指示子字符串的起始位置。  
  
 `end`  
 可选。  从 0 开始的索引整数，指示子字符串的结束位置。  子字符串包括 `end` 所指示的字符（不包括该字符）前面的字符。  
  
 如果省略 `end`，将返回从 `start` 一直到原字符串末尾的字符。  
  
## 备注  
 `substring` 方法将返回一个字符串，该字符串包含从 `start` 直到 `end`（不包含该参数）的子字符串。  
  
 **substring** 方法使用 `start` 和 `end` 两者中的较小值作为子字符串的起始点。  例如，strvar.substring\(0, 3**\)** 和 strvar.substring\(3, 0\) 将返回相同的子字符串。  
  
 如果 `start` 或 `end` 为 `NaN` 或负数，那么它将被替换为 0。  
  
 子字符串的长度等于 `start` 和 `end` 之差的绝对值。  例如，在 strvar.substring\(0, 3\) 和 strvar.substring\(3, 0\) 中，返回的子字符串的长度为 3。  
  
## 示例  
 下面的示例阐释了 **substring** 方法的用法。  
  
```javascript  
var s = "The quick brown fox jumps over the lazy dog.";  
var ss = s.substring(10, 15);  
document.write(ss);  
  
// Output:  
// brown  
  
```  
  
## 要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 请参阅  
 [substr 方法 \(String\)](../../javascript/reference/substr-method-string-javascript.md)