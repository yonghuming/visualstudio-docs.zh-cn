---
title: "Object.getOwnPropertySymbols 函数 (JavaScript) | Microsoft Docs"
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
ms.assetid: 68dd69b9-5a33-44c2-ba5f-21a4ae6c0879
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# Object.getOwnPropertySymbols 函数 (JavaScript)
返回对象的自有符号属性。  对象的自有符号属性是指直接在此对象上定义、而非从对象的原型继承的属性。  
  
## 语法  
  
```  
Object.getOwnPropertySymbols(object);  
```  
  
#### 参数  
 `object`  
 必需。  包含自有符号的对象。  
  
## 返回值  
 包含对象的自有符号的数组。  
  
## 备注  
 需要使用 `Object.getOwnPropertySymbols` 来获取对象的符号属性。  `Object.getOwnPropertyNames` 不会返回符号属性。  
  
## 示例  
 下面的代码示例演示如何获取对象的符号属性。  
  
```javascript  
var obj = {};  
var key = Symbol('description');  
  
obj[key] = 'data';  
  
var symbols = Object.getOwnPropertySymbols(obj);  
  
console.log(s[0].toString());  
  
// Output:  
// undefined  
// Symbol(description)  
```  
  
## 要求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]