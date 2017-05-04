---
title: "every 方法 (Array) (JavaScript) | Microsoft Docs"
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
  - "数组 [JavaScript], every 方法"
  - "every 方法"
ms.assetid: dc4ee2f8-fb9e-4c9f-af5a-fe836e40ddd1
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# every 方法 (Array) (JavaScript)
确定数组的所有成员是否满足指定的测试。  
  
## 语法  
  
```  
  
array1.every(callbackfn[, thisArg])  
```  
  
#### 参数  
  
|参数|定义|  
|--------|--------|  
|`array1`|必需。  一个数组对象。|  
|`callbackfn`|必需。  一个接受最多三个参数的函数。  `every` 方法会为 `array1` 中的每个元素调用 `callbackfn` 函数，直到 `callbackfn` 返回 `false`，或直到到达数组的结尾。|  
|`thisArg`|可选。  可在 `callbackfn` 函数中为其引用 `this` 关键字的对象。  如果省略 `thisArg`，则 `undefined` 将用作 `this` 值。|  
  
## 返回值  
 如果 `callbackfn` 函数为所有数组元素返回 `true`，则为 `true`；否则为 `false`。  如果数组没有元素，则 `every` 方法将返回 `true`。  
  
## 异常  
 如果 `callbackfn` 参数不是函数对象，则将引发 `TypeError` 异常。  
  
## 备注  
 `every` 方法会按升序顺序对每个数组元素调用一次 `callbackfn` 函数，直到 `callbackfn` 函数返回 `false`。  如果找到导致 `callbackfn` 返回 `false` 的元素，则 `every` 方法会立即返回 `false`。  否则，`every` 方法返回 `true`。  
  
 不为数组中缺少的元素调用该回调函数。  
  
 除了数组对象之外，`every` 方法可由具有 `length` 属性且具有已按数字编制索引的属性名的任何对象使用。  
  
> [!NOTE]
>  可以使用 [some 方法 \(Array\)](../../javascript/reference/some-method-array-javascript.md)检查回调函数是否对数组的任何元素均返回 `true`。  
  
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
  
 下表描述了在 `every` 方法启动后修改数组对象所获得的结果。  
  
|`every` 方法启动后的条件|元素是否传递给回调函数|  
|----------------------|-----------------|  
|在数组的原始长度之外添加元素。|否。|  
|添加元素以填充数组中缺少的元素。|是，如果该索引尚未传递给回调函数。|  
|元素被更改。|是，如果该元素尚未传递给回调函数。|  
|从数组中删除元素。|否，除非该元素已传递给回调函数。|  
  
## 示例  
 下面的示例阐释了 `every` 方法的用法。  
  
```javascript  
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
  
## 示例  
 下面的示例阐释 `thisArg` 参数的用法，该参数指定对其引用 `this` 关键字的对象。  
  
```javascript  
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
  
## 要求  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## 请参阅  
 [some 方法 \(Array\)](../../javascript/reference/some-method-array-javascript.md)   
 [filter 方法 \(Array\)](../../javascript/reference/filter-method-array-javascript.md)   
 [Array 对象](../../javascript/reference/array-object-javascript.md)   
 [使用数组](../../javascript/advanced/using-arrays-javascript.md)