---
title: "Object.create 函数 (JavaScript) |Microsoft 文档"
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
- create function [JavaScript]
- Object.create function [JavaScript]
ms.assetid: 0ad31f36-a9ee-444e-b0fe-c87843d03196
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f359908c5c836743e22390580f542df27d7b98e7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="objectcreate-function-javascript"></a>Object.create 函数 (JavaScript)
创建具有指定的原型，并可选择包含指定的属性的对象。  
  
## <a name="syntax"></a>语法  
  
```  
Object.create(prototype, descriptors)  
```  
  
#### <a name="parameters"></a>参数  
 `prototype`  
 必需。 要用作原型的对象。 可为 `null`。  
  
 `descriptors`  
 可选。 A[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]包含一个或多个属性描述符的对象。  
  
 数据属性是可以获取和设置值的属性。 数据属性描述符包含`value`属性，加上`writable`， `enumerable`，和`configurable`属性。 如果未指定的最后三个特性，它们将默认为`false`。 *访问器属性*每次的值是检索或设置调用用户提供的函数。 访问器属性描述符包含`set`属性，`get`和 / 或属性。 有关详细信息，请参阅[Object.defineProperty 函数](../../javascript/reference/object-defineproperty-function-javascript.md)。  
  
## <a name="return-value"></a>返回值  
 具有指定的内部原型以及包含指定的属性，如果任何新对象。  
  
## <a name="exceptions"></a>异常  
 A`TypeError`如果以下任何条件为 true 将引发异常：  
  
-   `prototype`参数不是一个对象，不是`null`。  
  
-   中的描述符`descriptors`自变量具有`value`或`writable`特性，并且具有`get`或`set`属性。  
  
-   中的描述符`descriptors`自变量具有`get`或`set`不是函数的属性。  
  
## <a name="remarks"></a>备注  
 你可以使用此函数使用`null``prototype`参数，以停止原型链。 创建的对象将具有任何原型。  
  
## <a name="example"></a>示例  
 下面的示例创建对象使用`null`原型，并将添加两个的可枚举属性。  
  
```JavaScript  
var newObj = Object.create(null, {  
            size: {  
                value: "large",  
                enumerable: true  
            },  
            shape: {  
                value: "round",  
                enumerable: true  
            }  
        });  
  
document.write(newObj.size + "<br/>");  
document.write(newObj.shape + "<br/>");  
document.write(Object.getPrototypeOf(newObj));  
  
// Output:  
// large  
// round  
// null  
  
```  
  
## <a name="example"></a>示例  
 下面的示例创建具有相同的内部原型为对象对象的对象。 你可以看到它具有作为通过使用对象文本创建的对象相同的原型。 [Object.getPrototypeOf](../../javascript/reference/object-getprototypeof-function-javascript.md)函数获取原始对象的原型。 若要获取的对象的属性描述符，可以使用[Object.getOwnPropertyDescriptor 函数](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md)。  
  
```JavaScript  
var firstLine = { x: undefined, y: undefined };  
  
var secondLine = Object.create(Object.prototype, {  
        x: {  
                value: undefined,   
                writable: true,   
                configurable: true,   
                enumerable: true  
            },  
            y: {  
                value: undefined,   
                writable: true,   
                configurable: true,   
                enumerable: true  
            }  
});  
  
document.write("first line prototype = " + Object.getPrototypeOf(firstLine));  
document.write("<br/>");  
document.write("second line prototype = " + Object.getPrototypeOf(secondLine));  
  
// Output:  
// first line prototype = [object Object]  
// second line prototype = [object Object]  
```  
  
## <a name="example"></a>示例  
 下面的示例创建具有相同的内部原型作为 Shape 对象的对象。  
  
```JavaScript  
  
// Create the shape object.  
var Shape = { twoDimensional: true, color: undefined, hasLineSegments: undefined };  
  
var Square = Object.create(Object.getPrototypeOf(Shape));  
  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [Object.getPrototypeOf 函数](../../javascript/reference/object-getprototypeof-function-javascript.md)   
 [isPrototypeOf 方法 (Object)](../../javascript/reference/isprototypeof-method-object-javascript.md)   
 [创建对象](../../javascript/creating-objects-javascript.md)