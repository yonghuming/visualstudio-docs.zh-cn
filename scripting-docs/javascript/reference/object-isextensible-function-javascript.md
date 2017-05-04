---
title: "Object.isExtensible 函数 (JavaScript) | Microsoft Docs"
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
  - "isExtensible 函数 [JavaScript]"
  - "Object.isExtensible 函数 [JavaScript]"
ms.assetid: a7d10beb-0d01-4e2d-8263-59ff07ac4352
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Object.isExtensible 函数 (JavaScript)
返回一个值，该值指示是否可向对象添加新属性。  
  
## 语法  
  
```javascript  
Object.isExtensible(object)  
```  
  
#### 参数  
 `object`  
 必需。  要测试的对象。  
  
## 返回值  
 如果对象是可扩展的（这表示可向对象添加新属性），则为 `true`；否则为 `false`。  
  
## 异常  
 如果 `object` 参数不是对象，则将引发 `TypeError` 异常。  
  
## 备注  
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
|`Object.isExtensible`|是|否|否|  
|[Object.isSealed](../../javascript/reference/object-issealed-function-javascript.md)|否|是|否|  
|[Object.isFrozen](../../javascript/reference/object-isfrozen-function-javascript.md)|否|是|是|  
  
## 示例  
 下面的示例阐释了 `Object.isExtensible` 函数的用法。  
  
```javascript  
// Create an object that has two properties.  
var obj = { pasta: "spaghetti", length: 10 };  
  
// Make the object non-extensible.  
Object.preventExtensions(obj);  
  
// Try to add a new property, and then verify that it is not added.  
obj.newProp = 50;  
document.write(obj.newProp);  
  
// Output:  
undefined  
  
```  
  
## 要求  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## 请参阅  
 [Object.preventExtensions 函数](../../javascript/reference/object-preventextensions-function-javascript.md)   
 [Object.seal 函数](../../javascript/reference/object-seal-function-javascript.md)   
 [Object.freeze 函数](../../javascript/reference/object-freeze-function-javascript.md)   
 [Object.isSealed 函数](../../javascript/reference/object-issealed-function-javascript.md)   
 [Object.isFrozen 函数](../../javascript/reference/object-isfrozen-function-javascript.md)