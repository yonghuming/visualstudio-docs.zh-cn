---
title: "for...in 语句 (JavaScript) | Microsoft Docs"
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
helpviewer_keywords: 
  - "迭代语句, for...in 语句"
  - "循环结构, for...in 语句"
ms.assetid: 1b51a0ce-89f7-4a69-88ed-017b47dc398f
caps.latest.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 20
---
# for...in 语句 (JavaScript)
为一个对象的每个属性或一个数组的每个元素执行一个或多个语句。  
  
## 语法  
  
```  
for (variable in [object | array]) {  
    statements   
}  
```  
  
## 参数  
 `variable`  
 必需。  一个变量，可以是 `object` 的任何属性名或 `array` 的任何元素索引。  
  
 `object`, `array`  
 可选。  要对其进行循环的对象或数组。  
  
 `statements`  
 可选。  要为 `object` 的每个属性或 `array` 的每个元素执行的一个或多个语句。  可以是复合语句。  
  
## 备注  
 在循环的每个迭代开始时，`variable` 的值为 `object` 的下一个属性名或 `array` 的下一个元素索引。  然后，可以将 `variable` 用于循环中的任何语句，以便引用 `object` 的属性或 `array` 的元素。  
  
 未以确定的方式分配对象的属性。  不能按某个特定属性的索引指定该属性，而只能按该属性的名称指定它。  
  
 按元素顺序循环访问数组，即 0、1、2。  
  
## 示例  
 下面的示例阐释了 `for...in` 语句的用法，该语句将一个对象用作一个相关数组。  
  
```javascript  
// Initialize object.  
a = {"a" : "Athens" , "b" : "Belgrade", "c" : "Cairo"}  
  
// Iterate over the properties.  
var s = ""  
for (var key in a) {  
    s += key + ": " + a[key];  
    s += "<br />";  
    }  
document.write (s);  
  
// Output:  
// a: Athens  
// b: Belgrade  
// c: Cairo  
```  
  
## 示例  
 此示例阐释了如何使用 `for ... in` 语句来便循环访问具有 expando 属性的 `Array` 对象。  
  
```javascript  
// Initialize the array.  
var arr = new Array("zero","one","two");  
  
// Add a few expando properties to the array.  
arr["orange"] = "fruit";  
arr["carrot"] = "vegetable";  
  
// Iterate over the properties and elements.  
var s = "";  
for (var key in arr) {  
    s += key + ": " + arr[key];  
    s += "<br />";  
}  
  
document.write (s);  
  
// Output:  
//   0: zero  
//   1: one  
//   2: two  
//   orange: fruit  
//   carrot: vegetable  
```  
  
> [!NOTE]
>  使用 `Enumerator` 对象循环访问集合的成员。  
  
## 要求  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
## 请参阅  
 [for 语句](../../javascript/reference/for-statement-javascript.md)   
 [while 语句](../../javascript/reference/while-statement-javascript.md)