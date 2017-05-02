---
title: "for...of 语句 (JavaScript) | Microsoft Docs"
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
ms.assetid: 7872b0b2-5701-4d72-9b52-ed13991542cc
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# for...of 语句 (JavaScript)
对从可迭代对象中获取的迭代器的每个值执行一个或多个语句。  
  
## 语法  
  
```  
for (variable of object) {  
    statements   
}  
```  
  
## 参数  
 `variable`  
 必需。  可为 `object` 的任何属性值的变量。  
  
 `object`  
 必需。  `Array`、`Map`、`Set` 等可迭代对象或实现 [迭代器接口](http://msdn.microsoft.com/zh-cn/3692355a-a703-4d43-8fb5-c03b4b7e8db1)的对象。  
  
 `statements`  
 可选。  要为 `object` 的每个值执行的一个或多个语句。  可以是复合语句。  
  
## 备注  
 在循环的每个迭代的开头，`variable` 的值是 `object` 的下一个属性值。  
  
## 示例  
 下面的示例阐释了如何使用数组上的 `for...of` 语句。  
  
```javascript  
let arr = [ "fred", "tom", "bob" ];  
  
for (let i of arr) {  
    console.log(i);  
}  
  
// Output:  
// fred  
// tom  
// bob  
  
```  
  
## 示例  
 下面的示例阐释了如何使用 `Map` 对象上的 `for...of` 语句。  
  
```javascript  
var m = new Map();  
m.set(1, "black");  
m.set(2, "red");  
  
for (var n of m) {  
  console.log(n);  
}  
  
// Output:  
// 1,black  
// 2,red  
  
```  
  
## 要求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## 请参阅  
 [for...in 语句](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)   
 [for 语句](../../javascript/reference/for-statement-javascript.md)   
 [while 语句](../../javascript/reference/while-statement-javascript.md)