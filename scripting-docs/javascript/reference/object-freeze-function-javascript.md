---
title: "Object.freeze 函数 (JavaScript) |Microsoft 文档"
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
- Object.freeze function
- freeze function
ms.assetid: 83ffe193-0a37-4e0c-9b66-44c422765fb3
caps.latest.revision: "20"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ec08b34c3c8b32245928e6e75f5df1fbdfe2d4a6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="objectfreeze-function-javascript"></a>Object.freeze 函数 (JavaScript)
防止修改现有属性的特性和值，并防止添加新属性。  
  
## <a name="syntax"></a>语法  
  
```JavaScript  
Object.freeze(object)  
```  
  
#### <a name="parameters"></a>参数  
 `object`  
 必需。 对其锁定属性的对象。  
  
## <a name="return-value"></a>返回值  
 传递给函数的对象。  
  
## <a name="exceptions"></a>异常  
 如果`object`自变量不是一个对象，`TypeError`引发异常。  
  
## <a name="remarks"></a>备注  
 `Object.freeze`函数执行下列任务：  
  
-   使得该对象不可扩展的以便不能将新属性添加到它。  
  
-   集`configurable`属性设为`false`的所有属性的对象。 当`configurable`是`false`，无法更改属性特性，并且无法删除属性。  
  
-   集`writable`属性设为`false`的所有数据属性的对象。 当`writable`为 false，不能更改数据属性值。  
  
 有关如何设置属性特性的详细信息，请参阅[Object.defineProperty 函数](../../javascript/reference/object-defineproperty-function-javascript.md)。 若要获取属性的特性，可以使用[Object.getOwnPropertyDescriptor 函数](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md)。  
  
## <a name="related-functions"></a>相关的函数  
 以下相关的函数防止修改对象属性。  
  
|函数|由非可扩展对象|`configurable`设置为`false`每个属性|`writable`设置为`false`每个属性|  
|--------------|------------------------------------|--------------------------------------------------------|----------------------------------------------------|  
|[Object.preventExtensions](../../javascript/reference/object-preventextensions-function-javascript.md)|是|No|No|  
|[Object.seal](../../javascript/reference/object-seal-function-javascript.md)|是|是|No|  
|`Object.freeze`|是|是|是|  
  
 以下函数将返回`true`如果满足所有标记下表中的条件。  
  
|函数|对象是可扩展的？|`configurable`是`false`的所有属性？|`writable`是`false`的所有数据属性？|  
|--------------|---------------------------|---------------------------------------------------|----------------------------------------------------|  
|[Object.isExtensible](../../javascript/reference/object-isextensible-function-javascript.md)|是|No|No|  
|[Object.isSealed](../../javascript/reference/object-issealed-function-javascript.md)|No|是|是|  
|[Object.isFrozen](../../javascript/reference/object-isfrozen-function-javascript.md)|No|是|是|  
  
## <a name="example"></a>示例  
 下面的示例阐释了 `Object.freeze` 函数的用法。  
  
```JavaScript  
// Create an object that has two properties.  
var obj = { pasta: "spaghetti", length: 10 };  
  
// Freeze the object.  
Object.freeze(obj);  
  
// Try to add a new property, and then verify that it is not added.   
    obj.newProp = 50;  
    document.write(obj.newProp);  
    document.write("<br/>");  
  
// Try to delete a property, and then verify that it is still present.   
delete obj.length;  
document.write(obj.length);  
document.write("<br/>");  
  
// Try to change a property value, and then verify that it is not changed.   
obj.pasta = "linguini";  
document.write(obj.pasta);  
  
// Output:  
// undefined  
// 10  
// spaghetti  
  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [Object.preventExtensions 函数](../../javascript/reference/object-preventextensions-function-javascript.md)   
 [Object.seal 函数](../../javascript/reference/object-seal-function-javascript.md)   
 [Object.isExtensible 函数](../../javascript/reference/object-isextensible-function-javascript.md)   
 [Object.isSealed 函数](../../javascript/reference/object-issealed-function-javascript.md)   
 [Object.isFrozen 函数](../../javascript/reference/object-isfrozen-function-javascript.md)