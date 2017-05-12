---
title: "prototype 属性（日期） | Microsoft Docs"
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
ms.assetid: 44f9c637-7da7-4833-906d-358506f32ced
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# prototype 属性（日期）
为日期返回对原型的引用。  
  
## 语法  
  
```  
  
date.prototype  
```  
  
## 备注  
 `date` 参数是对象的名称。  
  
 使用 `prototype` 属性为 Date 提供一组基本功能。  对象的新的实例“继承”了赋予该对象的原型的行为。  
  
 例如，若要将方法添加到返回数组的最大元素的值的 `Date` 对象，请声明函数、将它添加到 `Date.prototype` 并使用它。  
  
```javascript  
function max( ){  
    var max = new Date();  
    max.setFullYear(2200, 01, 01);  
    return max;  
}  
Date.prototype.maxDate = max;  
var myDate = new Date();  
  
if (myDate < myDate.maxDate())  
    document.write("today isn't the max");  
else if (myDate == myDate.maxDate())  
    document.write("today is the max");   
  
// Output:  
// today isn't the max  
  
```  
  
 所有内部 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 对象都有一个只读的 `prototype` 属性。  可将属性和方法添加到原型中，但不能为对象分配其他原型。  但是，可以向用户定义的对象分配新的原型。  
  
## 要求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]