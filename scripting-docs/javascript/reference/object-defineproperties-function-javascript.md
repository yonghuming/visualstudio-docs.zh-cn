---
title: "Object.defineProperties 函数 (JavaScript) | Microsoft Docs"
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
  - "Object.defineProperties 函数 [JavaScript]"
ms.assetid: 2dae6658-a1c9-495f-bf06-bb3e964e6762
caps.latest.revision: 24
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 24
---
# Object.defineProperties 函数 (JavaScript)
将一个或多个属性添加到对象，并\/或修改现有属性的特性。  
  
## 语法  
  
```  
  
object.defineProperties(object, descriptors)  
```  
  
## 参数  
 `object`  
 必需。  对其添加或修改属性的对象。  这可以是本机 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 对象或 DOM 对象。  
  
 `descriptors`  
 必需。  包含一个或多个描述符对象的 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 对象。  每个描述符对象描述一个数据属性或访问器属性。  
  
## 返回值  
 已传递给函数的对象。  
  
## 备注  
 `descriptors` 参数是一个包含一个或多个描述符对象的对象。  
  
 *数据属性*是可储存和检索值的属性。  数据属性描述符包含一个 `value` 特性和\/或一个 `writable` 特性。  有关更多信息，请参见[数据属性和访问器属性](../../javascript/advanced/data-properties-and-accessor-properties.md)。  
  
 一旦设置或检索属性值，*访问器属性*就会调用用户提供的函数。  访问器属性描述符包含 `set` 特性和\/或 `get` 特性。  
  
 如果对象已包含一个带指定名称的属性，则修改该属性的特性。  有关更多信息，请参见[Object.defineProperty 函数](../../javascript/reference/object-defineproperty-function-javascript.md)。  
  
 若要创建一个对象并向新对象添加属性，则可使用 [Object.create 函数](../../javascript/reference/object-create-function-javascript.md)。  
  
## 添加属性  
 在下面的示例中，`Object.defineProperties` 函数将数据属性和访问器属性添加到用户定义的对象。  
  
 该示例使用对象文本来创建具有 `newDataProperty` 和 `newAccessorProperty` 描述符对象的 `descriptors` 对象。  
  
```javascript  
var newLine = "<br />";  
  
var obj = {};  
Object.defineProperties(obj, {  
    newDataProperty: {  
        value: 101,  
        writable: true,  
        enumerable: true,  
        configurable: true  
    },  
    newAccessorProperty: {  
        set: function (x) {  
            document.write("in property set accessor" + newLine);  
            this.newaccpropvalue = x;  
        },  
        get: function () {  
            document.write("in property get accessor" + newLine);  
            return this.newaccpropvalue;  
        },  
        enumerable: true,  
        configurable: true  
    }});  
  
// Set the accessor property value.  
obj.newAccessorProperty = 10;  
document.write ("newAccessorProperty value: " + obj.newAccessorProperty + newLine);  
  
// Output:  
// in property set accessor  
// in property get accessor  
// newAccessorProperty value: 10  
  
```  
  
 与前面的示例类似，下面的示例将动态添加属性而不是使用对象文本添加。  
  
```javascript  
  
var newLine = "<br />";  
  
// Create the descriptors object.  
var descriptors = new Object();  
  
// Add a data property descriptor to the descriptors object.  
descriptors.newDataProperty = new Object();  
descriptors.newDataProperty.value = 101;  
descriptors.newDataProperty.writable = true;  
descriptors.newDataProperty.enumerable = true;  
descriptors.newDataProperty.configurable = true;  
  
// Add an accessor property descriptor to the descriptors object.  
descriptors.newAccessorProperty = new Object();  
descriptors.newAccessorProperty.set = function (x) {  
    document.write("in property set accessor" + newLine);  
    this.newaccpropvalue = x;  
};  
descriptors.newAccessorProperty.get = function () {  
    document.write("in property get accessor" + newLine);  
    return this.newaccpropvalue;  
};  
descriptors.newAccessorProperty.enumerable = true;  
descriptors.newAccessorProperty.configurable = true;  
  
// Call the Object.defineProperties function.  
var obj = new Object();  
Object.defineProperties(obj, descriptors);  
  
// Set the accessor property value.  
obj.newAccessorProperty = 10;  
document.write ("newAccessorProperty value: " + obj.newAccessorProperty + newLine);  
  
// Output:  
// in property set accessor  
// in property get accessor  
// newAccessorProperty value: 10  
  
```  
  
## 修改属性  
 若要修改对象的属性特性，请添加以下代码。  `Object.defineProperties` 函数修改 `newDataProperty` 的 `writable` 特性，并修改 `newAccessorProperty` 的 `enumerable` 特性。  它将 `anotherDataProperty` 添加进对象，因为该属性名不存在。  
  
```  
Object.defineProperties(obj, {  
    newDataProperty: { writable: false },  
    newAccessorProperty: { enumerable: false },  
    anotherDataProperty: { value: "abc" }  
});  
```  
  
## 要求  
 在 Internet Explorer 9 标准、Internet Explorer 10 标准和 [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] app 中受支持。  仅在 DOM 对象的 Internet Explorer 8 中受支持，否则不受支持。  
  
## 请参阅  
 [Object.getOwnPropertyDescriptor 函数](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md)   
 [Object.getOwnPropertyNames 函数](../../javascript/reference/object-getownpropertynames-function-javascript.md)   
 [Object.defineProperty 函数](../../javascript/reference/object-defineproperty-function-javascript.md)   
 [Object.create 函数](../../javascript/reference/object-create-function-javascript.md)   
 [Object 对象](../../javascript/reference/object-object-javascript.md)