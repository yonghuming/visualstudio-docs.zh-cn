---
title: "prototype 属性（数字） | Microsoft Docs"
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
ms.assetid: d5fb87af-fc3a-4469-8dde-d31daf654f94
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# prototype 属性（数字）
为数字的类返回原型的引用。  
  
## 语法  
  
```  
  
number.prototype  
```  
  
## 备注  
 `number` 参数是数字的名称。  
  
 用 `prototype` 属性为对象的类提供一组基本功能。  对象的新的实例“继承”了赋予该对象的原型的行为。  
  
 例如，若要将方法添加到返回数字位数（整数）的 `Number` 对象，请声明函数、将它添加到 `Number.prototype` 并使用它。  
  
```javascript  
function number_digits() {  
    var digits = 0;  
    var num = this;  
    while (num) >= 1) {  
        digits++;  
        num /= 10;  
    }  
    return digits;  
}  
  
Number.prototype.digits = number_digits;  
var myNumber = new Number(3456.789);  
document.write(myNumber.digits());  
// Output:  
// 4  
```  
  
 所有内部 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 对象都有一个只读的 `prototype` 属性。  可将属性和方法添加到原型中，但不能为对象分配其他原型。  但是，可以向用户定义的对象分配新的原型。  
  
 本语言参考中，每个内部对象的方法和属性列表都指示了哪些是对象原型的一部分，哪些不是。  
  
## 要求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]