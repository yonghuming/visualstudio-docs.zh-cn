---
title: "Object.getPrototypeOf 函数 (JavaScript) | Microsoft Docs"
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
helpviewer_keywords: 
  - "getPrototypeOf 函数 [JavaScript]"
  - "Object.getPrototypeOf 函数 [JavaScript]"
ms.assetid: 1c59cd7a-a7e2-4c5c-83ec-e6bd2b104d9f
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Object.getPrototypeOf 函数 (JavaScript)
返回对象的原型。  
  
## 语法  
  
```javascript  
Object.getPrototypeOf(object)  
```  
  
#### 参数  
 `object`  
 必需。  引用原型的对象。  
  
## 返回值  
 `object` 参数的原型。  原型也是对象。  
  
## 异常  
 如果 `object` 参数不是对象，则将引发 `TypeError` 异常。  
  
## 示例  
 下面的示例阐释了 `Object.getPrototypeOf` 函数的用法。  
  
```javascript  
// Create a constructor function.  
function Pasta(grain, width) {  
    this.grain = grain;  
    this.width = width;  
}  
// Create an object from the pasta constructor.  
var spaghetti = new Pasta("wheat", 0.2);  
  
// Obtain the prototype from the object.  
var proto = Object.getPrototypeOf(spaghetti);  
  
// Add a property to the prototype and validate that  
// the original object has the property.  
proto.foodgroup = "carbohydrates";  
document.write(spaghetti.foodgroup + " ");  
  
// Verify that the prototype obtained from the object  
// is the same as the prototype of the constructor.  
var result = (proto === Pasta.prototype);  
document.write(result + " ");  
  
// Verify that prototype obtained from the object  
// is a prototype of the original object.  
var result = proto.isPrototypeOf(spaghetti);  
document.write(result);  
  
// Output: carbohydrates true true  
```  
  
## 示例  
 下面的示例使用 `Object.getPrototypeOf` 函数来验证数据类型。  
  
```javascript  
var reg = /a/;  
var result = (Object.getPrototypeOf(reg) === RegExp.prototype);  
document.write(result + " ");  
  
var err = new Error("an error");  
var result = (Object.getPrototypeOf(err) === Error.prototype);  
document.write(result);  
  
// Output: true true  
  
```  
  
## 要求  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## 请参阅  
 [prototype 属性（对象）](../../javascript/reference/prototype-property-object-javascript.md)   
 [isPrototypeOf 方法 \(Object\)](../../javascript/reference/isprototypeof-method-object-javascript.md)