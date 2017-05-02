---
title: "filter 方法 (Array) (JavaScript) | Microsoft Docs"
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
  - "数组 [JavaScript], filter 方法"
  - "filter 方法 [JavaScript]"
ms.assetid: 1d260370-9e6e-43fc-870f-2d35850db7ee
caps.latest.revision: 32
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 32
---
# filter 方法 (Array) (JavaScript)
返回数组中的满足回调函数中指定的条件的元素。  
  
## 语法  
  
```  
  
array1.filter(callbackfn[, thisArg])  
```  
  
#### 参数  
  
|参数|定义|  
|--------|--------|  
|`array1`|必需。  一个数组对象。|  
|`callbackfn`|必需。  一个接受最多三个参数的函数。  对于数组中的每个元素，`filter` 方法都会调用 `callbackfn` 函数一次。|  
|`thisArg`|可选。  可在 `callbackfn` 函数中为其引用 `this` 关键字的对象。  如果省略 `thisArg`，则 `undefined` 将用作 `this` 值。|  
  
## 返回值  
 一个包含回调函数为其返回 `true` 的所有值的新数组。  如果回调函数为 `array1` 的所有元素返回 `false`，则新数组的长度为 0。  
  
## 异常  
 如果 `callbackfn` 参数不是函数对象，则将引发 `TypeError` 异常。  
  
## 备注  
 对于数组中的每个元素，`filter` 方法都会调用 `callbackfn` 函数一次（采用升序索引顺序）。  不为数组中缺少的元素调用该回调函数。  
  
 除了数组对象之外，`filter` 方法可由具有 `length` 属性且具有已按数字编制索引的属性名的任何对象使用。  
  
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
 `filter` 方法不直接修改原始数组，但回调函数可能会修改它。  下表描述了在 `filter` 方法启动后修改数组对象所获得的结果。  
  
|`filter` 方法启动后的条件|元素是否传递给回调函数|  
|-----------------------|-----------------|  
|在数组的原始长度之外添加元素。|否。|  
|添加元素以填充数组中缺少的元素。|是，如果该索引尚未传递给回调函数。|  
|元素被更改。|是，如果该元素尚未传递给回调函数。|  
|从数组中删除元素。|否，除非该元素已传递给回调函数。|  
  
## 示例  
 下面的示例演示如何使用 `filter` 方法。  
  
```javascript  
// Define a callback function.  
function CheckIfPrime(value, index, ar) {  
    high = Math.floor(Math.sqrt(value)) + 1;  
  
    for (var div = 2; div <= high; div++) {  
        if (value % div == 0) {  
            return false;  
        }  
    }   
    return true;  
}  
  
// Create the original array.  
var numbers = [31, 33, 35, 37, 39, 41, 43, 45, 47, 49, 51, 53];  
  
// Get the prime numbers that are in the original array.   
var primes = numbers.filter(CheckIfPrime);  
  
document.write(primes);  
// Output: 31,37,41,43,47,53  
```  
  
## 示例  
 在下面的示例中，`callbackfn` 参数包含回调函数的代码。  
  
```javascript  
// Create the original array.  
var arr = [5, "element", 10, "the", true];  
  
// Create an array that contains the string  
// values that are in the original array.  
var result = arr.filter(  
    function (value) {  
        return (typeof value === 'string');  
    }  
);  
  
document.write(result);  
// Output: element, the  
```  
  
## 示例  
 下面的示例显示 `window` DOM 对象中以字母“css”开头的属性名。  
  
```javascript  
var filteredNames = Object.getOwnPropertyNames(window).filter(IsC);  
  
    for (i in filteredNames)  
        document.write(filteredNames[i] + "<br/>");  
  
// Check whether the string starts with "css".  
function IsC(value) {  
    var firstChar = value.substr(0, 3);  
    if (firstChar.toLowerCase() == "css")  
        return true;  
    else  
        return false;  
    }  
  
// Output:  
// CSSRule  
// CSSFontFaceRule  
// CSSImportRule  
// CSSMediaRule  
// CSSNamespaceRule  
// CSSPageRule  
// CSSRuleList  
// CSSStyleDeclaration  
// CSSStyleRule  
// CSSStyleSheet  
  
```  
  
## 示例  
 下面的示例阐释 `thisArg` 参数的用法，该参数指定对其引用 `this` 关键字的对象。  
  
```javascript  
var checkNumericRange = function(value) {  
    if (typeof value !== 'number')  
        return false;  
    else   
        return value >= this.minimum && value <= this.maximum;  
}  
  
var numbers = [6, 12, "15", 16, "the", -12];  
  
// The obj argument enables use of the this value  
// within the callback function.  
var obj = { minimum: 10, maximum: 20 }  
  
var result = numbers.filter(checkNumericRange, obj);  
  
document.write(result);  
// Output: 12,16  
  
```  
  
## 示例  
 `filter` 方法可应用于字符串而不是数组。  下面的示例演示如何执行此操作。  
  
```javascript  
// Define a callback function that returns true  
// if the current array element follows a space  
// or is the first character.  
function CheckValue(value, index, ar) {  
    if (index == 0)  
        return true;  
    else  
        return ar[index - 1] === " ";  
}  
  
// Create a string.  
var sentence = "The quick brown fox jumps over the lazy dog.";   
  
// Create an array that contains all characters that follow a space.  
var subset = [].filter.call(sentence, CheckValue);   
  
// You can use this alternative syntax.  
//var subset = Array.prototype.filter.call(sentence, CheckValue);  
  
document.write(subset);  
// Output: T,q,b,f,j,o,t,l,d  
  
```  
  
## 要求  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## 请参阅  
 [Array 对象](../../javascript/reference/array-object-javascript.md)   
 [使用数组](../../javascript/advanced/using-arrays-javascript.md)   
 [map 方法 \(Array\)](../../javascript/reference/map-method-array-javascript.md)   
 [forEach 方法 \(Array\)](../../javascript/reference/foreach-method-array-javascript.md)