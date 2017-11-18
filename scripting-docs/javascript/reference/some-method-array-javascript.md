---
title: "some 方法 (Array) (JavaScript) |Microsoft 文档"
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
- arrays [JavaScript], some method
- some method [JavaScript]
ms.assetid: 7b6822f9-c406-4f4e-bfec-a93459745992
caps.latest.revision: "18"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ba3f855c61daac511bcf7aca6b47f643dda93313
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="some-method-array-javascript"></a>some 方法 (Array) (JavaScript)
确定指定的回调函数是否返回`true`数组的任何元素。  
  
## <a name="syntax"></a>语法  
  
```  
  
array1.some(callbackfn[, thisArg])  
```  
  
#### <a name="parameters"></a>参数  
  
|参数|定义|  
|---------------|----------------|  
|`array1`|必需。 一个数组对象。|  
|`callbackfn`|必需。 最多可以接受三个参数的函数。 `some`方法调用`callbackfn`中每个元素的函数`array1`直到`callbackfn`返回`true`，或直至数组的末尾。|  
|`thisArg`|可选。 `this` 函数中的 `callbackfn` 关键字可引用的对象。 如果省略 `thisArg`，则 `undefined` 将用作 `this` 值。|  
  
## <a name="return-value"></a>返回值  
 `true`如果`callbackfn`函数返回`true`任何数组元素; 否则为`false`。  
  
## <a name="exceptions"></a>异常  
 如果 `callbackfn` 参数不是函数对象，则将引发 `TypeError` 异常。  
  
## <a name="remarks"></a>备注  
 `some`方法调用`callbackfn`函数对每个数组元素，直到升序索引顺序`callbackfn`函数返回`true`。 如果元素导致`callbackfn`返回`true`找到，则`some`方法立即返回`true`。 如果回调不返回`true`上任何元素，`some`方法返回`false`。  
  
 将不会为数组中缺少的元素调用回调函数。  
  
 除了数组对象之外，`some` 方法可由具有 `length` 属性且具有已按数字编制索引的属性名的任何对象使用。  
  
> [!NOTE]
>  你可以使用[every 方法 (Array)](../../javascript/reference/every-method-array-javascript.md)若要检查的回调函数是否返回`true`的数组的所有元素。  
  
## <a name="callback-function-syntax"></a>回调函数语法  
 回调函数的语法如下所示：  
  
 `function callbackfn(value, index, array1)`  
  
 你可以声明具有最多三个参数的回调函数。  
  
 下表列出了回调函数参数。  
  
|回调参数|定义|  
|------------------------|----------------|  
|`value`|数组元素的值。|  
|`index`|数组元素的数字索引。|  
|`array1`|包含该元素的数组对象。|  
  
## <a name="modifying-the-array-object"></a>修改数组对象  
 数组对象可由回调函数修改。  
  
 下表描述了在 `some` 方法启动后修改数组对象所获得的结果。  
  
|`some` 方法启动后的条件|元素是否传递给回调函数？|  
|----------------------------------------------|------------------------------------------|  
|在数组的原始长度之外添加元素。|不可以。|  
|添加元素以填充数组中缺少的元素。|是，如果该索引尚未传递给回调函数。|  
|元素已更改。|是，如果该元素尚未传递给回调函数。|  
|从数组中删除元素。|否，除非该元素已传递给回调函数。|  
  
## <a name="example"></a>示例  
 下面的示例使用`some`要找出任何元素在数组中的方法为偶数。  
  
```JavaScript  
// The callback function.  
function CheckIfEven(value, index, ar) {  
    if (value % 2 == 0)  
        return true;  
}  
  
var numbers = [1, 15, 4, 10, 11, 22];  
  
var evens = numbers.some(CheckIfEven);  
document.write(evens);  
  
// Output:  
// true  
```  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用`thisArg`参数，指定的对象`this`关键字可引用。 它会检查任何数组中的数字是否超出提供传递的对象的范围  
  
```JavaScript  
// Create a function that returns true if the value is   
// outside the range.  
var isOutsideRange = function (value) {  
    return value < this.minimum || value > this.maximum;  
}  
  
// Create an array of numbers.  
var numbers = [6, 12, 16, 22, -12];  
  
// The range object is to be the 'this' object.  
var range = { minimum: 10, maximum: 20 };  
  
document.write(numbers.some(isOutsideRange, range));  
  
// Output: true  
  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [every 方法 (Array)](../../javascript/reference/every-method-array-javascript.md)   
 [filter 方法 (Array)](../../javascript/reference/filter-method-array-javascript.md)   
 [map 方法 (Array)](../../javascript/reference/map-method-array-javascript.md)