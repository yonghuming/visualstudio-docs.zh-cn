---
title: "代理对象 (JavaScript) |Microsoft 文档"
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
ms.assetid: 2b89abee-04fa-47e6-9676-980016cff5f8
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 489d329528e88c27df03ca0e6d6d1608a39446e1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="proxy-object-javascript"></a>代理对象 (JavaScript)
为对象启用自定义行为。  
  
## <a name="syntax"></a>语法  
  
```  
proxyObj = new Proxy(target, handler)  
```  
  
#### <a name="parameters"></a>参数  
 `target`  
 必需。 将通过代理虚拟化的对象或函数。  
  
 `handler`  
 必需。 具有可实现自定义行为的方法（陷阱）的对象。  
  
## <a name="remarks"></a>备注  
 `Proxy` 对象用于截获对另一个对象执行的内部低级别操作。 代理对象可以用于拦截、对象虚拟化、日志记录/分析和其他用途。  
  
 如果尚未在代理的处理程序中定义特定操作陷阱，该操作将转发至目标。  
  
 处理程序对象可定义以下方法（陷阱）来实现自定义行为。 此处所列示例并非全部示例。 若要支持有条件的默认行为中的处理程序方法，使用的方法[反映对象](../../javascript/reference/reflect-object-javascript.md)。  
  
|处理程序方法（陷阱）语法|用法示例|  
|------------------------------------|-----------------------|  
|`apply: function(target, thisArg, args)`|函数调用陷阱。|  
|`construct: function(target, args)`|构造函数陷阱。|  
|`defineProperty: function(target, propertyName, descriptor)`|陷阱[Object.defineProperty 函数](../../javascript/reference/object-defineproperty-function-javascript.md)。|  
|`deleteProperty: function(target, propertyName)`|`delete` 语句的陷阱。|  
|`enumerate: function(target)`|陷阱[为..中](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)语句， [Object.getOwnPropertySymbols](../../javascript/reference/object-getownpropertysymbols-function-javascript.md)， [Object.keys](../../javascript/reference/object-keys-function-javascript.md)函数，和[JSON.stringify](../../javascript/reference/json-stringify-function-javascript.md)。|  
|`get: function(target, propertyName, receiver)`|任何的陷阱[getter](../../javascript/creating-objects-javascript.md)属性。|  
|`getOwnPropertyDescriptor: function(target, propertyName)`|陷阱[Object.getOwnPropertyDescriptor 函数](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md)。|  
|`getPrototypeOf: function(target)`|陷阱[Object.getPrototypeOf 函数](../../javascript/reference/object-getprototypeof-function-javascript.md)。|  
|`has: function(target, propertyName)`|陷阱`in`运算符， [hasOwnProperty 方法 (Object)](../../javascript/reference/hasownproperty-method-object-javascript.md)，和其他方法。|  
|`isExtensible: function(target)`|陷阱[Object.isExtensible 函数](../../javascript/reference/object-isextensible-function-javascript.md)。|  
|`ownKeys: function(target)`|陷阱[Object.getOwnPropertyNames 函数](../../javascript/reference/object-getownpropertynames-function-javascript.md)。|  
|`preventExtensions: function(target)`|陷阱[Object.preventExtensions 函数](../../javascript/reference/object-preventextensions-function-javascript.md)。|  
|`set: function(target, propertyName, value, receiver)`|任何的陷阱[setter](../../javascript/creating-objects-javascript.md)属性。|  
|`setPrototypeOf: function(target, prototype)`|陷阱[Object.setPrototypeOf](../../javascript/reference/object-setprototypeof-function-javascript.md)。|  
  
## <a name="example"></a>示例  
 以下代码示例展示了如何使用 `get` 陷阱为对象文本创建代理。  
  
```JavaScript  
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
  
## <a name="example"></a>示例  
 以下代码示例展示了如何使用 `apply` 陷阱为函数创建代理。  
  
```JavaScript  
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
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]