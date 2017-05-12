---
title: "Reflect 对象 (JavaScript) | Microsoft Docs"
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
ms.assetid: 1df74f34-2eb4-42f1-a930-b943c86daa0e
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Reflect 对象 (JavaScript)
提供在截获的操作中使用的方法。  
  
## 语法  
  
```  
Reflect.[method]  
```  
  
#### 参数  
 `method`  
 必需。  `Reflect` 对象的某一个方法的名称。  
  
## 备注  
 不能使用 `new` 运算符实例化 Reflect 对象。  
  
 Reflect 方法通常与[代理](../../javascript/reference/proxy-object-javascript.md)一起使用，因为后者允许你委托默认行为而无需在代码中实现该默认行为。  
  
 Reflect 提供与每个代理陷阱具有相同名称的静态方法。  表中的描述并不详尽。  
  
|方法|描述|  
|--------|--------|  
|`Reflect.apply(target, thisArg, args)`|类似于 Function 对象的 [apply](../../javascript/reference/apply-method-function-javascript.md) 方法。|  
|`Reflect.construct(target, args)`|等效于 `new` 运算符的函数。|  
|`Reflect.defineProperty(target, propertyName, descriptor)`|类似于 [Object.defineProperty](../../javascript/reference/object-defineproperty-function-javascript.md)。  返回一个布尔值，该值指示调用是否成功。|  
|`Reflect.deleteProperty(target, propertyName)`|类似于 `delete` 语句。  返回一个布尔值，该值指示调用是否成功。|  
|`Reflect.enumerate(target)`|类似于 [for…in](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md) 语句，[Object.getOwnPropertySymbols](../../javascript/reference/object-getownpropertysymbols-function-javascript.md)、[Object.keys](../../javascript/reference/object-keys-function-javascript.md) 函数和 [JSON.stringify](../../javascript/reference/json-stringify-function-javascript.md)。|  
|`Reflect.get(target, propertyName, receiver)`|等效于任何 [getter](../../javascript/creating-objects-javascript.md) 属性的函数。|  
|`Reflect.getOwnPropertyDescriptor(target, propertyName)`|类似于 [Object.getOwnPropertyDescriptor](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md)。  返回一个布尔值，该值指示调用是否成功。|  
|`Reflect.getPrototypeOf(target)`|类似于 [Object.getPrototypeOf](../../javascript/reference/object-getprototypeof-function-javascript.md)。|  
|`Reflect.has(target, propertyName)`|类似于 `in` 运算符、[hasOwnProperty 方法 \(Object\)](../../javascript/reference/hasownproperty-method-object-javascript.md) 和其他方法。  返回一个布尔值，该值指示调用是否成功。|  
|`Reflect.isExtensible(target)`|类似于 [Object.isExtensible](../../javascript/reference/object-isextensible-function-javascript.md)。|  
|`Reflect.ownKeys(target)`|类似于 [Object.getOwnPropertyNames](../../javascript/reference/object-getownpropertynames-function-javascript.md)。|  
|`Reflect.preventExtensions(target)`|类似于 [Object.preventExtensions](../../javascript/reference/object-preventextensions-function-javascript.md)。  返回一个布尔值，该值指示调用是否成功。|  
|`Reflect.set(target, propertyName, value, receiver)`|类似于使用任何 [setter](../../javascript/creating-objects-javascript.md) 属性。  返回一个布尔值，该值指示调用是否成功。|  
|`Reflect.setPrototypeOf(target, prototype)`|类似于 [Object.setPrototypeOf](../../javascript/reference/object-setprototypeof-function-javascript.md)。  返回一个布尔值，该值指示调用是否成功。|  
  
## 示例  
 下面的代码示例演示如何使用 `Reflect.get` 编写代理，该代理可阻止对以下划线开头的属性的 GET 操作。  
  
```javascript  
var p = new Proxy({}, {  
    get(k, t, r) {  
        // return undefined if key begins with underscore  
        if(k[0] === '_') return undefined;  
  
       // otherwise do default behavior  
       return Reflect.get(k, t, r);  
    }  
});  
  
p._foo = 1;  
console.log(p._foo);  
  
p.foo = 1;  
console.log(p.foo);  
  
// Output:  
// undefined  
// 1  
  
```  
  
## 要求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]