---
title: "String.fromCodePoint 函数 (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 7c4c057b-c67a-4b10-afdd-4f75c7c5988c
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# String.fromCodePoint 函数 (JavaScript)
返回与 Unicode UTF\-16 码位关联的字符串。  
  
## 语法  
  
```  
String.fromCodePoint(...codePoints);  
```  
  
#### 参数  
 `…codePoints`  
 必需。  指定一个或多个 UTF\-16 码位值的 rest 参数。  
  
## 备注  
 如果 `...codePoints` 不是有效的 UTF\-16 码位，此函数将引发 `RangeError` 异常。  
  
## 示例  
 下面的示例演示了如何使用 `fromCodePoint` 函数。  
  
```javascript  
var str1 = String.fromCodePoint(0x20BB7);  
var str2 = String.fromCodePoint(98);  
var str3 = String.fromCodePoint(97, 98, 99);  
  
if(console && console.log) {  
    console.log(str1);  
    console.log(str2);  
    console.log(str3);  
}  
  
// Output:  
// 𠮷  
// b  
// abc  
  
```  
  
## 要求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]