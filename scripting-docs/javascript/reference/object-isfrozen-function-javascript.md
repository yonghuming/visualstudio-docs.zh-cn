---
title: "Object.isFrozen 函数 (JavaScript) | Microsoft Docs"
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
  - "isFrozen 函数 [JavaScript]"
  - "Object.isFrozen 函数 [JavaScript]"
ms.assetid: 6cf1bbc6-56e8-429b-8e2c-0024fa614acc
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Object.isFrozen 函数 (JavaScript)
如果无法在对象中修改现有属性的特性和值，且无法向对象添加新属性，则返回 `true`。  
  
## 语法  
  
```javascript  
Object.isFrozen(object)  
```  
  
#### 参数  
 `object`  
 必需。  要测试的对象。  
  
## 返回值  
 如果满足下列所有条件，则为 `true`：  
  
-   对象是不可扩展的，这表示无法向对象添加新属性。  
  
-   `configurable` 特性对于所有现有属性为 `false`。  
  
-   `writable` 特性对于所有现有数据属性为 `false`。  
  
 在该对象不具有现有属性的情况下，如果该对象是不可扩展的，则此函数返回 `true`。  
  
## 异常  
 如果 `object` 参数不是对象，则将引发 `TypeError` 异常。  
  
## 备注  
 在某个属性的 `configurable` 特性为 `false` 时，无法更改该属性的特性，也无法删除该属性。  当 `writable` 为 `false` 时，无法更改数据属性值。  在 `configurable` 为 `false` 且 `writable` 为 `true` 时，可以更改 `value` 和 `writable` 特性。  
  
 有关如何设置属性的特性的信息，请参见 [Object.defineProperty 函数](../../javascript/reference/object-defineproperty-function-javascript.md)。  若要获取属性的特性，可使用 [Object.getOwnPropertyDescriptor 函数](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md)。  
  
## 相关函数  
 以下相关函数可阻止修改对象的特性。  
  
|函数|对象已设置为不可扩展的|为每个属性将 `configurable` 设置为 `false`|为每个属性将 `writable` 设置为 `false`|  
|--------|-----------------|---------------------------------------|-----------------------------------|  
|[Object.preventExtensions](../../javascript/reference/object-preventextensions-function-javascript.md)|是|否|否|  
|[Object.seal](../../javascript/reference/object-seal-function-javascript.md)|是|是|否|  
|[Object.freeze](../../javascript/reference/object-freeze-function-javascript.md)|是|是|是|  
  
 如果满足下表中标记的所有条件，则以下函数返回 `true`。  
  
|函数|对象是否可扩展|为所有属性将 `configurable` 设置为 `false`|为所有数据属性将 `writable` 设置为 `false`|  
|--------|-------------|---------------------------------------|-------------------------------------|  
|[Object.isExtensible](../../javascript/reference/object-isextensible-function-javascript.md)|是|否|否|  
|[Object.isSealed](../../javascript/reference/object-issealed-function-javascript.md)|否|是|否|  
|`Object.isFrozen`|否|是|是|  
  
## 示例  
 下面的示例阐释了 `Object.isFrozen` 函数的用法。  
  
```javascript  
// Create an object that has two properties.  
var obj = { pasta: "spaghetti", length: 10 };  
  
// Freeze the object, and verify that it is frozen.  
Object.freeze(obj);  
document.write(obj.isFrozen());  
  
// Try to add a new property, and then verify that it is not added.   
obj.newProp = 50;  
document.write (obj.newProp);  
document.write ("<br/>");  
  
// Try to delete a property, and then verify that it is still present.  
delete obj.length;  
document.write (obj.length);  
document.write ("<br/> ");  
  
// Try to change a property value, and then verify that it is not changed.  
obj.pasta = "linguini";  
document.write (obj.pasta);  
  
// Output:  
// true  
// undefined  
// 10  
// spaghetti  
  
```  
  
## 要求  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## 请参阅  
 [Object.preventExtensions 函数](../../javascript/reference/object-preventextensions-function-javascript.md)   
 [Object.seal 函数](../../javascript/reference/object-seal-function-javascript.md)   
 [Object.freeze 函数](../../javascript/reference/object-freeze-function-javascript.md)   
 [Object.isExtensible 函数](../../javascript/reference/object-isextensible-function-javascript.md)   
 [Object.isSealed 函数](../../javascript/reference/object-issealed-function-javascript.md)   
 [Object.defineProperty 函数](../../javascript/reference/object-defineproperty-function-javascript.md)   
 [Object.getOwnPropertyDescriptor 函数](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md)   
 [Object.getOwnPropertyNames 函数](../../javascript/reference/object-getownpropertynames-function-javascript.md)