---
title: "reduceRight 方法 (Array) (JavaScript) |Microsoft 文档"
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
- arrays [JavaScript], reduceRight method
- reduceRight method [JavaScript]
ms.assetid: 85963761-da11-407c-8bce-278c930e61bd
caps.latest.revision: "19"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0d7fd2794157eadacefa7404f9333c51aed9425c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="reduceright-method-array-javascript"></a>reduceRight 方法 (Array) (JavaScript)
为数组、 以降序顺序中的所有元素调用指定的回调函数。 回调函数的返回值是累积的结果，并且作为对回调函数的下一个调用中的自变量提供。  
  
## <a name="syntax"></a>语法  
  
```  
  
array1.reduceRight(callbackfn[, initialValue])  
```  
  
#### <a name="parameters"></a>参数  
  
|参数|定义|  
|---------------|----------------|  
|`array1`|必需。 一个数组对象。|  
|`callbackfn`|必需。 接受最多四个自变量的函数。 对于数组中的每个元素，`reduceRight` 方法都会调用 `callbackfn` 函数一次。|  
|`initialValue`|可选。 如果`initialValue`指定，它用于作为初始值开始累积。 首次调用`callbackfn`函数提供此值作为参数而不是数组值。|  
  
## <a name="return-value"></a>返回值  
 包含从对回调函数的最后一个调用累积的结果的对象。  
  
## <a name="exceptions"></a>异常  
 A`TypeError`时将引发异常的以下条件的任何一种情况：  
  
-   `callbackfn`参数不是函数对象。  
  
-   数组不包含任何元素和`initialValue`未提供。  
  
## <a name="remarks"></a>备注  
 如果`initialValue`提供，`reduceRight`方法调用`callbackfn`函数中降序索引的数组中每个元素的一次。 如果没有`initialValue`提供，`reduceRight`方法调用`callbackfn`函数对每个元素，从上一次第二个元素，按降序索引开始。  
  
 回调函数的返回值用作`previousValue`上对回调函数的下一个调用的自变量。 对回调函数的最后一个调用的返回值是返回值的`reduceRight`方法。  
  
 将不会为数组中缺少的元素调用回调函数。  
  
 若要会累积升序索引顺序中的某个结果，使用[reduce 方法 (Array)](../../javascript/reference/reduce-method-array-javascript.md)。  
  
## <a name="callback-function-syntax"></a>回调函数语法  
 回调函数的语法如下所示：  
  
 `function callbackfn(previousValue, currentValue, currentIndex, array1)`  
  
 可以使用最多四个参数来声明回调函数。  
  
 下表列出了回调函数参数。  
  
|回调参数|定义|  
|-----------------------|----------------|  
|`previousValue`|来自调用的回调函数的值。 如果`initialValue`提供给`reduceRight`方法，`previousValue`是`initialValue`在首次调用该函数。|  
|`currentValue`|当前数组元素的值。|  
|`currentIndex`|当前数组元素的数字索引。|  
|`array1`|包含该元素的数组对象。|  
  
## <a name="first-call-to-the-callback-function"></a>首次调用回调函数  
 第一次调用回调函数时，作为自变量提供的值取决于是否`reduceRight`方法具有`initialValue`自变量。  
  
 如果`initialValue`提供给`reduceRight`方法：  
  
-   `previousValue` 参数为 `initialValue`。  
  
-   `currentValue`参数是数组中出现的最后一个元素的值。  
  
 如果`initialValue`未提供：  
  
-   `previousValue`参数是数组中出现的最后一个元素的值。  
  
-   `currentValue`参数是数组中出现的倒数第二个元素的值。  
  
## <a name="modifying-the-array-object"></a>修改数组对象  
 数组对象可由回调函数修改。  
  
 下表描述了在 `reduceRight` 方法启动后修改数组对象所获得的结果。  
  
|`reduceRight` 方法启动后的条件|元素是否传递给回调函数？|  
|-----------------------------------------------------|------------------------------------------|  
|在数组的原始长度之外添加元素。|不可以。|  
|添加元素以填充数组中缺少的元素。|是，如果该索引尚未传递给回调函数。|  
|元素已更改。|是，如果该元素尚未传递给回调函数。|  
|从数组中删除元素。|否，除非该元素已传递给回调函数。|  
  
## <a name="example"></a>示例  
 下面的示例将数组值串联成一个字符串，分隔各个值与"::"。 因为没有初始值提供给`reduceRight`方法，对回调函数的第一个调用已作为 456`previousValue`自变量并将它作为 123`currentValue`自变量。  
  
```JavaScript  
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
  
## <a name="example"></a>示例  
 下面的示例查找数组元素的平方和。 `reduceRight`方法调用使用初始值为 0。  
  
```JavaScript  
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
  
## <a name="example"></a>示例  
 下面的示例获取一个数组，其值是 1 到 10 之间的那些元素。 提供给的初始值`reduceRight`方法为空数组。  
  
```JavaScript  
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
  
## <a name="example"></a>示例  
 `reduceRight` 方法可应用于一个字符串。 下面的示例演示如何使用此方法反向字符串中的字符。  
  
```JavaScript  
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
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [reduce 方法 (Array)](../../javascript/reference/reduce-method-array-javascript.md)