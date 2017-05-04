---
title: "reduce 方法 (Array) (JavaScript) | Microsoft Docs"
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
  - "数组 [JavaScript], reduce 方法"
  - "回调函数, reduce 方法 [JavaScript]"
  - "reduce 方法 [JavaScript]"
ms.assetid: 48d069e0-e083-494f-86d5-d459d2377dc5
caps.latest.revision: 21
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 21
---
# reduce 方法 (Array) (JavaScript)
对数组中的所有元素调用指定的回调函数。  该回调函数的返回值为累积结果，并且此返回值在下一次调用该回调函数时作为参数提供。  
  
## 语法  
  
```  
  
array1.reduce(callbackfn[, initialValue])  
```  
  
#### 参数  
  
|参数|定义|  
|--------|--------|  
|`array1`|必需。  一个数组对象。|  
|`callbackfn`|必需。  一个接受最多四个参数的函数。  对于数组中的每个元素，`reduce` 方法都会调用 `callbackfn` 函数一次。|  
|`initialValue`|可选。  如果指定 `initialValue`，则它将用作初始值来启动累积。  第一次调用 `callbackfn` 函数会将此值作为参数而非数组值提供。|  
  
## 返回值  
 通过最后一次调用回调函数获得的累积结果。  
  
## 异常  
 当满足下列任一条件时，将引发 `TypeError` 异常：  
  
-   `callbackfn` 参数不是函数对象。  
  
-   数组不包含元素，且未提供 `initialValue`。  
  
## 备注  
 如果提供了 `initialValue`，则 `reduce` 方法会对数组中的每个元素调用一次 `callbackfn` 函数（按升序索引顺序）。  如果未提供 `initialValue`，则 `reduce` 方法会对从第二个元素开始的每个元素调用 `callbackfn` 函数。  
  
 回调函数的返回值在下一次调用回调函数时作为 `previousValue` 参数提供。  最后一次调用回调函数获得的返回值为 `reduce` 方法的返回值。  
  
 不为数组中缺少的元素调用该回调函数。  
  
> [!NOTE]
>  [reduceRight 方法 \(Array\)](../../javascript/reference/reduceright-method-array-javascript.md)按降序索引顺序处理元素。  
  
## 回调函数语法  
 回调函数的语法如下所示：  
  
 `function callbackfn(previousValue, currentValue, currentIndex, array1)`  
  
 可使用最多四个参数来声明回调函数。  
  
 下表列出了回调函数参数。  
  
|回调参数|定义|  
|----------|--------|  
|`previousValue`|通过上一次调用回调函数获得的值。  如果向 `reduce` 方法提供 `initialValue`，则在首次调用函数时，`previousValue` 为 `initialValue`。|  
|`currentValue`|当前数组元素的值。|  
|`currentIndex`|当前数组元素的数字索引。|  
|`array1`|包含该元素的数组对象。|  
  
## 第一次调用回调函数  
 在第一次调用回调函数时，作为参数提供的值取决于 `reduce` 方法是否具有 `initialValue` 参数。  
  
 如果向 reduce 方法提供 `initialValue`：  
  
-   `previousValue` 参数为 `initialValue`。  
  
-   `currentValue` 参数是数组中的第一个元素的值。  
  
 如果未提供 `initialValue`：  
  
-   `previousValue` 参数是数组中的第一个元素的值。  
  
-   `currentValue` 参数是数组中的第二个元素的值。  
  
## 修改数组对象  
 数组对象可由回调函数修改。  
  
 下表描述了在 `reduce` 方法启动后修改数组对象所获得的结果。  
  
|`reduce` 方法启动后的条件|元素是否传递给回调函数|  
|-----------------------|-----------------|  
|在数组的原始长度之外添加元素。|否。|  
|添加元素以填充数组中缺少的元素。|是，如果该索引尚未传递给回调函数。|  
|元素被更改。|是，如果该元素尚未传递给回调函数。|  
|从数组中删除元素。|否，除非该元素已传递给回调函数。|  
  
## 示例  
 下面的示例将数组值连接成字符串，各个值用“::”分隔开。  由于未向 `reduce` 方法提供初始值，第一次调用回调函数时会将“abc”作为 `previousValue` 参数并将“def”作为 `currentValue` 参数。  
  
```javascript  
// Define the callback function.  
function appendCurrent (previousValue, currentValue) {  
    return previousValue + "::" + currentValue;  
    }  
  
// Create an array.  
var elements = ["abc", "def", 123, 456];  
  
// Call the reduce method, which calls the callback function  
// for each array element.  
var result = elements.reduce(appendCurrent);  
  
document.write(result);  
  
// Output:  
//  abc::def::123::456  
  
```  
  
## 示例  
 下面的示例向数组添加舍入后的值。  使用初始值 0 调用 `reduce` 方法。  
  
```javascript  
// Define the callback function.  
function addRounded (previousValue, currentValue) {  
    return previousValue + Math.round(currentValue);  
    }  
  
// Create an array.  
var numbers = [10.9, 15.4, 0.5];  
  
// Call the reduce method, starting with an initial value of 0.  
var result = numbers.reduce(addRounded, 0);  
  
document.write (result);  
// Output: 27  
```  
  
## 示例  
 下面的示例向数组中添加值。  `currentIndex` 和 `array1` 参数用于回调函数。  
  
```javascript  
function addDigitValue(previousValue, currentDigit, currentIndex, array) {  
    var exponent = (array.length - 1) - currentIndex;  
    var digitValue = currentDigit * Math.pow(10, exponent);  
    return previousValue + digitValue;  
    }  
  
var digits = [4, 1, 2, 5];  
  
// Determine an integer that is computed from values in the array.  
var result = digits.reduce(addDigitValue, 0);  
  
document.write (result);  
// Output: 4125  
```  
  
## 示例  
 下面的示例获取一个数组，该数组仅包含另一个数组中的介于 1 和 10 之间值。  提供给 `reduce` 方法的初始值是一个空数组。  
  
```javascript  
function Process(previousArray, currentValue) {  
    // If currentValue is between 1 and 10,   
    // append currentValue to the array.  
    var nextArray;  
    if (currentValue >= 1 && currentValue <= 10)  
        nextArray = previousArray.concat(currentValue);  
    else  
        nextArray = previousArray;  
  
    // If this is not the last call by the reduce method,  
    // the returned array is previousArray on the next call.  
    // If this is the last call by the reduce method, the  
    // returned array is the return value of the reduce method.  
    return nextArray;  
}  
  
// Create an array.  
var numbers = [20, 1, -5, 6, 50, 3];  
  
// Call the reduce method, starting with an initial empty array.  
var emptyArray = new Array();  
var resultArray = numbers.reduce(Process, emptyArray);  
  
document.write("result array=" + resultArray);  
  
// Output:  
// result array=1,6,3  
```  
  
## 要求  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## 请参阅  
 [reduceRight 方法 \(Array\)](../../javascript/reference/reduceright-method-array-javascript.md)