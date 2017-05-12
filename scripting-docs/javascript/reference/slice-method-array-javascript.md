---
title: "slice 方法 (Array) (JavaScript) | Microsoft Docs"
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
  - "slice"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "索引从 0 开始"
  - "Array 对象"
  - "slice 方法"
ms.assetid: 3c122219-14de-4126-b091-809659c026d6
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# slice 方法 (Array) (JavaScript)
返回一个数组中的一部分。  
  
## 语法  
  
```  
  
arrayObj.slice(start, [end])   
```  
  
## 参数  
 `arrayObj`  
 必需。  一个 `Array` 对象。  
  
 `start`  
 必需。  `arrayObj` 的指定部分的开头。  
  
 `end`  
 可选。  `arrayObj` 的指定部分的结尾。  
  
## 备注  
 `slice` 方法返回一个 `Array` 对象，其中包含了 `arrayObj` 的指定部分。  
  
 `slice` 方法一直复制到 `end` 所指示的元素，但是不包括该元素。  如果 `start` 为负，则将其视为 `length` \+ `start`，其中 `length` 为数组的长度。  如果 `end` 为负，则将其视为 `length` \+ `end`，其中 `length` 为数组的长度。  如果省略 `end`，则将一直提取到 `arrayObj` 的结尾。  如果 `end` 出现在 `start` 之前，则不会将任何元素复制到新数组中。  
  
## 示例  
 下面的示例演示如何使用 `slice` 方法。  在第一个示例中，`myArray` 的所有元素（最后一个元素除外）将复制到 `newArray` 中。  在第二个示例中，仅将 `myArray` 的最后两个元素复制到 `newArray` 中。  
  
```javascript  
var origArray = [3, 5, 7, 9];  
var newArray = origArray. slice(0, -1);  
document.write(origArray);  
document.write("<br/>");  
newArray = origArray. slice(-2);  
document.write(newArray);  
  
// Output:  
// 3,5,7,9  
// 7,9  
  
```  
  
## 要求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## 请参阅  
 [slice 方法（字符串）](../../javascript/reference/slice-method-string-javascript.md)   
 [String 对象](../../javascript/reference/string-object-javascript.md)