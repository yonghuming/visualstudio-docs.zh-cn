---
title: "every 方法 (Array) (JavaScript) |Microsoft 文档"
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
- every method
- arrays [JavaScript], every method
ms.assetid: dc4ee2f8-fb9e-4c9f-af5a-fe836e40ddd1
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4a05263ae45df61c47a3580d474863c8d4ff3dd1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="every-method-array-javascript"></a>every 方法 (Array) (JavaScript)
确定数组的所有成员是否都满足指定的测试。  
  
## <a name="syntax"></a>语法  
  
```  
  
array1.every(callbackfn[, thisArg])  
```  
  
#### <a name="parameters"></a>参数  
  
|参数|定义|  
|---------------|----------------|  
|`array1`|必需。 一个数组对象。|  
|`callbackfn`|必需。 最多可以接受三个参数的函数。 `every`方法调用`callbackfn`中每个元素的函数`array1`直到`callbackfn`返回`false`，或直至数组的末尾。|  
|`thisArg`|可选。 `this` 函数中的 `callbackfn` 关键字可引用的对象。 如果省略 `thisArg`，则 `undefined` 将用作 `this` 值。|  
  
## <a name="return-value"></a>返回值  
 `true`如果`callbackfn`函数返回`true`对于所有数组元素; 否则为`false`。 如果数组为没有元素，`every`方法返回`true`。  
  
## <a name="exceptions"></a>异常  
 如果 `callbackfn` 参数不是函数对象，则将引发 `TypeError` 异常。  
  
## <a name="remarks"></a>备注  
 `every`方法调用`callbackfn`函数中每个数组元素，直到升序索引顺序，一次`callbackfn`函数返回`false`。 如果元素导致`callbackfn`返回`false`找到，则`every`方法立即返回`false`。 否则为`every`方法返回`true`。  
  
 将不会为数组中缺少的元素调用回调函数。  
  
 除了数组对象之外，`every` 方法可由具有 `length` 属性且具有已按数字编制索引的属性名的任何对象使用。  
  
> [!NOTE]
>  你可以使用[some 方法 (Array)](../../javascript/reference/some-method-array-javascript.md)若要检查的回调函数是否返回`true`数组的任何元素。  
  
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
  
 下表描述了在 `every` 方法启动后修改数组对象所获得的结果。  
  
|`every` 方法启动后的条件|元素是否传递给回调函数？|  
|-----------------------------------------------|------------------------------------------|  
|在数组的原始长度之外添加元素。|不可以。|  
|添加元素以填充数组中缺少的元素。|是，如果该索引尚未传递给回调函数。|  
|元素已更改。|是，如果该元素尚未传递给回调函数。|  
|从数组中删除元素。|否，除非该元素已传递给回调函数。|  
  
## <a name="example"></a>示例  
 下面的示例演示 `every` 方法的用法。  
  
```JavaScript  
// Define the callback function.  
function CheckIfEven(value, index, ar) {  
    document.write(value + " ");  
  
    if (value % 2 == 0)  
        return true;  
    else  
        return false;  
}  
  
// Create an array.  
var numbers = [2, 4, 5, 6, 8];  
  
// Check whether the callback function returns true for all of the  
// array values.  
if (numbers.every(CheckIfEven))  
    document.write("All are even.");  
else  
    document.write("Some are not even.");  
  
// Output:  
// 2 4 5 Some are not even.  
```  
  
## <a name="example"></a>示例  
 下面的示例阐释 `thisArg` 参数的用法，该参数指定 `this` 关键字可引用的对象。  
  
```JavaScript  
// Create a function that returns true if the value is  
// numeric and within range.  
var checkNumericRange = function(value) {  
    if (typeof value !== 'number')  
        return false;  
    else   
        return value >= this.minimum && value <= this.maximum;  
}  
  
// Create an array of numbers.  
var numbers = [10, 15, 19];  
  
// Check whether the callback function returns true for  
// all of the array values.  
// The obj argument enables use of the this value  
// within the callback function.  
  
var obj = { minimum: 10, maximum: 20 }  
  
if (numbers.every(checkNumericRange, obj))  
    document.write ("All are within range.");  
else  
    document.write ("Some are not within range.");  
  
// Output:  
//   All are within range.  
  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [some 方法 (Array)](../../javascript/reference/some-method-array-javascript.md)   
 [filter 方法 (Array)](../../javascript/reference/filter-method-array-javascript.md)   
 [数组对象](../../javascript/reference/array-object-javascript.md)   
 [使用数组](../../javascript/advanced/using-arrays-javascript.md)