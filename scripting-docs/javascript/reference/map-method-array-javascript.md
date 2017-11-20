---
title: "map 方法 (Array) (JavaScript) |Microsoft 文档"
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
- map method [JavaScript]
- arrays [JavaScript], map method
ms.assetid: 500dc4f8-d73d-4a28-a5b8-c9bd5674ea36
caps.latest.revision: "20"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 609d9c88000a7a30fe8edc03b52df032f7d19ba9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="map-method-array-javascript"></a>map 方法 (Array) (JavaScript)
对数组的每个元素调用定义的回调函数并返回包含结果的数组。  
  
## <a name="syntax"></a>语法  
  
```  
  
array1.map(callbackfn[, thisArg])  
```  
  
#### <a name="parameters"></a>参数  
  
|参数|定义|  
|---------------|----------------|  
|`array1`|必需。 一个数组对象。|  
|`callbackfn`|必需。 最多可以接受三个参数的函数。 对于数组中的每个元素，`map` 方法都会调用 `callbackfn` 函数一次。|  
|`thisArg`|可选。 `this` 函数中的 `callbackfn` 关键字可引用的对象。 如果省略 `thisArg`，则 `undefined` 将用作 `this` 值。|  
  
## <a name="return-value"></a>返回值  
 一个新数组，其中的每个元素均为关联的原始数组元素的回调函数返回值。  
  
## <a name="exceptions"></a>异常  
 如果 `callbackfn` 参数不是函数对象，则将引发 `TypeError` 异常。  
  
## <a name="remarks"></a>备注  
 对于数组中的每个元素，`map` 方法都会调用 `callbackfn` 函数一次（采用升序索引顺序）。 将不会为数组中缺少的元素调用回调函数。  
  
 除了数组对象之外，`map` 方法可由具有 `length` 属性且具有已按数字编制索引的属性名的任何对象使用。  
  
## <a name="callback-function-syntax"></a>回调函数语法  
 回调函数的语法如下所示：  
  
 `function callbackfn(value, index, array1)`  
  
 你可使用最多三个参数来声明回调函数。  
  
 下表列出了回调函数参数。  
  
|回调参数|定义|  
|-----------------------|----------------|  
|`value`|数组元素的值。|  
|`index`|数组元素的数字索引。|  
|`array1`|包含该元素的数组对象。|  
  
## <a name="modifying-the-array-object"></a>修改数组对象  
 数组对象可由回调函数修改。  
  
 下表描述了在 `map` 方法启动后修改数组对象所获得的结果。  
  
|`map` 方法启动后的条件|元素是否传递给回调函数？|  
|---------------------------------------------|------------------------------------------|  
|在数组的原始长度之外添加元素。|不可以。|  
|添加元素以填充数组中缺少的元素。|是，如果该索引尚未传递给回调函数。|  
|元素已更改。|是，如果该元素尚未传递给回调函数。|  
|从数组中删除元素。|否，除非该元素已传递给回调函数。|  
  
## <a name="example"></a>示例  
 下面的示例演示 `map` 方法的用法。  
  
```JavaScript  
// Define the callback function.  
function AreaOfCircle(radius) {  
    var area = Math.PI * (radius * radius);  
    return area.toFixed(0);  
}  
  
// Create an array.  
var radii = [10, 20, 30];  
  
// Get the areas from the radii.  
var areas = radii.map(AreaOfCircle);  
  
document.write(areas);  
  
// Output:  
// 314,1257,2827  
```  
  
## <a name="example"></a>示例  
 下面的示例阐释 `thisArg` 参数的用法，该参数指定 `this` 关键字可引用的对象。  
  
```JavaScript  
// Define an object that contains a divisor property and  
// a remainder function.  
var obj = {  
    divisor: 10,  
    remainder: function (value) {  
        return value % this.divisor;  
    }  
}  
  
// Create an array.  
var numbers = [6, 12, 25, 30];  
  
// Get the remainders.  
// The obj argument specifies the this value in the callback function.  
var result = numbers.map(obj.remainder, obj);  
document.write(result);  
  
// Output:  
// 6,2,5,0  
```  
  
## <a name="example"></a>示例  
 在下面的示例中，内置 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 方法用作回调函数。  
  
```JavaScript  
// Apply Math.sqrt(value) to each element in an array.  
var numbers = [9, 16];  
var result = numbers.map(Math.sqrt);  
  
document.write(result);  
// Output: 3,4  
```  
  
## <a name="example"></a>示例  
 `map` 方法可应用于一个字符串。 下面的示例阐释了这一点。  
  
```JavaScript  
// Define the callback function.  
function threeChars(value, index, str) {  
    // Create a string that contains the previous, current,  
    // and next character.  
    return str.substring(index - 1, index + 2);  
}  
  
// Create a string.  
var word = "Thursday";  
  
// Apply the map method to the string.  
// Each array element in the result contains a string that  
// has the previous, current, and next character.  
// The commented out statement shows an alternative syntax.  
var result = [].map.call(word, threeChars);  
// var result = Array.prototype.map.call(word, threeChars);  
  
document.write(result);  
  
// Output:  
// Th,Thu,hur,urs,rsd,sda,day,ay  
  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [JavaScript 方法](../../javascript/reference/javascript-methods.md)   
 [数组对象](../../javascript/reference/array-object-javascript.md)   
 [使用数组](../../javascript/advanced/using-arrays-javascript.md)   
 [filter 方法 (Array)](../../javascript/reference/filter-method-array-javascript.md)   
 [forEach 方法 (Array)](../../javascript/reference/foreach-method-array-javascript.md)   
 [Hilo JavaScript 示例应用程序 （Windows 应用商店）](http://hilojs.codeplex.com/SourceControl/latest)