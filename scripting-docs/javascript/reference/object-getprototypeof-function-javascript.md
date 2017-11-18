---
title: "Object.getPrototypeOf 函数 (JavaScript) |Microsoft 文档"
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
- getPrototypeOf function [JavaScript]
- Object.getPrototypeOf function [JavaScript]
ms.assetid: 1c59cd7a-a7e2-4c5c-83ec-e6bd2b104d9f
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0c752c57fcc47192bb43790b2e93dd74fcdfbb65
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="objectgetprototypeof-function-javascript"></a>Object.getPrototypeOf 函数 (JavaScript)
返回某个对象的原型。  
  
## <a name="syntax"></a>语法  
  
```JavaScript  
Object.getPrototypeOf(object)  
```  
  
#### <a name="parameters"></a>参数  
 `object`  
 必需。 引用原型的对象。  
  
## <a name="return-value"></a>返回值  
 原型`object`自变量。 原型也是一个对象。  
  
## <a name="exceptions"></a>异常  
 如果`object`自变量不是一个对象，`TypeError`引发异常。  
  
## <a name="example"></a>示例  
 下面的示例阐释了 `Object.getPrototypeOf` 函数的用法。  
  
```JavaScript  
// Create a constructor function.  
function Pasta(grain, width) {  
    this.grain = grain;  
    this.width = width;  
}  
// Create an object from the pasta constructor.  
var spaghetti = new Pasta("wheat", 0.2);  
  
// Obtain the prototype from the object.  
var proto = Object.getPrototypeOf(spaghetti);  
  
// Add a property to the prototype and validate that  
// the original object has the property.  
proto.foodgroup = "carbohydrates";  
document.write(spaghetti.foodgroup + " ");  
  
// Verify that the prototype obtained from the object  
// is the same as the prototype of the constructor.  
var result = (proto === Pasta.prototype);  
document.write(result + " ");  
  
// Verify that prototype obtained from the object  
// is a prototype of the original object.  
var result = proto.isPrototypeOf(spaghetti);  
document.write(result);  
  
// Output: carbohydrates true true  
```  
  
## <a name="example"></a>示例  
 下面的示例使用`Object.getPrototypeOf`函数来验证数据类型。  
  
```JavaScript  
var reg = /a/;  
var result = (Object.getPrototypeOf(reg) === RegExp.prototype);  
document.write(result + " ");  
  
var err = new Error("an error");  
var result = (Object.getPrototypeOf(err) === Error.prototype);  
document.write(result);  
  
// Output: true true  
  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [prototype 属性 （对象）](../../javascript/reference/prototype-property-object-javascript.md)   
 [isPrototypeOf 方法 (Object)](../../javascript/reference/isprototypeof-method-object-javascript.md)