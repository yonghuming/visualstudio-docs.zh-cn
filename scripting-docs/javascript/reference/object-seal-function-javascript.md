---
title: "Object.seal 函数 (JavaScript) |Microsoft 文档"
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
- Object.seal function
- seal function
ms.assetid: e72c804a-4dab-4ec9-b9df-9c9c908aa12d
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2dca9066be9a557b97a52ae749cecfb218504509
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="objectseal-function-javascript"></a>Object.seal 函数 (JavaScript)
防止修改现有属性的特性，并防止添加新属性。  
  
## <a name="syntax"></a>语法  
  
```JavaScript  
Object.seal(object)  
```  
  
#### <a name="parameters"></a>参数  
 `object`  
 必需。 对其锁定属性的对象。  
  
## <a name="return-value"></a>返回值  
 传递给函数的对象。  
  
## <a name="exceptions"></a>异常  
 如果`object`自变量不是一个对象，`TypeError`引发异常。  
  
## <a name="remarks"></a>备注  
 `Object.seal`函数执行下列两项内容：  
  
-   使得该对象不可扩展的以便不能将新属性添加到它。  
  
-   集`configurable`属性设为`false`的所有属性的对象。  
  
 当`configurable`属性是`false`属性特性不能更改，无法删除属性。 当`configurable`是`false`和`writable`是`true`、`value`和`writable`属性已发生更改。  
  
 `Object.seal`函数不会更改`writable`属性。  
  
 有关如何设置属性特性的详细信息，请参阅[Object.defineProperty 函数](../../javascript/reference/object-defineproperty-function-javascript.md)。 若要获取属性的特性，可以使用[Object.getOwnPropertyDescriptor 函数](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md)。  
  
## <a name="related-functions"></a>相关的函数  
 以下相关的函数防止修改对象属性。  
  
|函数|由非可扩展对象|`configurable`设置为`false`每个属性|`writable`设置为`false`每个属性|  
|--------------|------------------------------------|--------------------------------------------------------|----------------------------------------------------|  
|[Object.preventExtensions](../../javascript/reference/object-preventextensions-function-javascript.md)|是|No|No|  
|`Object.seal`|是|是|No|  
|[Object.freeze](../../javascript/reference/object-freeze-function-javascript.md)|是|是|是|  
  
 以下函数将返回`true`如果满足所有标记下表中的条件。  
  
|函数|对象是可扩展的？|`configurable`是`false`的所有属性？|`writable`是`false`的所有数据属性？|  
|--------------|---------------------------|---------------------------------------------------|----------------------------------------------------|  
|[Object.isExtensible](../../javascript/reference/object-isextensible-function-javascript.md)|是|No|No|  
|[Object.isSealed](../../javascript/reference/object-issealed-function-javascript.md)|No|是|No|  
|[Object.isFrozen](../../javascript/reference/object-isfrozen-function-javascript.md)|No|是|是|  
  
## <a name="example"></a>示例  
 下面的示例阐释了 `Object.seal` 函数的用法。  
  
```JavaScript  
// Create an object that has two properties.  
var obj = { pasta: "spaghetti", length: 10 };  
// Seal the object.  
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
 [Object.freeze 函数](../../javascript/reference/object-freeze-function-javascript.md)   
 [Object.isExtensible 函数](../../javascript/reference/object-isextensible-function-javascript.md)   
 [Object.isSealed 函数](../../javascript/reference/object-issealed-function-javascript.md)   
 [Object.isFrozen 函数](../../javascript/reference/object-isfrozen-function-javascript.md)