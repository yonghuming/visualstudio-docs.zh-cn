---
title: "normalize 方法 (String) (JavaScript) | Microsoft Docs"
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
ms.assetid: d50077c1-b5fa-4e7a-9c9d-dc66cfc423ac
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# normalize 方法 (String) (JavaScript)
返回指定字符串的 Unicode 范式。  
  
## 语法  
  
```  
stringObj.normalize([form]);  
```  
  
#### 参数  
 `stringObj`  
 必需。  要对照测试的字符串对象。  
  
 `form`  
 可选。  Unicode 范式值。  
  
## 返回值  
 指定字符串的 Unicode 范式。  
  
## 异常  
 如果 `form` 是不受支持的值，则会引发 `RangeError`。  
  
## 备注  
 如果 `stringObj` 不是字符串，则它将被转换为字符串（在方法尝试返回该字符串的 Unicode 范式之前）。  
  
 `form` 必须为 Unicode 范式值、“NFC”、“NFD”、“NFKC”或“NFKD”，对应于为 [Unicode 标准附录 \#15](http://www.unicode.org/reports/tr15/)指定的值。  `form` 的默认值为“NFC”。  
  
## 示例  
 下面的代码示例演示 `normalize` 方法的使用。  
  
```javascript  
// ANGSTORM SIGN and LATIN CAPITAL A WITH RING ABOVE is canonically equivalent  
"\u212b".normalize("NFC") === "\u00c5";  
  
// Decomposed, ANGSTOM SIGN is LATIN CAPITAL A followed by COMBINING RING ABOVE  
"\u212b".normalize("NFD") === "\u0041\u030a"  
  
// Normalization Form C will combine the result back into the precombined character  
"\u0041\u030a".normalize("NFC") === "\u00c5"  
  
// LATIN SMALL LIGATURE FI is compatibility equivalent with LATIN SMALL LETTER F followed by  
// LATIN SMALL LETTER I.  
"\ufb01".normalize("NFKD") === "fi";  
  
// Same mapping in NFKC  
"\ufb01".normalize("NFKC") === "fi";  
  
// NFKC will not recombine compatibility characters.  
"fi".normalize("NFKC") === "fi";  
```  
  
## 要求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]