---
title: "reduceRight 方法 (Array) (JavaScript) | Microsoft Docs"
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
  - "数组 [JavaScript], reduceRight 方法"
  - "reduceRight 方法 [JavaScript]"
ms.assetid: 85963761-da11-407c-8bce-278c930e61bd
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# reduceRight 方法 (Array) (JavaScript)
按降序顺序对数组中的所有元素调用指定的回调函数。  该回调函数的返回值为累积结果，并且此返回值在下一次调用该回调函数时作为参数提供。  
  
## 语法  
  
```  
  
array1.reduceRight(callbackfn[, initialValue])  
```  
  
#### 参数  
  
|参数|定义|  
|--------|--------|  
|`array1`|必需。  一个数组对象。|  
|`callbackfn`|必需。  一个接受最多四个参数的函数。  对于数组中的每个元素，`reduceRight` 方法都会调用 `callbackfn` 函数一次。|  
|`initialValue`|可选。  如果指定 `initialValue`，则它将用作初始值来启动累积。  第一次调用 `callbackfn` 函数会将此值作为参数而非数组值提供。|  
  
## 返回值  
 包含通过最后一次调用回调函数获得的累积结果的对象。  
  
## 异常  
 当满足下列任一条件时，将引发 `TypeError` 异常：  
  
-   `callbackfn` 参数不是函数对象。  
  
-   数组不包含元素，且未提供 `initialValue`。  
  
## 备注  
 如果提供了 `initialValue`，则 `reduceRight` 方法会按降序索引顺序对数组中的每个元素调用一次 `callbackfn` 函数。  如果未提供 `initialValue`，则 `reduceRight` 方法会按降序索引顺序对每个元素（从倒数第二个元素开始）调用 `callbackfn` 函数。  
  
 回调函数的返回值在下一次调用回调函数时作为 `previousValue` 参数提供。  最后一次调用回调函数获得的返回值为 `reduceRight` 方法的返回值。  
  
 不为数组中缺少的元素调用该回调函数。  
  
 若要按升序索引顺序累积结果，请使用 [reduce 方法 \(Array\)](../../javascript/reference/reduce-method-array-javascript.md)。  
  
## 回调函数语法  
 回调函数的语法如下所示：  
  
 `function callbackfn(previousValue, currentValue, currentIndex, array1)`  
  
 可使用最多四个参数来声明回调函数。  
  
 下表列出了回调函数参数。  
  
|回调参数|定义|  
|----------|--------|  
|`previousValue`|通过上一次调用回调函数获得的值。  如果向 `reduceRight` 方法提供 `initialValue`，则在首次调用函数时，`previousValue` 为 `initialValue`。|  
|`currentValue`|当前数组元素的值。|  
|`currentIndex`|当前数组元素的数字索引。|  
|`array1`|包含该元素的数组对象。|  
  
## 第一次调用回调函数  
 在第一次调用回调函数时，作为参数提供的值取决于 `reduceRight` 方法是否具有 `initialValue` 参数。  
  
 如果向 `reduceRight` 方法提供 `initialValue`：  
  
-   `previousValue` 参数为 `initialValue`。  
  
-   `currentValue` 参数是数组中的最后一个元素的值。  
  
 如果未提供 `initialValue`：  
  
-   `previousValue` 参数是数组中的最后一个元素的值。  
  
-   `currentValue` 参数是数组中的倒数第二个元素的值。  
  
## 修改数组对象  
 数组对象可由回调函数修改。  
  
 下表描述了在 `reduceRight` 方法启动后修改数组对象所获得的结果。  
  
|`reduceRight` 方法启动后的条件|元素是否传递给回调函数|  
|----------------------------|-----------------|  
|在数组的原始长度之外添加元素。|否。|  
|添加元素以填充数组中缺少的元素。|是，如果该索引尚未传递给回调函数。|  
|元素被更改。|是，如果该元素尚未传递给回调函数。|  
|从数组中删除元素。|否，除非该元素已传递给回调函数。|  
  
## 示例  
 下面的示例将数组值连接成字符串，各个值用“::”分隔开。  由于未向 `reduceRight` 方法提供初始值，第一次调用回调函数时会将 456 作为 `previousValue` 参数并将 123 作为 `currentValue` 参数。  
  
```javascript  
// Define the callback function.  
function appendCurrent (previousValue, currentValue) {  
    return previousValue + "::" + currentValue;  
    }  
  
// Create an array.  
var elements = ["abc", "def", 123, 456];  
  
// Call the reduceRight method, which calls the callback function  
// for each array element, in descending index order.  
var result = elements.reduceRight(appendCurrent);  
  
document.write(result);  
  
// Output:  
//  456::123::def::abc  
```  
  
## 示例  
 下面的示例查找数组元素的平方和。  使用初始值 0 调用 `reduceRight` 方法。  
  
```javascript  
// Define the callback function.  
function Process(previousValue, currentValue, index, array) {  
    // Add the previous value to the current value squared.  
    var nextValue = previousValue + (currentValue * currentValue);  
  
    // If this is not the last call by the reduceRight method,  
    // the return value is previousValue on the next call.  
    // If this is the last call by the reduceRight method, the  
    // return value is the return value of the reduceRight method.  
    return nextValue;  
}  
  
// Create an array.  
var numbers = [3, 4, 5];  
  
// Call the reduceRight method with an initial value of 0.  
var sumOfSquares = numbers.reduceRight(Process, 0);  
  
document.write("sum of squares=" + sumOfSquares);  
  
// Output:  
//  sum of squares=50  
```  
  
## 示例  
 下面的示例获取数组中值为 1 到 10 之间的元素。  提供给 `reduceRight` 方法的初始值是一个空数组。  
  
```javascript  
function Process2(previousArray, currentValue) {  
    // If currentValue is between 1 and 10,   
    // append currentValue to the array.  
    var nextArray;  
    if (currentValue >= 1 && currentValue <= 10)  
        nextArray = previousArray.concat(currentValue);  
    else  
        nextArray = previousArray;  
  
    // If this is not the last call by the reduceRight method,  
    // the returned array is previousArray on the next call.  
    // If this is the last call by the reduceRight method, the  
    // returned array is the return value of the reduceRight method.  
    return nextArray;  
}  
  
// Create an array.  
var numbers = [20, 1, -5, 6, 50, 3];  
  
// Call the reduceRight method, starting with an empty array.  
var emptyArray = new Array();  
var resultArray = numbers.reduceRight(Process2, emptyArray);  
  
document.write("result array=" + resultArray);  
  
// Output:  
//  result array=3,6,1  
```  
  
## 示例  
 `reduceRight` 方法可应用于字符串。  下面的示例演示如何使用此方法反转字符串中的字符。  
  
```javascript  
// Define the callback function.  
function AppendToArray(previousValue, currentValue) {  
    return previousValue + currentValue;  
}  
  
var word = "retupmoc";  
  
// Create a string that reverses the characters of another string.  
// The commented-out statement shows an alternative syntax.  
var result = [].reduceRight.call(word, AppendToArray, "the ");  
// var result = Array.prototype.reduceRight.call(word, AppendToArray, "the ");  
  
document.write(result);  
  
// Output:  
// the computer  
```  
  
## 要求  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## 请参阅  
 [reduce 方法 \(Array\)](../../javascript/reference/reduce-method-array-javascript.md)