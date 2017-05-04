---
title: "concat 方法 (String) (JavaScript) | Microsoft Docs"
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
  - "concat"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "concat 方法 (String)"
  - "Concat 方法"
ms.assetid: 5d28ebb2-d534-4179-9297-a4c821ee9f24
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# concat 方法 (String) (JavaScript)
返回由两个或两个以上的字符串串联而成的字符串。  
  
## 语法  
  
```  
  
string1. concat([string2[, string3[, . . . [, stringN]]]])  
```  
  
## 参数  
 `string1`  
 必需。  所有其他指定的字符串要连接到的 `String` 对象或字符串。  
  
 `string2,. . ., stringN`  
 可选。  要追加到 `string1` 的末尾的字符串。  
  
## 备注  
 `concat` 方法的结果等同于：`result` \= `string1` \+ `string2` \+ `string3` \+ `stringN`。  源字符串中或结果字符串中的值的变化都不会影响另一个字符串中的值。  如果有不是字符串的参数，则它们在连接到 `string1` 之前将首先被转换为字符串。  
  
## 示例  
 下面的示例阐释了 `concat` 方法用于字符串时的用法：  
  
```javascript  
var str1 = "ABCD"  
var str2 = "EFGH";  
var str3 = "1234";  
var str4 = "5678";  
document.write(str1.concat(str2, str3, str4));  
  
// Output: "ABCDEFGH12345678"  
  
```  
  
## 要求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **适用于**：[String 对象](../../javascript/reference/string-object-javascript.md)  
  
## 请参阅  
 [加法运算符 \(\+\)](../../javascript/reference/addition-operator-decrement-javascript.md)