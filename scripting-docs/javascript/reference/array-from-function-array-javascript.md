---
title: "Array.from 函数（数组）(JavaScript) | Microsoft Docs"
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
ms.assetid: 1bf59a99-f860-4c4d-b4c6-d5f1f946a490
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Array.from 函数（数组）(JavaScript)
从类似数组的对象或可迭代的对象返回一个数组。  
  
## 语法  
  
```  
Array.from (arrayLike [ , mapfn [ , thisArg ] ] );  
```  
  
#### 参数  
 `arrayLike`  
 必需。  类似数组的对象或可迭代的对象。  
  
 `mapfn`  
 可选。  要对 `arrayLike` 中的每个元素调用的映射函数。  
  
 `thisArg`  
 可选。  指定映射函数中的 `this` 对象。  
  
## 备注  
 `arrayLike` 参数必须是具有编制索引的元素和 `length` 属性的对象或可迭代对象，如 `Set` 对象。  
  
 对数组中每个元素调用了可选映射函数。  
  
## 示例  
 下面的示例从 DOM 元素节点集合中返回一个数组。  
  
```javascript  
var elemArr = Array.from(document.querySelectorAll('*'));  
var elem = elemArr[0]; // elem contains a reference to the first DOM element  
  
```  
  
## 示例  
 下面的示例返回一个字符数组。  
  
```javascript  
var charArr = Array.from("abc");  
// charArr[0] == "a";  
```  
  
## 示例  
 下面的示例返回集合中包含的对象数组。  
  
```javascript  
var setObj = new Set("a", "b", "c");  
var objArr = Array.from(setObj);  
// objArr[1] == "b";  
  
```  
  
## 示例  
 下面的示例演示如何使用箭头语法和映射函数更改元素的值。  
  
```javascript  
var arr = Array.from([1, 2, 3], x => x * 10);  
// arr[0] == 10;  
// arr[1] == 20;  
// arr[2] == 30;  
```  
  
## 要求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]