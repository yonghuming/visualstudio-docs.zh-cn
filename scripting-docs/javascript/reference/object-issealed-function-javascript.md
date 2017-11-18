---
title: "Object.isSealed 函数 (JavaScript) |Microsoft 文档"
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
- properties [JavaScript], locking attributes
- isSealed function [JavaScript]
- Object.isSealed [JavaScript]
ms.assetid: af4f192e-cebe-44b9-8eef-90c096f5ae8f
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4d3b9cb603a456382e3b23e6f7d0037063027b98
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="objectissealed-function-javascript"></a>Object.isSealed 函数 (JavaScript)
如果无法在对象中修改现有属性特性，并且无法将新属性添加到对象，则返回 `true`。  
  
## <a name="syntax"></a>语法  
  
```JavaScript  
Object.isSealed(object)  
```  
  
#### <a name="parameters"></a>参数  
 `object`  
 必需。 要测试的对象。  
  
## <a name="return-value"></a>返回值  
 `true`如果这两个以下条件：  
  
-   对象是不可扩展的指示不能将新属性添加到对象。  
  
-   `configurable`属性是`false`的所有现有属性。  
  
 如果对象不具有任何属性，该函数将返回`true`的对象是否不可扩展。  
  
## <a name="exceptions"></a>异常  
 如果`object`自变量不是一个对象，`TypeError`引发异常。  
  
## <a name="remarks"></a>备注  
 当`configurable`属性的属性`false`，无法更改属性特性，并且无法删除属性。 当`writable`是`false`，不能更改数据属性值。 当`configurable`是`false`和`writable`是`true`、`value`和`writable`属性已发生更改。  
  
 `Object.isSealed`函数不使用`writable`属性来确定其返回值的属性。  
  
 有关如何设置属性特性的信息，请参阅[Object.defineProperty 函数](../../javascript/reference/object-defineproperty-function-javascript.md)。 若要获取属性的特性，可以使用[Object.getOwnPropertyDescriptor 函数](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md)。  
  
## <a name="related-functions"></a>相关的函数  
 以下相关的函数防止修改对象属性。  
  
|函数|由非可扩展对象|`configurable`设置为`false`每个属性|`writable`设置为`false`每个属性|  
|--------------|------------------------------------|--------------------------------------------------------|----------------------------------------------------|  
|[Object.preventExtensions](../../javascript/reference/object-preventextensions-function-javascript.md)|是|No|No|  
|[Object.seal](../../javascript/reference/object-seal-function-javascript.md)|是|是|No|  
|[Object.freeze](../../javascript/reference/object-freeze-function-javascript.md)|是|是|是|  
  
 以下函数将返回`true`如果满足所有标记下表中的条件。  
  
|函数|对象是可扩展的？|`configurable`是`false`的所有属性？|`writable`是`false`的所有数据属性？|  
|--------------|---------------------------|---------------------------------------------------|----------------------------------------------------|  
|[Object.isExtensible](../../javascript/reference/object-isextensible-function-javascript.md)|是|No|No|  
|`Object.isSealed`|No|是|No|  
|[Object.isFrozen](../../javascript/reference/object-isfrozen-function-javascript.md)|No|是|是|  
  
## <a name="example"></a>示例  
 下面的示例阐释了 `Object.isSealed` 函数的用法。  
  
```JavaScript  
// Create an object that has two properties.  
var obj = { pasta: "spaghetti", length: 10 };  
  
// Seal the object, and verify that it is sealed.  
Object.seal(obj);  
document.write(Object.isSealed(obj));  
document.write("<br/>");  
  
// Try to add a new property, and then verify that it is not added.   
obj.newProp = 50;  
document.write(obj.newProp);  
document.write("<br/>");  
  
// Try to delete a property, and then verify that it is still present.   
delete obj.length;  
document.write(obj.length);  
  
// Output:  
// true  
// undefined  
// 10  
  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [Object.preventExtensions 函数](../../javascript/reference/object-preventextensions-function-javascript.md)   
 [Object.seal 函数](../../javascript/reference/object-seal-function-javascript.md)   
 [Object.freeze 函数](../../javascript/reference/object-freeze-function-javascript.md)   
 [Object.isExtensible 函数](../../javascript/reference/object-isextensible-function-javascript.md)   
 [Object.isFrozen 函数](../../javascript/reference/object-isfrozen-function-javascript.md)   
 [Object.defineProperty 函数](../../javascript/reference/object-defineproperty-function-javascript.md)   
 [Object.getOwnPropertyDescriptor 函数](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md)