---
title: "charCodeAt 方法 (String) (JavaScript) | Microsoft Docs"
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
  - "charCodeAt"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "charCodeAt 方法"
ms.assetid: 5b0290a7-ee4d-4738-a909-c02ef64a2f1a
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# charCodeAt 方法 (String) (JavaScript)
返回指定位置的字符的 Unicode 值。  
  
## 语法  
  
```  
  
strObj. charCodeAt(index)  
```  
  
## 参数  
 `strObj`  
 必需。  任何 `String` 对象或字符串。  
  
 `index`  
 必需。  所需字符的从零开始的索引。  如果指定索引处没有字符，则返回 `NaN`。  
  
## 备注  
  
## 示例  
 下面的示例阐释了 `charCodeAt` 方法的用法。  
  
```javascript  
var str = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";   
document.write(str.charCodeAt(str.length - 1));  
  
// Output: 90   
```  
  
## 要求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## 请参阅  
 [String.fromCharCode 函数](../../javascript/reference/string-fromcharcode-function-javascript.md)