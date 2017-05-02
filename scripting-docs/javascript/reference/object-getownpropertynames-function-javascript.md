---
title: "Object.getOwnPropertyNames 函数 (JavaScript) | Microsoft Docs"
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
  - "getOwnPropertyNames 方法 [JavaScript]"
  - "Object.getOwnPropertyNames 方法 [JavaScript]"
ms.assetid: 59f4b6b1-02be-44b3-a06c-a5ca8f70c3d8
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Object.getOwnPropertyNames 函数 (JavaScript)
返回对象自己的属性的名称。  一个对象的自己的属性是指直接对该对象定义的属性，而不是从该对象的原型继承的属性。  对象的属性包括字段（对象）和函数。  
  
## 语法  
  
```javascript  
Object.getOwnPropertyNames(object)  
```  
  
#### 参数  
  
|参数|定义|  
|--------|--------|  
|`object`|必需。  包含自己的属性的对象。|  
  
## 返回值  
 一个数组，其中包含对象自己的属性的名称。  
  
## 异常  
 如果为 `object` 参数提供的值不是对象的名称，则将引发 `TypeError` 异常。  
  
## 备注  
 `getOwnPropertyNames` 方法同时返回可枚举的和不可枚举的属性和方法的名称。  若要仅返回可枚举的属性和方法的名称，可使用 [Object.keys 函数](../../javascript/reference/object-keys-function-javascript.md)。  
  
## 示例  
 下面的示例创建一个对象，该对象具有三个属性和一个方法。  然后使用 `getOwnPropertyNames` 方法获取该对象自己的属性（包括方法）。  
  
```javascript  
function Pasta(grain, width, shape) {  
    // Define properties.  
    this.grain = grain;  
    this.width = width;  
    this.shape = shape;  
    this.toString = function () {  
        return (this.grain + ", " + this.width + ", " + this.shape);  
    }  
}  
  
// Create an object.  
var spaghetti = new Pasta("wheat", 0.2, "circle");  
  
// Get the own property names.  
var arr = Object.getOwnPropertyNames(spaghetti);  
document.write (arr);  
  
// Output:  
//   grain,width,shape,toString  
```  
  
## 示例  
 下面的示例显示了使用 Pasta 构造函数构造的 spaghetti 对象中以字母“S”开头的属性名。  
  
```javascript  
function Pasta(grain, size, shape) {  
    this.grain = grain;   
    this.size = size;   
    this.shape = shape;   
}  
  
var spaghetti = new Pasta("wheat", 2, "circle");  
  
var names = Object.getOwnPropertyNames(spaghetti).filter(CheckKey);  
document.write(names);   
  
// Check whether the first character of a string is 's'.   
function CheckKey(value) {  
    var firstChar = value.substr(0, 1);   
    if (firstChar.toLowerCase() == 's')  
        return true;   
    else  
         return false;   
}  
// Output:  
// size,shape  
```  
  
## 要求  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## 请参阅  
 [Object.keys 函数](../../javascript/reference/object-keys-function-javascript.md)