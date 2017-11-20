---
title: "Object.getOwnPropertyNames 函数 (JavaScript) |Microsoft 文档"
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
- getOwnPropertyNames method [JavaScript]
- Object.getOwnPropertyNames method [JavaScript]
ms.assetid: 59f4b6b1-02be-44b3-a06c-a5ca8f70c3d8
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 76ca0036b9dedf7b4cee7b543469939e35dfe8d1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="objectgetownpropertynames-function-javascript"></a>Object.getOwnPropertyNames 函数 (JavaScript)
返回的对象的自己的属性的名称。 对象的自己的属性是那些直接对该对象定义的不会从对象的原型继承。 对象的属性包括字段 （对象） 和函数。  
  
## <a name="syntax"></a>语法  
  
```JavaScript  
Object.getOwnPropertyNames(object)  
```  
  
#### <a name="parameters"></a>参数  
  
|参数|定义|  
|---------------|----------------|  
|`object`|必需。 包含自己的属性的对象。|  
  
## <a name="return-value"></a>返回值  
 一个数组，包含该对象的自己的属性的名称。  
  
## <a name="exceptions"></a>异常  
 如果为值提供`object`参数不是对象的名称`TypeError`引发异常。  
  
## <a name="remarks"></a>备注  
 `getOwnPropertyNames`方法返回的可枚举和非可枚举属性和方法的名称。 若要返回只有名称的可枚举属性和方法的名称，可以使用[Object.keys 函数](../../javascript/reference/object-keys-function-javascript.md)。  
  
## <a name="example"></a>示例  
 下面的示例创建具有三个属性和方法的对象。 然后，它使用`getOwnPropertyNames`方法来获取该对象的自身属性 （包括方法）。  
  
```JavaScript  
function Pasta(grain, width, shape) {  
    // Define properties.  
    this.grain = grain;  
    this.width = width;  
    this.shape = shape;  
    this.toString = function () {  
        return (this.grain + ", " + this.width + ", " + this.shape);  
    }  
}  
  
// Create an object.  
var spaghetti = new Pasta("wheat", 0.2, "circle");  
  
// Get the own property names.  
var arr = Object.getOwnPropertyNames(spaghetti);  
document.write (arr);  
  
// Output:  
//   grain,width,shape,toString  
```  
  
## <a name="example"></a>示例  
 下面的示例显示的字母开头的属性名称中**复式**对象使用构造**Pasta**构造函数。  
  
```JavaScript  
function Pasta(grain, size, shape) {  
    this.grain = grain;   
    this.size = size;   
    this.shape = shape;   
}  
  
var spaghetti = new Pasta("wheat", 2, "circle");  
  
var names = Object.getOwnPropertyNames(spaghetti).filter(CheckKey);  
document.write(names);   
  
// Check whether the first character of a string is 's'.   
function CheckKey(value) {  
    var firstChar = value.substr(0, 1);   
    if (firstChar.toLowerCase() == 's')  
        return true;   
    else  
         return false;   
}  
// Output:  
// size,shape  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [Object.keys 函数](../../javascript/reference/object-keys-function-javascript.md)