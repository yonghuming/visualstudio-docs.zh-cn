---
title: "indexOf 方法 (Array) (JavaScript) | Microsoft Docs"
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
  - "数组 [JavaScript], IndexOf 方法"
  - "indexOf 方法 [JavaScript]"
ms.assetid: 5bee31ae-aaf1-4466-8cfd-ed287e3cdf17
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# indexOf 方法 (Array) (JavaScript)
返回某个值在数组中的第一个匹配项的索引。  
  
## 语法  
  
```  
  
array1.indexOf(searchElement[, fromIndex])  
```  
  
#### 参数  
  
|参数|定义|  
|--------|--------|  
|`array1`|必需。  一个数组对象。|  
|`searchElement`|必需。  要在 `array1` 中定位的值。|  
|`fromIndex`|可选。  用于开始搜索的数组索引。  如果省略 `fromIndex`，则从索引 0 处开始搜索。|  
  
## 返回值  
 数组中的 `searchElement` 的第一个匹配项的索引；如果未找到 `searchElement`，则为 \-1。  
  
## 备注  
 `indexOf` 方法在数组中搜索指定的值。  该方法返回第一个匹配项的索引；如果找不到指定的值，则为 \-1。  
  
 按升序索引顺序执行搜索。  
  
 数组元素将与 `searchElement` 值进行全等比较，与 `===` 运算符类似。  有关更多信息，请参见[比较运算符](../../javascript/reference/comparison-operators-javascript.md)。  
  
 可选 `fromIndex` 参数指定用于开始搜索的数组索引。  如果 `fromIndex` 大于或等于数组长度，则返回 \-1。  如果 `fromIndex` 为负，则搜索从数组长度加上 `fromIndex` 的位置处开始。  
  
## 示例  
 下面的示例阐释了 `indexOf` 方法的用法。  
  
```javascript  
// Create an array. (The elements start at index 0.)  
var ar = ["ab", "cd", "ef", "ab", "cd"];  
  
// Determine the first location of "cd".  
document.write(ar.indexOf("cd") + "<br/>");  
  
// Output: 1  
  
// Find "cd" starting at index 2.  
document.write(ar.indexOf("cd", 2) + "<br/>");  
  
// Output: 4  
  
// Find "gh" (which is not found).  
document.write (ar.indexOf("gh")+ "<br/>");  
  
// Output: -1  
  
// Find "ab" with a fromIndex argument of -2.  
// The search starts at index 3, which is the array length plus -2.  
document.write (ar.indexOf("ab", -2) + "<br/>");  
// Output: 3  
  
```  
  
## 要求  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## 请参阅  
 [JavaScript 方法](../../javascript/reference/javascript-methods.md)   
 [Array 对象](../../javascript/reference/array-object-javascript.md)   
 [使用数组](../../javascript/advanced/using-arrays-javascript.md)