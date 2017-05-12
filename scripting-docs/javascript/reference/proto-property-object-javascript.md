---
title: "__proto__ 属性 (Object) (JavaScript) | Microsoft Docs"
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
  - "__proto__"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 97c3f84d-125e-4905-b921-b021264964ee
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# __proto__ 属性 (Object) (JavaScript)
包含对指定对象的内部原型的引用。  
  
## 语法  
  
```  
object.__proto__  
```  
  
#### 参数  
 `object`  
 必需。  要对其设置原型的对象。  
  
## 备注  
 `__proto__` 属性可用于设置对象的原型。  
  
 该对象或函数继承新原型的所有方法和属性，以及新原型的原型链中的所有方法和属性。  对象可以仅有一个原型（不包括原型链中继承的原型），因此当您调用 `__proto__` 属性时，将替换以前的原型。  
  
 您只能在可扩展对象上设置原型。  有关更多信息，请参见 [Object.preventExtensions 函数](../../javascript/reference/object-preventextensions-function-javascript.md)。  
  
> [!NOTE]
>  `__proto__` 属性名称以两个下划线开始和结束。  
  
## 示例  
 下面的代码示例显示如何为对象设置原型。  
  
```javascript  
function Rectangle() {  
}  
  
var rec = new Rectangle();  
  
if (console && console.log) {  
    console.log(rec.__proto__ === Rectangle.prototype);  // Returns true  
    rec.__proto__ = Object.prototype;  
    console.log(rec.__proto__ === Rectangle.prototype);  // Returns false  
}  
```  
  
## 示例  
 下面的代码示例演示如何通过将属性添加到原型来将其添加到对象中。  
  
```javascript  
var proto = { y: 2 };  
  
var obj = { x: 10 };  
obj.__proto__ = proto;  
  
proto.y = 20;  
proto.z = 40;  
  
if (console && console.log) {  
    console.log(obj.x === 10);  // Returns true  
    console.log(obj.y === 20);  // Returns true  
    console.log(obj.z === 40);  // Returns true  
}  
```  
  
## 示例  
 下面的代码示例通过在 `String` 对象上设置新原型将特性添加到该对象。  
  
```javascript  
var stringProp = { desc: "description" };  
  
String.__proto__ = stringProp;  
var s1 = "333";  
var s2 = new String("333");  
  
if (console && console.log) {  
  
    console.log(String.desc === "description"); // Returns true  
    console.log(s1.desc === "description");     // Returns false  
    console.log(s2.desc === "description");     // Returns false  
  
    s1.__proto__ = String;  // Can't be set.  
    s2.__proto__ = String;  
  
    console.log(s1.desc === "description"); // Returns false  
    console.log(s2.desc === "description"); // Returns true  
}  
```  
  
## 要求  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## 请参阅  
 [原型和原型继承](../../javascript/advanced/prototypes-and-prototype-inheritance.md)