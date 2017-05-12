---
title: "Object.create 函数 (JavaScript) | Microsoft Docs"
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
  - "create 函数 [JavaScript]"
  - "Object.create 函数 [JavaScript]"
ms.assetid: 0ad31f36-a9ee-444e-b0fe-c87843d03196
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# Object.create 函数 (JavaScript)
创建一个具有指定原型且可选择性地包含指定属性的对象。  
  
## 语法  
  
```  
Object.create(prototype, descriptors)  
```  
  
#### 参数  
 `prototype`  
 必需。  要用作原型的对象。  可以为 `null`。  
  
 `descriptors`  
 可选。  包含一个或多个属性描述符的 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 对象。  
  
 “数据属性”是可获取且可设置值的属性。  数据属性描述符包含 `value` 特性，以及 `writable`、`enumerable` 和 `configurable` 特性。  如果未指定最后三个特性，则它们默认为 `false`。  只要检索或设置该值，“访问器属性”就会调用用户提供的函数。  访问器属性描述符包含 `set` 特性和\/或 `get` 特性。  有关详细信息，请参阅 [Object.defineProperty 函数](../../javascript/reference/object-defineproperty-function-javascript.md)。  
  
## 返回值  
 一个具有指定的内部原型且包含指定的属性（如果有）的新对象。  
  
## 异常  
 如果满足下列任一条件，则将引发 `TypeError` 异常：  
  
-   `prototype` 参数不是对象且不为 `null`。  
  
-   `descriptors` 参数中的描述符具有 `value` 或 `writable` 特性，并具有 `get` 或 `set` 特性。  
  
-   `descriptors` 参数中的描述符具有不为函数的 `get` 或 `set` 特性。  
  
## 备注  
 若要停止原型链，可以使用采用了 `null` `prototype` 参数的函数。  所创建的对象将没有原型。  
  
## 示例  
 下面的示例创建使用 `null` 原型的对象并添加两个可枚举的属性。  
  
```javascript  
var newObj = Object.create(null, {  
            size: {  
                value: "large",  
                enumerable: true  
            },  
            shape: {  
                value: "round",  
                enumerable: true  
            }  
        });  
  
document.write(newObj.size + "<br/>");  
document.write(newObj.shape + "<br/>");  
document.write(Object.getPrototypeOf(newObj));  
  
// Output:  
// large  
// round  
// null  
  
```  
  
## 示例  
 下面的示例创建一个具有与 Object 对象相同的内部原型的对象。  您会发现，该对象具有与使用对象文本创建的对象相同的原型。  [Object.getPrototypeOf](../../javascript/reference/object-getprototypeof-function-javascript.md) 函数可获取原始对象的原型。  若要获取对象的属性描述符，可以使用[Object.getOwnPropertyDescriptor 函数](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md)。  
  
```javascript  
var firstLine = { x: undefined, y: undefined };  
  
var secondLine = Object.create(Object.prototype, {  
        x: {  
                value: undefined,   
                writable: true,   
                configurable: true,   
                enumerable: true  
            },  
            y: {  
                value: undefined,   
                writable: true,   
                configurable: true,   
                enumerable: true  
            }  
});  
  
document.write("first line prototype = " + Object.getPrototypeOf(firstLine));  
document.write("<br/>");  
document.write("second line prototype = " + Object.getPrototypeOf(secondLine));  
  
// Output:  
// first line prototype = [object Object]  
// second line prototype = [object Object]  
```  
  
## 示例  
 下面的示例创建一个具有与 Shape 对象相同的内部原型的对象。  
  
```javascript  
  
// Create the shape object.  
var Shape = { twoDimensional: true, color: undefined, hasLineSegments: undefined };  
  
var Square = Object.create(Object.getPrototypeOf(Shape));  
  
```  
  
## 要求  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## 请参阅  
 [Object.getPrototypeOf 函数](../../javascript/reference/object-getprototypeof-function-javascript.md)   
 [isPrototypeOf 方法 \(Object\)](../../javascript/reference/isprototypeof-method-object-javascript.md)   
 [Creating 对象](../../javascript/creating-objects-javascript.md)