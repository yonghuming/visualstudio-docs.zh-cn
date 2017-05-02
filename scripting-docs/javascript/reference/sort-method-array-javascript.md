---
title: "sort 方法 (Array) (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "sort"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Sort 方法"
ms.assetid: 9bd8b54a-c838-4806-85c8-62eebe6bc48c
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# sort 方法 (Array) (JavaScript)
对 `Array` 排序。  
  
## 语法  
  
```  
  
arrayobj.sort(sortFunction)   
```  
  
## 参数  
 `arrayObj`  
 必需。  任意 `Array` 对象。  
  
 `sortFunction`  
 可选。  用来确定元素顺序的函数的名称。  如果省略 ASCII 字符顺序，则将按升序对这些元素进行排序。  
  
## 返回值  
 已排序的数组。  
  
## 备注  
 `sort` 方法就地对 `Array` 对象进行排序；在执行过程中不会创建新 `Array` 对象。  
  
 如果在 `sortFunction` 参数中提供一个函数，则该函数必须返回下列值之一：  
  
-   如果所传递的第一个参数小于第二个参数，则返回负值。  
  
-   如果两个参数相等，则返回零。  
  
-   如果第一个参数大于第二个参数，则返回正值。  
  
## 示例  
 下面的示例演示如何使用 `sort` 方法。  
  
```javascript  
var a = new Array(4, 11, 2, 10, 3, 1);  
  
var b = a.sort();  
document.write(b);  
document.write("<br/>");  
  
// This is ASCII character order.  
// Output: 1,10,11,2,3,4)  
  
// Sort the array elements with a function that compares array elements.  
b = a.sort(CompareForSort);  
document.write(b);  
document.write("<br/>");  
// Output: 1,2,3,4,10,11.  
  
// Sorts array elements in ascending order numerically.  
function CompareForSort(first, second)  
{  
    if (first == second)  
        return 0;  
    if (first < second)  
        return -1;  
    else  
        return 1;   
}  
```  
  
## 要求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]