---
title: "Object.keys 函数 (JavaScript) |Microsoft 文档"
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
- Object.keys method [JavaScript]
- keys method [JavaScript]
ms.assetid: cf4a7daf-cf28-4467-bc6b-f7f106ec3876
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0e725c3ab7206b04d9a900cb614b57c37dfc4351
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="objectkeys-function-javascript"></a>Object.keys 函数 (JavaScript)
返回对象的可枚举属性和方法的名称。  
  
## <a name="syntax"></a>语法  
  
```JavaScript  
Object.keys(object)  
```  
  
#### <a name="parameters"></a>参数  
  
|参数|定义|  
|---------------|----------------|  
|`object`|必需。 包含的属性和方法的对象。 这可以是你创建的对象或现有的文档对象模型 (DOM) 对象。|  
  
## <a name="return-value"></a>返回值  
 一个数组，包含可枚举属性的名称和对象的方法。  
  
## <a name="exceptions"></a>异常  
 如果为值提供`object`参数不是对象的名称`TypeError`引发异常。  
  
## <a name="remarks"></a>备注  
 `keys`方法返回仅的可枚举属性和方法的名称。 若要返回的可枚举和非可枚举属性和方法的名称，可以使用[Object.getOwnPropertyNames 函数](../../javascript/reference/object-getownpropertynames-function-javascript.md)。  
  
 璝惠`enumerable`属性的属性，请参阅[Object.defineProperty 函数](../../javascript/reference/object-defineproperty-function-javascript.md)和[Object.getOwnPropertyDescriptor 函数](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md)。  
  
## <a name="example"></a>示例  
 下面的示例创建具有三个属性和方法的对象。 然后，它使用`keys`方法以获取的属性和方法的对象。  
  
```JavaScript  
// Create a constructor function.  
function Pasta(grain, width, shape) {  
    this.grain = grain;  
    this.width = width;  
    this.shape = shape;  
  
    // Define a method.  
    this.toString = function () {  
        return (this.grain + ", " + this.width + ", " + this.shape);  
    }  
}  
  
// Create an object.  
var spaghetti = new Pasta("wheat", 0.2, "circle");  
  
// Put the enumerable properties and methods of the object in an array.  
var arr = Object.keys(spaghetti);  
document.write (arr);  
  
// Output:  
// grain,width,shape,toString  
```  
  
## <a name="example"></a>示例  
 下面的示例显示 Pasta 对象中的"g"字母开头的所有可枚举属性的名称。  
  
```JavaScript  
// Create a constructor function.  
function Pasta(grain, width, shape) {  
    this.grain = grain;  
    this.width = width;  
    this.shape = shape;  
}  
  
var polenta = new Pasta("corn", 1, "mush");  
  
var keys = Object.keys(polenta).filter(CheckKey);  
document.write(keys);  
  
// Check whether the first character of a string is "g".  
function CheckKey(value) {  
    var firstChar = value.substr(0, 1);  
    if (firstChar.toLowerCase() == "g")  
        return true;  
    else  
        return false;  
}  
  
// Output:  
// grain  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [Object.getOwnPropertyNames 函数](../../javascript/reference/object-getownpropertynames-function-javascript.md)