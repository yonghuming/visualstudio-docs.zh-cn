---
title: "Object.defineProperty 函数 (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- defineProperty function [JavaScript]
- Object.defineProperty function [JavaScript]
ms.assetid: c5d05346-940a-40c2-b12a-e8b25abc8d46
caps.latest.revision: "74"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 89291f5c836f74a5dd71099328ce389a12f6fd24
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="objectdefineproperty-function-javascript"></a>Object.defineProperty 函数 (JavaScript)
将属性添加到对象，或修改现有属性的特性。  
  
## <a name="syntax"></a>语法  
  
```  
Object.defineProperty(object, propertyname, descriptor)  
```  
  
## <a name="parameters"></a>参数  
 `object`  
 必需。 要在其上添加或修改属性的对象。 这可能是一个本机 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 对象（即用户定义的对象或内置对象）或 DOM 对象。  
  
 `propertyname`  
 必需。 一个包含属性名称的字符串。  
  
 `descriptor`  
 必需。 属性描述符。 它可以针对数据属性或访问器属性。  
  
## <a name="return-value"></a>返回值  
 已修改对象。  
  
## <a name="remarks"></a>备注  
 可使用 `Object.defineProperty` 函数来执行以下操作：  
  
-   向对象添加新属性。 当对象不具有指定的属性名称时，发生此操作。  
  
-   修改现有属性的特性。 当对象已具有指定的属性名称时，发成此操作。  
  
 描述符对象中会提供属性定义，用于描述数据属性或访问器属性的特性。 描述符对象是 `Object.defineProperty` 函数的参数。  
  
 若要将多个属性添加到对象，或修改现有的多个属性，可以使用[Object.defineProperties 函数](../../javascript/reference/object-defineproperties-function-javascript.md)。  
  
## <a name="exceptions"></a>异常  
 如果以下任一条件为 true，则引发 `TypeError` 异常：  
  
-   `object` 参数不是对象。  
  
-   对象不是[可扩展](../../javascript/reference/object-isextensible-function-javascript.md)且不存在指定的属性名称...  
  
-   `descriptor` 具有 `value` 或 `writable` 特性，并且具有 `get` 或 `set` 特性。  
  
-   `descriptor` 具有 `get` 或 `set` 特性，上述特性不是函数且已定义。  
  
-   指定的属性名称已存在，现有属性具有 `false` 的 `configurable` 特性，且 `descriptor` 包含一个或多个与现有属性中特性不同的特性。 但是，当现有属性具有 `false` 的 `configurable` 特性和 `true` 的 `writable` 特性时，则允许 `value` 或 `writable` 特性不同。  
  
## <a name="adding-a-data-property"></a>添加数据属性  
 在以下示例中，`Object.defineProperty` 函数向用户定义的对象添加数据属性。 若改为向现有的 DOM 对象添加属性，则取消对 `var = window.document` 行的注释。  
  
```JavaScript  
var newLine = "<br />";  
  
// Create a user-defined object.  
var obj = {};  
  
// Add a data property to the object.  
Object.defineProperty(obj, "newDataProperty", {  
    value: 101,  
    writable: true,  
    enumerable: true,  
    configurable: true  
});  
  
// Set the property value.  
obj.newDataProperty = 102;  
document.write("Property value: " + obj.newDataProperty + newLine);  
  
// Output:  
// Property value: 102  
```  
  
 若要列出对象属性，请将以下代码添加到此示例中。  
  
```JavaScript  
var names = Object.getOwnPropertyNames(obj);  
for (var i = 0; i < names.length; i++) {  
    var prop = names[i];  
  
    document.write(prop + ': ' + obj[prop]);  
    document.write(newLine);  
}  
  
// Output:  
//  newDataProperty: 102  
```  
  
## <a name="modifying-a-data-property"></a>修改数据特性  
 若要修改对象的属性特性，请将以下代码添加到前面所示的 `addDataProperty` 函数。 `descriptor` 参数只包含 `writable` 特性。 其他数据属性特性保持不变。  
  
```JavaScript  
// Modify the writable attribute of the property.  
Object.defineProperty(obj, "newDataProperty", { writable: false });  
  
// List the property attributes by using a descriptor.  
// Get the descriptor with Object.getOwnPropertyDescriptor.  
var descriptor = Object.getOwnPropertyDescriptor(obj, "newDataProperty");  
for (var prop in descriptor) {  
    document.write(prop + ': ' + descriptor[prop]);  
    document.write(newLine);  
}  
  
// Output  
// writable: false  
// value: 102  
// configurable: true  
// enumerable: true  
```  
  
