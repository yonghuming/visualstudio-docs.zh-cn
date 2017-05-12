---
title: "prototype 属性（数组） | Microsoft Docs"
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
ms.assetid: 5fedf632-8316-4e5d-ab20-10e41aa4d9f8
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# prototype 属性（数组）
为数组的类返回原型的引用。  
  
## 语法  
  
```  
  
array.prototype  
```  
  
## 备注  
 `array` 参数是数组的名称。  
  
 用 `prototype` 属性为对象的类提供一组基本功能。  对象的新的实例“继承”了赋予该对象的原型的行为。  
  
 例如，若要将方法添加到返回数组的最大元素的值的 `Array` 对象，请声明函数、将它添加到 `Array.prototype` 并使用它。  
  
```javascript  
function array_max( ){  
    var i, max = this[0];  
    for (i = 1; i < this.length; i++)  
    {  
    if (max < this[i])  
    max = this[i];  
    }  
    return max;  
}  
Array.prototype.max = array_max;  
var myArray = new Array(7, 1, 3, 11, 25, 9  
);  
document.write(myArray.max());  
  
// Output: 25  
```  
  
 所有内部 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 对象都有一个只读的 `prototype` 属性。  可将属性和方法添加到原型中，但不能为对象分配其他原型。  但是，可以向用户定义的对象分配新的原型。  
  
 本语言参考中，每个内部对象的方法和属性列表都指示了哪些是对象原型的一部分，哪些不是。  
  
## 要求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]