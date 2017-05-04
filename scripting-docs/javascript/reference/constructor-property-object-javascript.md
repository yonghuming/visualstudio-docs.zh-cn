---
title: "constructor 属性（对象）(JavaScript) | Microsoft Docs"
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
  - "constructor"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "constructor 属性"
ms.assetid: 6f5d0e9d-e85f-4fde-b558-744510483d69
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# constructor 属性（对象）(JavaScript)
指定创建一个对象的函数。  
  
## 语法  
  
```  
  
object.constructor  
```  
  
## 备注  
 必需的 `object` 是一个对象或函数的名称。  
  
 `constructor` 属性是每个具有原型的对象的原型成员。  这包括除 `Global` 和 `Math` 对象之外的所有内部 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 对象。  `constructor` 属性包含了对某种函数的引用，此种函数构造了特定对象的实例。  
  
## 示例  
 下面的示例阐释了 constructor 属性的用法。  
  
```javascript  
// A constructor function.  
function MyObj() {  
    this.number = 1;  
}  
  
var x = new String("Hi");  
  
if (x.constructor == String)  
    document.write("Object is a String.");  
document.write ("<br />");  
  
var y = new MyObj;  
if (y.constructor == MyObj)  
    document.write("Object constructor is MyObj.");  
  
// Output:  
// Object is a String.  
// Object constructor is MyObj.  
  
```  
  
## 要求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## 请参阅  
 [prototype 属性（对象）](../../javascript/reference/prototype-property-object-javascript.md)