## <a name="adding-an-accessor-property"></a>添加访问器属性  
 在以下示例中，`Object.defineProperty` 函数向用户定义的对象添加访问器属性。  
  
```JavaScript  
var newLine = "<br />";  
  
// Create a user-defined object.  
var obj = {};  
  
// Add an accessor property to the object.  
Object.defineProperty(obj, "newAccessorProperty", {  
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
});  
  
// Set the property value.  
obj.newAccessorProperty = 30;  
document.write("Property value: " + obj.newAccessorProperty + newLine);  
  
// Output:  
// in property set accessor  
// in property get accessor  
// Property value: 30  
  
```  
  
 若要列出对象属性，请将以下代码添加到此示例中。  
  
```JavaScript  
var names = Object.getOwnPropertyNames(obj);  
for (var i = 0; i < names.length; i++) {  
    var prop = names[i];  
  
    document.write(prop + ': ' + obj[prop]);  
    document.write(newLine);  
}  
// Output:  
// in property get accessor  
// newAccessorProperty: 30  
  
```  
  
## <a name="modifying-an-accessor-property"></a>修改访问器属性  
 若要修改对象的访问器属性，请将以下代码添加前面所示的代码。 `descriptor` 参数只包含 `get` 访问器定义。 其他属性特性保持不变。  
  
```JavaScript  
// Modify the get accessor.  
Object.defineProperty(obj, "newAccessorProperty", {  
    get: function () { return this.newaccpropvalue; }  
});  
  
// List the property attributes by using a descriptor.  
// Get the descriptor with Object.getOwnPropertyDescriptor.  
var descriptor = Object.getOwnPropertyDescriptor(obj, "newAccessorProperty");  
for (var prop in descriptor) {  
    document.write(prop + ': ' + descriptor[prop]);  
    document.write(newLine);  
}  
  
// Output:  
// get: function () { return this.newaccpropvalue; }  
// set: function (x) { document.write("in property set accessor" + newLine); this.newaccpropvalue = x; }  
// configurable: true  
// enumerable: true  
```  
  
## <a name="modifying-a-property-on-a-dom-element"></a>修改 DOM 元素上的属性  
 下面的示例演示如何通过使用 `Object.getOwnPropertyDescriptor` 函数来获取和修改属性的属性描述符，从而自定义内置 DOM 属性。 对于此示例中，必须通过使用 ID 为“div”的 DIV 元素。  
  
```JavaScript  
// Get the querySelector property descriptor.  
var descriptor = Object.getOwnPropertyDescriptor(Element.prototype, "querySelector");  
  
// Make the property read-only.  
descriptor.value = "query";  
descriptor.writable = false;  
// Apply the changes to the Element prototype.  
Object.defineProperty(Element.prototype, "querySelector", descriptor);  
  
// Get a DOM element from the HTML body.  
var elem = document.getElementById("div");  
  
// Attempt to change the value. This causes the revised value attribute to be called.  
elem.querySelector = "anotherQuery";  
document.write(elem.querySelector);  
  
// Output:  
// query  
  
```  
  
## <a name="requirements"></a>要求  
 Internet Explorer 9 标准模式、Internet Explorer 10 标准模式以及 [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] 应用支持所有功能。  
  
 [!INCLUDE[jsv58textspecific](../../javascript/reference/includes/jsv58textspecific-md.md)] 支持 DOM 对象，但不支持用户定义的对象。 可以指定 `enumerable` 和 `configurable` 特性，但不使用它们。  
  
## <a name="see-also"></a>另请参阅  
 [文档对象模型原型，第 2 部分： 访问器 (getter/setter) 支持](http://msdn.microsoft.com/library/dd229916\(v=VS.85\).aspx)   
 [Object.defineProperties 函数](../../javascript/reference/object-defineproperties-function-javascript.md)   
 [Object.create 函数](../../javascript/reference/object-create-function-javascript.md)   
 [Object.getOwnPropertyDescriptor 函数](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md)   
 [Object.getOwnPropertyNames 函数](../../javascript/reference/object-getownpropertynames-function-javascript.md)