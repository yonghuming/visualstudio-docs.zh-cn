---
title: "Number.isSafeInteger（数字）(JavaScript) | Microsoft Docs"
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
ms.assetid: c7ef6ce8-fe71-4e53-be44-4dd440aef21d
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# Number.isSafeInteger（数字）(JavaScript)
返回一个布尔值，该值指示数字可否在 JavaScript 中安全表示。  
  
## 语法  
  
```  
Number.isSafeInteger(numValue)   
```  
  
## 返回值  
 如果数字在 `Number.MIN_SAFE_INTEGER` 和 `Number.MAX_SAFE_INTEGER` 之间（包含），则为 `true`；否则为 `false`。  
  
## 备注  
 JavaScript 中的安全整数是应用任何舍入前的 IEEE\-754 双精度数字。  
  
## 示例  
  
```javascript  
// Returns true  
Number.isSafeInteger(-100)  
Number.isSafeInteger(9007199254740991)  
  
// Returns false  
Number.isSafeInteger(Number.NaN)  
Number.isSafeInteger(Infinity)  
Number.isSafeInteger("100")  
Number.isSafeInteger(9007199254740992);  
```  
  
## 要求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
 **适用于**：[Number 对象](../../javascript/reference/number-object-javascript.md)