---
title: "some 方法 (Array) (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "数组 [JavaScript], some 方法"
  - "some 方法 [JavaScript]"
ms.assetid: 7b6822f9-c406-4f4e-bfec-a93459745992
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# some 方法 (Array) (JavaScript)
确定指定的回调函数是否为数组中的任何元素均返回 `true`。  
  
## 语法  
  
```  
  
array1.some(callbackfn[, thisArg])  
```  
  
#### 参数  
  
|参数|定义|  
|--------|--------|  
|`array1`|必需。  一个数组对象。|  
|`callbackfn`|必需。  一个接受最多三个参数的函数。  `some` 方法会为 `array1` 中的每个元素调用 `callbackfn` 函数，直到 `callbackfn` 返回 `true`，或直到到达数组的结尾。|  
|`thisArg`|可选。  可在 `callbackfn` 函数中为其引用 `this` 关键字的对象。  如果省略 `thisArg`，则 `undefined` 将用作 `this` 值。|  
  
## 返回值  
 如果 `callbackfn` 函数为任何数组元素均返回 `true`，则为 `true`；否则为 `false`。  
  
## 异常  
 如果 `callbackfn` 参数不是函数对象，则将引发 `TypeError` 异常。  
  
## 备注  
 `some` 方法会按升序索引顺序对每个数组元素调用 `callbackfn` 函数，直到 `callbackfn` 函数返回 `true`。  如果找到导致 `callbackfn` 返回 `true` 的元素，则 `some` 方法会立即返回 `true`。  如果回调不对任何元素返回 `true`，则 `some` 方法会返回 `false`。  
  
 不为数组中缺少的元素调用该回调函数。  
  
 除了数组对象之外，`some` 方法可由具有 `length` 属性且具有已按数字编制索引的属性名的任何对象使用。  
  
> [!NOTE]
>  可以使用 [every 方法 \(Array\)](../../javascript/reference/every-method-array-javascript.md)检查回调函数是否对数组的所有元素都返回 `true`。  
  
## 回调函数语法  
 回调函数的语法如下所示：  
  
 `function callbackfn(value, index, array1)`  
  
 可使用最多三个参数来声明回调函数。  
  
 下表列出了回调函数参数。  
  
|回调参数|定义|  
|----------|--------|  
|`value`|数组元素的值。|  
|`index`|数组元素的数字索引。|  
|`array1`|包含该元素的数组对象。|  
  
## 修改数组对象  
 数组对象可由回调函数修改。  
  
 下表描述了在 `some` 方法启动后修改数组对象所获得的结果。  
  
|`some` 方法启动后的条件|元素是否传递给回调函数|  
|---------------------|-----------------|  
|在数组的原始长度之外添加元素。|否。|  
|添加元素以填充数组中缺少的元素。|是，如果该索引尚未传递给回调函数。|  
|元素被更改。|是，如果该元素尚未传递给回调函数。|  
|从数组中删除元素。|否，除非该元素已传递给回调函数。|  
  
## 示例  
 下面的示例使用 `some` 方法查明数组中的任何元素是否相等。  
  
```javascript  
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
  
## 示例  
 下面的示例演示如何使用 `thisArg` 参数，该参数指定 `this` 关键字可引用的对象。  它检查数组中是否有数字位于传递的对象所提供的范围之外。  
  
```javascript  
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
  
## 要求  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## 请参阅  
 [every 方法 \(Array\)](../../javascript/reference/every-method-array-javascript.md)   
 [filter 方法 \(Array\)](../../javascript/reference/filter-method-array-javascript.md)   
 [map 方法 \(Array\)](../../javascript/reference/map-method-array-javascript.md)