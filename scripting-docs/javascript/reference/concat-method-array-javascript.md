---
title: "concat 方法 (Array) (JavaScript) | Microsoft Docs"
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
  - "concat"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "concat 方法 (Array)"
  - "Concat 方法"
ms.assetid: bc2b4a6a-209e-4d59-8c24-59db01d53b1e
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# concat 方法 (Array) (JavaScript)
组合两个或两个以上的数组。  
  
## 语法  
  
```  
  
array1.concat([item1[, item2[, . . . [, itemN]]]])   
```  
  
## 参数  
 `array1`  
 必需。  其他数组连接到的 `Array` 对象。  
  
 `item1,. . ., itemN`  
 可选。  要添加到 `array1` 的末尾的附加项。  
  
## 备注  
 `concat` 方法返回一个 `Array` 对象，它包含 `array1` 和任何其他提供的项的连接。  
  
 要添加的项 \(*item1 itemN*\) 会按顺序（从列表中的第一个项开始）添加到数组。  如果某一项为数组，则其内容将添加到 `array1` 的末尾。  如果该项不是数组，则将其作为单个数组元素添加到数组末尾。  
  
 源数组元素按以下规则复制到结果数组：  
  
-   如果从连接到新数组的任何数组中复制某个对象，则该对象引用仍然指向相同的对象。  不论新数组和原始数组中哪一个有改变，都将引起对方的改变。  
  
-   如果将某个数字或字符串值添加到新数组，则只复制其值。  更改一个数组中的值不会影响另一个数组中的值。  
  
## 示例  
 下面的示例演示如何将 `concat` 方法用于数组：  
  
```javascript  
var a, b, c, d;  
a = new Array(1,2,3);  
b = "dog";  
c = new Array(42, "cat");  
d = a.concat(b, c);  
document.write(d);  
  
//Output:   
1, 2, 3, "dog", 42, "cat"  
  
```  
  
## 要求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## 请参阅  
 [concat 方法（字符串）](../../javascript/reference/concat-method-string-javascript.md)   
 [join 方法 \(Array\)](../../javascript/reference/join-method-array-javascript.md)