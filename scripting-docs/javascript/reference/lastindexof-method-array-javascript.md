---
title: "lastIndexOf 方法 (Array) (JavaScript) | Microsoft Docs"
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
  - "数组 [JavaScript], lastIndexOf 方法"
  - "lastIndexOf 方法 [JavaScript]"
ms.assetid: 04f5145d-007e-498f-b06f-11ab384c2968
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# lastIndexOf 方法 (Array) (JavaScript)
返回指定的值在数组中的最后一个匹配项的索引。  
  
## 语法  
  
```  
  
array1.lastIndexOf(searchElement[, fromIndex])  
```  
  
#### 参数  
  
|参数|定义|  
|--------|--------|  
|`array1`|必需。  要搜索的数组对象。|  
|`searchElement`|必需。  要在 `array1` 中定位的值。|  
|`fromIndex`|可选。  用于开始搜索的数组索引。  如果省略 `fromIndex`，则搜索将从数组中的最后一个索引处开始。|  
  
## 返回值  
 数组中的 `searchElement` 的最后一个匹配项的索引；如果未找到 `searchElement`，则为 \-1。  
  
## 备注  
 `lastIndexOf` 方法在数组中搜索指定的值。  该方法返回第一个匹配项的索引；如果找不到指定的值，则为 \-1。  
  
 搜索按降序索引顺序进行（首先搜索最后一个成员）。  若要按升序顺序搜索，请使用 [indexOf 方法 \(Array\)](../../javascript/reference/indexof-method-array-javascript.md)。  
  
 数组元素将与 `searchElement` 值进行全等比较，与使用 `===` 运算符进行的比较类似。  有关更多信息，请参见[比较运算符](../../javascript/reference/comparison-operators-javascript.md)。  
  
 可选 `fromIndex` 参数指定用于开始搜索的数组索引。  如果 `fromIndex` 大于或等于数组长度，则搜索整个数组。  如果 `fromIndex` 为负，则搜索从数组长度加上 `fromIndex` 的位置处开始。  如果计算所得的索引小于 0，则返回 \-1。  
  
## 示例  
 下面的示例阐释了 `lastIndexOf` 方法的用法。  
  
```javascript  
// Create an array.  
var ar = ["ab", "cd", "ef", "ab", "cd"];  
  
// Determine the first location, in descending order, of "cd".  
document.write(ar.lastIndexOf("cd") + "<br/>");  
  
// Output: 4  
  
// Find "cd" in descending order, starting at index 2.  
document.write(ar.lastIndexOf("cd", 2) + "<br/>");  
  
// Output: 1  
  
// Search for "gh" (which is not found).  
document.write(ar.lastIndexOf("gh")+ "<br/>");  
  
// Output: -1  
  
// Find "ab" with a fromIndex argument of -3.  
// The search in descending order starts at index 3,  
// which is the array length minus 2.  
document.write(ar.lastIndexOf("ab", -3) + "<br/>");  
// Output: 0  
  
```  
  
## 要求  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## 请参阅  
 [indexOf 方法 \(Array\)](../../javascript/reference/indexof-method-array-javascript.md)   
 [Array 对象](../../javascript/reference/array-object-javascript.md)   
 [使用数组](../../javascript/advanced/using-arrays-javascript.md)