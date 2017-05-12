---
title: "代理对象 (JavaScript) | Microsoft Docs"
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
ms.assetid: 2b89abee-04fa-47e6-9676-980016cff5f8
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# 代理对象 (JavaScript)
启用对象的自定义行为。  
  
## 语法  
  
```  
proxyObj = new Proxy(target, handler)  
```  
  
#### 参数  
 `target`  
 必需。  将通过代理虚拟化的对象或函数。  
  
 `handler`  
 必需。  具有可实现自定义行为的方法（陷阱）的对象。  
  
## 备注  
 `Proxy` 对象用于截获对另一个对象执行的内部低级别操作。  代理对象可以用于拦截、对象虚拟化、日志记录\/分析和其他用途。  
  
 如果尚未在代理的处理程序中定义特定操作陷阱，该操作将转发至目标。  
  
 处理程序对象可定义以下方法（陷阱）来实现自定义行为。  此处所列示例并非全部示例。  若要支持处理程序方法中有条件的默认行为，可使用[Reflect 对象](../../javascript/reference/reflect-object-javascript.md)方法。  
  
|处理程序方法（陷阱）语法|用法示例|  
|------------------|----------|  
|`apply: function(target, thisArg, args)`|函数调用陷阱。|  
|`construct: function(target, args)`|构造函数陷阱。|  
|`defineProperty: function(target, propertyName, descriptor)`|[Object.defineProperty 函数](../../javascript/reference/object-defineproperty-function-javascript.md) 陷阱。|  
|`deleteProperty: function(target, propertyName)`|`delete` 语句的陷阱。|  
|`enumerate: function(target)`|[for…in](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md) 语句、[Object.getOwnPropertySymbols](../../javascript/reference/object-getownpropertysymbols-function-javascript.md)、[Object.keys](../../javascript/reference/object-keys-function-javascript.md) 函数和 [JSON.stringify](../../javascript/reference/json-stringify-function-javascript.md) 的陷阱。|  
|`get: function(target, propertyName, receiver)`|任何 [getter](../../javascript/creating-objects-javascript.md) 属性的陷阱。|  
|`getOwnPropertyDescriptor: function(target, propertyName)`|[Object.getOwnPropertyDescriptor 函数](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md) 的陷阱。|  
|`getPrototypeOf: function(target)`|[Object.getPrototypeOf 函数](../../javascript/reference/object-getprototypeof-function-javascript.md) 的陷阱。|  
|`has: function(target, propertyName)`|`in` 运算符、[hasOwnProperty 方法 \(Object\)](../../javascript/reference/hasownproperty-method-object-javascript.md) 和其他方法的陷阱。|  
|`isExtensible: function(target)`|[Object.isExtensible 函数](../../javascript/reference/object-isextensible-function-javascript.md) 的陷阱。|  
|`ownKeys: function(target)`|[Object.getOwnPropertyNames 函数](../../javascript/reference/object-getownpropertynames-function-javascript.md) 的陷阱。|  
|`preventExtensions: function(target)`|[Object.preventExtensions 函数](../../javascript/reference/object-preventextensions-function-javascript.md) 的陷阱。|  
|`set: function(target, propertyName, value, receiver)`|任何 [setter](../../javascript/creating-objects-javascript.md) 属性的陷阱。|  
|`setPrototypeOf: function(target, prototype)`|[Object.setPrototypeOf](../../javascript/reference/object-setprototypeof-function-javascript.md) 的陷阱。|  
  
## 示例  
 以下代码示例展示了如何使用 `get` 陷阱为对象文本创建代理。  
  
```javascript  
var target = {};  
var handler = {  
  get: function (receiver, name) {  
    // This example includes a template string.  
    return `Hello, ${name}!`;  
  }  
};  
  
var p = new Proxy(target, handler);  
console.log(p.world);  
  
// Output:  
// Hello, world!  
  
```  
  
## 示例  
 以下代码示例展示了如何使用 `apply` 陷阱为函数创建代理。  
  
```javascript  
var target = function () { return 'I am the target'; };  
var handler = {  
  // This example includes a rest parameter.  
  apply: function (receiver, ...args) {  
    return 'I am the proxy';  
  }  
};  
  
var p = new Proxy(target, handler);  
console.log(target()):  
console.log(p()):  
  
// Output:  
// I am the target  
// I am the proxy  
```  
  
## 要求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]