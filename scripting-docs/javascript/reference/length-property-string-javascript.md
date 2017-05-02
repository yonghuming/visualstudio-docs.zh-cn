---
title: "length 属性 (String) (JavaScript) | Microsoft Docs"
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
  - "length Property"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "字符串 [Visual Studio]，长度"
  - "Length 属性"
  - "length 属性 (String)"
ms.assetid: 7dbd4a0e-c24e-4561-9b5b-e75e649a10a4
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# length 属性 (String) (JavaScript)
返回 `String` 对象的长度。  
  
> [!WARNING]
>  JavaScript 字符串是不可变的，因此无法修改字符串的长度。  
  
## 语法  
  
```  
  
      strVariable.length  
"String Literal".length   
```  
  
## 备注  
 `length` 属性包含一个整数，该整数指示 `String` 对象中的字符数。  `String` 对象中的最后一个字符的索引为 `length` \- 1。  
  
## 示例  
 下面的代码演示如何使用 `length`。  JavaScript 字符串是不可变的，无法就地进行修改。  但是，您可以编写数组的反转字符串，然后调用包含空字符的 `join`，这将生成不包含分隔符的字符串。  
  
```javascript  
var str = "every good boy does fine";  
        var start = 0;  
        var end = str.length - 1;  
        var tmp = "";  
        var arr = new Array(end);  
  
        while (end >= 0) {  
            arr[start++] = str.charAt(end--);  
        }  
  
// Join the elements of the array with a   
        var str2 = arr.join('');  
        document.write(str2);  
  
// Output: enif seod yob doog yreve  
  
```  
  
## 要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]