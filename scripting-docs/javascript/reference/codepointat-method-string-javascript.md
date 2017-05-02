---
title: "codePointAt 方法（字符串）(JavaScript) | Microsoft Docs"
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
ms.assetid: 7979018f-1be3-4a13-9e8f-c84c7ed35288
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# codePointAt 方法（字符串）(JavaScript)
返回一个 Unicode utf\-16 字符的码位。  
  
## 语法  
  
```  
stringObj.codePointAt(pos);  
```  
  
#### 参数  
 `stringObj`  
 必需。  字符串对象。  
  
 `pos`  
 必需。  字符的位置。  
  
## 备注  
 此方法返回所有 UTF\-16 字符的码位值，包括 astral 码位（具有四个以上的十六进制值的码位）。  
  
 如果 `pos` 小于零 \(0\) 或大于字符串大小，则返回值为 `undefined`。  
  
## 示例  
 下面的示例显示如何使用 `codePointAt` 方法。  
  
```javascript  
var cp1 = "𠮷".codePointAt(0);  
vary cp2 = 'abc'.codePointAt(1);  
  
if(console && console.log) {  
    console.log(cp1);  
    console.log(cp2);}  
  
// Output:  
// 0x20BB7  
// 98  
  
```  
  
## 要求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]