---
title: "Object.keys 函数 (JavaScript) | Microsoft Docs"
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
  - "keys 方法 [JavaScript]"
  - "Object.keys 方法 [JavaScript]"
ms.assetid: cf4a7daf-cf28-4467-bc6b-f7f106ec3876
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Object.keys 函数 (JavaScript)
返回对象的可枚举属性和方法的名称。  
  
## 语法  
  
```javascript  
Object.keys(object)  
```  
  
#### 参数  
  
|参数|定义|  
|--------|--------|  
|`object`|必需。  包含属性和方法的对象。  这可以是您创建的对象或现有文档对象模型 \(DOM\) 对象。|  
  
## 返回值  
 一个数组，其中包含对象的可枚举属性和方法的名称。  
  
## 异常  
 如果为 `object` 参数提供的值不是对象的名称，则将引发 `TypeError` 异常。  
  
## 备注  
 `keys` 方法仅返回可枚举属性和方法的名称。  若要返回可枚举的和不可枚举的属性和方法的名称，可使用 [Object.getOwnPropertyNames 函数](../../javascript/reference/object-getownpropertynames-function-javascript.md)。  
  
 有关属性的 `enumerable` 特性的信息，请参见 [Object.defineProperty 函数](../../javascript/reference/object-defineproperty-function-javascript.md)和 [Object.getOwnPropertyDescriptor 函数](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md)。  
  
## 示例  
 下面的示例创建一个对象，该对象具有三个属性和一个方法。  然后使用 `keys` 方法获取该对象的属性和方法。  
  
```javascript  
// Create a constructor function.  
function Pasta(grain, width, shape) {  
    this.grain = grain;  
    this.width = width;  
    this.shape = shape;  
  
    // Define a method.  
    this.toString = function () {  
        return (this.grain + ", " + this.width + ", " + this.shape);  
    }  
}  
  
// Create an object.  
var spaghetti = new Pasta("wheat", 0.2, "circle");  
  
// Put the enumerable properties and methods of the object in an array.  
var arr = Object.keys(spaghetti);  
document.write (arr);  
  
// Output:  
// grain,width,shape,toString  
```  
  
## 示例  
 下面的示例显示 Pasta 对象中以字母“g”开头的所有可枚举属性的名称。  
  
```javascript  
// Create a constructor function.  
function Pasta(grain, width, shape) {  
    this.grain = grain;  
    this.width = width;  
    this.shape = shape;  
}  
  
var polenta = new Pasta("corn", 1, "mush");  
  
var keys = Object.keys(polenta).filter(CheckKey);  
document.write(keys);  
  
// Check whether the first character of a string is "g".  
function CheckKey(value) {  
    var firstChar = value.substr(0, 1);  
    if (firstChar.toLowerCase() == "g")  
        return true;  
    else  
        return false;  
}  
  
// Output:  
// grain  
```  
  
## 要求  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## 请参阅  
 [Object.getOwnPropertyNames 函数](../../javascript/reference/object-getownpropertynames-function-javascript.md)