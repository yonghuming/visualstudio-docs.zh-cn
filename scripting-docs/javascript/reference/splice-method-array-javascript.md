---
title: "splice 方法 (Array) (JavaScript) | Microsoft Docs"
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
  - "splice"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "splice 方法"
ms.assetid: 85fdfb13-e3d9-4c89-b524-3ccee7001c93
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# splice 方法 (Array) (JavaScript)
从一个数组中移除元素，如有必要，在所移除元素的位置上插入新元素，并返回所移除的元素。  
  
## 语法  
  
```  
  
arrayObj.splice(start, deleteCount, [item1[, item2[, . . . [,itemN]]]])  
```  
  
## 参数  
 `arrayObj`  
 必需。  一个 `Array` 对象。  
  
 `start`  
 必需。  数组中移除元素操作的起点，从 0 开始。  
  
 `deleteCount`  
 必需。  要移除的元素数。  
  
 `item1, item2,. . ., itemN`  
 可选。  插入数组中代替已移除元素的元素。  
  
## 备注  
 `splice` 方法通过移除从 `start` 位置开始的指定个数的元素并插入新元素来修改 `arrayObj`。  返回值是一个由所移除的元素组成的新 `Array` 对象。  
  
## 示例  
 下面的代码演示如何使用 `splice` 方法。  
  
```javascript  
var arr = new Array("4", "11", "2", "10", "3", "1");  
arr.splice(2, 2, "21", "31");  
document.write(arr);  
  
// Output: 4,11,21,31,3,1  
  
```  
  
## 要求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## 请参阅  
 [slice 方法（数组）](../../javascript/reference/slice-method-array-javascript.md)