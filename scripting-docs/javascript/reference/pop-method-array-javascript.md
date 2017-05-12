---
title: "pop 方法 (Array) (JavaScript) | Microsoft Docs"
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
  - "pop"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Pop 方法"
ms.assetid: 4fae7f98-29f1-4041-ba43-601f2e5145ec
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# pop 方法 (Array) (JavaScript)
从数组中移除最后一个元素并返回该元素。  
  
## 语法  
  
```  
  
arrayObj.pop( )  
```  
  
## 备注  
 使用 [push](../../javascript/reference/push-method-array-javascript.md) 和 `pop` 方法可模拟一个使用先进先出 \(LIFO\) 的原则来存储数据的堆栈。  
  
 必需的 `arrayObj` 引用是 `Array` 对象。  
  
 如果该数组为空，则返回 `undefined`。  
  
## 示例  
 下面的示例阐释了 `pop` 方法的用法。  
  
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
  
// Output: 9 8 7 6 5  
```  
  
## 要求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## 请参阅  
 [push 方法 \(Array\)](../../javascript/reference/push-method-array-javascript.md)