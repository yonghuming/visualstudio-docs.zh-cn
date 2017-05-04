---
title: "Object.preventExtensions 函数 (JavaScript) | Microsoft Docs"
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
  - "Object.preventExtensions 函数 [JavaScript]"
  - "preventExtensions 函数 [JavaScript]"
  - "阻止新属性 [JavaScript]"
  - "属性 [JavaScript], 阻止新"
ms.assetid: e6b48197-2374-4437-a9fe-519dd45a2077
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Object.preventExtensions 函数 (JavaScript)
阻止向对象添加新属性。  
  
## 语法  
  
```javascript  
Object.preventExtensions(object)  
```  
  
#### 参数  
 `object`  
 必需。  要成为不可扩展的对象的对象。  
  
## 返回值  
 传递给函数的对象。  
  
## 异常  
 如果 `object` 参数不是对象，则将引发 `TypeError` 异常。  
  
## 备注  
 `Object.preventExtensions` 函数使对象不可扩展，这样便无法向其添加新的命名属性。  在使某个对象不可扩展后，不能对其进行扩展。  
  
 有关如何设置属性的特性的信息，请参见 [Object.defineProperty 函数](../../javascript/reference/object-defineproperty-function-javascript.md)。  
  
## 相关函数  
 以下相关函数可阻止修改对象的特性。  
  
|函数|对象已设置为不可扩展的|为每个属性将 `configurable` 设置为 `false`|为每个属性将 `writable` 设置为 `false`|  
|--------|-----------------|---------------------------------------|-----------------------------------|  
|`Object.preventExtensions`|是|否|否|  
|[Object.seal](../../javascript/reference/object-seal-function-javascript.md)|是|是|否|  
|[Object.freeze](../../javascript/reference/object-freeze-function-javascript.md)|是|是|是|  
  
 如果满足下表中标记的所有条件，则以下函数返回 `true`。  
  
|函数|对象是否可扩展|为所有属性将 `configurable` 设置为 `false`|为所有数据属性将 `writable` 设置为 `false`|  
|--------|-------------|---------------------------------------|-------------------------------------|  
|[Object.isExtensible](../../javascript/reference/object-isextensible-function-javascript.md)|是|否|否|  
|[Object.isSealed](../../javascript/reference/object-issealed-function-javascript.md)|否|是|否|  
|[Object.isFrozen](../../javascript/reference/object-isfrozen-function-javascript.md)|否|是|是|  
  
## 示例  
 下面的示例阐释了 `Object.preventExtensions` 函数的用法。  
  
```javascript  
// Create an object that has two properties.  
var obj = { pasta: "spaghetti", length: 10 };  
  
// Make the object non-extensible.  
Object.preventExtensions(obj);  
document.write(Object.isExtensible(obj));  
document.write("<br/>");  
  
// Try to add a new property, and then verify that it is not added.  
obj.newProp = 50;  
document.write(obj.newProp);  
  
// Output:  
// false  
// undefined  
  
```  
  
## 要求  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## 请参阅  
 [Object.seal 函数](../../javascript/reference/object-seal-function-javascript.md)   
 [Object.freeze 函数](../../javascript/reference/object-freeze-function-javascript.md)   
 [Object.isExtensible 函数](../../javascript/reference/object-isextensible-function-javascript.md)   
 [Object.isSealed 函数](../../javascript/reference/object-issealed-function-javascript.md)   
 [Object.isFrozen 函数](../../javascript/reference/object-isfrozen-function-javascript.md)