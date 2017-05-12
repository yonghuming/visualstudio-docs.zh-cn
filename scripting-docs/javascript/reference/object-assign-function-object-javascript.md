---
title: "Object.assign 函数（对象）(JavaScript) | Microsoft Docs"
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
ms.assetid: 2dd6b312-dcd3-414e-8d53-088c6341c46d
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Object.assign 函数（对象）(JavaScript)
将来自一个或多个源对象中的值复制到一个目标对象。  
  
## 语法  
  
```  
Object.assign(target, ...sources );  
```  
  
#### 参数  
 `target`  
 必需。  可枚举属性复制到的对象。  
  
 `...sources`  
 必需。  从其中复制可枚举属性的对象。  
  
## 异常  
 如果存在分配错误，此函数将引发 `TypeError`，这将终止复制操作。  如果目标属性不可写，则将引发 `TypeError`。  
  
## 备注  
 此函数返回目标对象。  仅*可枚举自有*属性从源对象复制到目标对象。  可使用此函数合并或克隆对象。  
  
 `null` 或 `undefined` 源被视为空对象一样对待，不会对目标对象产生任何影响。  
  
## 示例  
 下面的代码示例演示如何使用 `Object.assign` 合并对象。  
  
```javascript  
var first = { name: "Bob" };  
var last = { lastName: "Smith" };  
  
var person = Object.assign(first, last);  
console.log(person);  
  
// Output:  
// { name: "Bob", lastName: "Smith" }   
```  
  
## 示例  
 下面的代码示例演示如何使用 `Object.assign` 克隆对象。  
  
```javascript  
var obj = { person: "Bob Smith"};  
var clone = Object.assign({}, obj);  
```  
  
## 要求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]