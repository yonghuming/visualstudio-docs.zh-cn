---
title: "findIndex 方法（数组）(JavaScript) | Microsoft Docs"
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
ms.assetid: 3a200cf0-db67-4c7b-89f8-5e9f5dc1a926
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# findIndex 方法（数组）(JavaScript)
返回满足回调函数中指定的测试条件的第一个数组元素的索引值。  
  
## 语法  
  
```  
arrayObj.findIndex(callbackfn [, thisArg]);  
```  
  
#### 参数  
 `arrayObj`  
 必需。  数组对象。  
  
 `callbackfn`  
 必需。  用于测试数组中的每个元素的回调函数。  
  
 `thisArg`  
 可选。  指定回调函数中的 `this` 对象。  如果未指定，则未定义 `this` 对象。  
  
## 备注  
 对于数组中的每个元素，`findIndex` 方法都会调用一次回调函数（采用升序索引顺序），直到有元素返回 `true`。  只要有一个元素返回 true，`findIndex` 立即返回该返回 true 的元素的索引值。  如果数组中没有任何元素返回 true，则 `findIndex` 返回 \-1。  
  
 `findIndex` 不会改变数组对象。  
  
## 回调函数语法  
 回调函数的语法如下所示：  
  
 `function callbackfn(value, index, thisArg)`  
  
 你可使用最多三个参数来声明回调函数。  
  
 回调函数的参数如下所示。  
  
|回调参数|定义|  
|----------|--------|  
|`value`|数组元素的值。|  
|`index`|数组元素的数字索引。|  
|`arrayObj`|要遍历的数组对象。|  
  
## 示例  
 在下面的示例中，回调函数测试数组中的每个元素是否都等于 2。  
  
```javascript  
[1,2,3].findIndex(function(x) { x == 2; });  
// Returns an index value of 1.  
  
```  
  
## 示例  
 下面的示例使用箭头语法来测试每个元素。  在此示例中，没有任何元素返回 `true`，`findIndex` 返回 \-1。  
  
```  
[1,2,3].findIndex(x => x == 4);  
// Returns an index value of -1.  
  
```  
  
## 要求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]