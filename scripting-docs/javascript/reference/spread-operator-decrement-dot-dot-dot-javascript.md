---
title: "Spread 运算符 (...) (JavaScript) | Microsoft Docs"
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
ms.assetid: 10263a4c-bd27-4d87-9917-fb4b6bf373db
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# Spread 运算符 (...) (JavaScript)
允许从 iterable 表达式（如另一个数组文本）初始化部分数组文本，或允许表达式扩展到多个参数（在函数调用中）。  
  
## 语法  
  
```  
var array = [[arg0ToN ,] ...iterable [, arg0ToN]]  
func([args ,] ...iterable [, args | ...iterable])  
  
```  
  
## 参数  
 `iterable`  
 必需。  迭代对象。  
  
 `arg0ToN`  
 可选。  数组文本的一个或多个元素。  
  
 `args`  
 可选。  函数的一个或多个参数。  
  
## 备注  
 有关迭代器的更多信息，请参见[迭代器和生成器](../../javascript/advanced/iterators-and-generators-javascript.md)。  有关使用 spread 运算符作为 rest 参数的详细信息，请参阅[函数](../../javascript/functions-javascript.md)。  
  
## 示例  
 以下代码示例将 spread 运算符的用法与 `concat` 方法的用法进行了对比。  
  
```javascript  
var a, b, c, d, e;  
a = [1,2,3];  
b = "dog";  
c = [42, "cat"];  
  
// Using the concat method.  
d = a.concat(b, c);  
  
// Using the spread operator.  
e = [...a, b, ...c];  
  
console.log(d);  
console.log(e);  
  
// Output:  
// 1, 2, 3, "dog", 42, "cat"  
// 1, 2, 3, "dog", 42, "cat"  
```  
  
## 示例  
 下面的代码示例演示了如何在函数调用中使用 spread 运算符。  在此示例中，使用 spread 运算符将两个数组文本传递给了函数，并且数组扩展到多个参数。  
  
```javascript  
function f(a, b, c, x, y, z) {  
  return a + b + c + x + y + z;  
}  
  
var args = [1, 2, 3];  
console.log(f(...args, 4, ...[5, 6]));  
  
// Output:  
// 21  
  
```  
  
## 示例  
 使用 spread 运算符，可以简化之前需要使用 `apply` 的代码。  
  
```javascript  
function f(x, y, z) {  
    return x + y + z;  
}  
  
var args = [1, 2, 3];  
  
// Old method  
func.apply(this, args);  
// New method  
func(...args);  
  
```  
  
## 要求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## 请参阅  
 [运算符优先级](../../javascript/operator-subtractprecedence-javascript.md)   
 [运算符摘要 \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)