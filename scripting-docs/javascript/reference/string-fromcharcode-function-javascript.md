---
title: "String.fromCharCode 函数 (JavaScript) | Microsoft Docs"
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
  - "fromCharCode"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "fromCharCodeAt 方法"
  - "字符，来自 Unicode"
ms.assetid: f64120c1-23a7-48ca-8d1c-db3e8856cab4
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# String.fromCharCode 函数 (JavaScript)
从一些 Unicode 字符值中返回一个字符串。  
  
## 语法  
  
```  
String.fromCharCode([code1[, code2[, ...[, codeN]]]])   
```  
  
## 参数  
 `String`  
 必需。  `String` 对象。  
  
 `code1`, ..., `codeN`  
 可选。  要转换为字符串的一系列 Unicode 字符值。  如果不提供参数，则结果为空字符串。  
  
## 备注  
 只能对 `String` 对象而非字符串实例调用此函数。  
  
 以下示例展示如何使用此方法：  
  
```javascript  
var test = String.fromCharCode(112, 108, 97, 105, 110);  
document.write(test);  
  
// Output: plain  
  
```  
  
## 要求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## 请参阅  
 [charCodeAt 方法 \(String\)](../../javascript/reference/charcodeat-method-string-javascript.md)