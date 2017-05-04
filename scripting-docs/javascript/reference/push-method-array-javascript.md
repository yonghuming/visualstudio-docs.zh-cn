---
title: "push 方法 (Array) (JavaScript) | Microsoft Docs"
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
  - "push"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Push 方法"
ms.assetid: fa6e5799-dabe-4b3d-bd1f-0afc68c77134
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# push 方法 (Array) (JavaScript)
将新元素追加到一个数组中，并返回新的数组长度。  
  
## 语法  
  
```  
  
arrayObj.push([item1 [item2 [. . . [itemN ]]]])  
```  
  
## 参数  
 `arrayObj`  
 必需。  一个 `Array` 对象。  
  
 `item, item2,. . ., itemN`  
 可选。  `Array` 的新元素。  
  
## 备注  
 可使用 `push` 和 `pop` 方法模拟后进先出堆栈。  
  
 `push` 方法按元素出现的顺序附加元素。  如果某个参数是数组，则以单个元素的形式添加它。  使用 `concat` 方法要合并两个或多个数组中的元素。  
  
## 示例  
 下面的示例阐释了 `push` 方法的用法。  
  
```javascript  
var number;  
var my_array = new Array();  
  
my_array.push (5, 6, 7);  
my_array.push (8, 9);  
  
number = my_array.pop();  
while (number != undefined)  
   {  
   document.write (number + " ");  
   number = my_array.pop();  
   }  
  
// Output:  
// 9 8 7 6 5  
```  
  
## 要求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## 请参阅  
 [concat 方法（数组）](../../javascript/reference/concat-method-array-javascript.md)   
 [pop 方法 \(Array\)](../../javascript/reference/pop-method-array-javascript.md)