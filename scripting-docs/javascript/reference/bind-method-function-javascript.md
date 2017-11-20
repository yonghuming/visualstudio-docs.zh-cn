---
title: "bind 方法 (Function) (JavaScript) |Microsoft 文档"
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
- parameters [JavaScript], bind method
- arguments [JavaScript], bind method
- bind method [JavaScript]
- this keyword [JavaScript], bind method
ms.assetid: 28946f47-b758-48cf-b508-610a0f2f6e19
caps.latest.revision: "21"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dd7fc752df9bd41f8625ac2cb484486dfd19558d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="bind-method-function-javascript"></a>bind 方法 (Function) (JavaScript)
对于给定函数，创建具有与原始函数相同的主体的绑定函数。 在绑定函数中，`this` 对象将解析为传入的对象。 绑定函数具有指定的初始参数。  
  
## <a name="syntax"></a>语法  
  
```  
  
function.bind(thisArg[,arg1[,arg2[,argN]]])  
```  
  
#### <a name="parameters"></a>参数  
 `function`  
 必需。 一个函数对象。  
  
 `thisArg`  
 必需。 `this` 关键字可在新函数中引用的对象。  
  
 `arg1`[,`arg2`[,`argN`]]]  
 可选。 要传递到新函数的参数的列表。  
  
## <a name="return-value"></a>返回值  
 与 `function` 函数相同的新函数，`thisArg` 对象和初始参数除外。  
  
## <a name="exceptions"></a>异常  
 如果指定的 `function` 不是函数，则将引发 `TypeError` 异常。  
  
## <a name="example"></a>示例  
 下面的代码演示如何使用 `bind` 方法。  
  
```JavaScript  
// Define the original function.  
var checkNumericRange = function (value) {  
    if (typeof value !== 'number')  
        return false;  
    else  
        return value >= this.minimum && value <= this.maximum;  
}  
  
// The range object will become the this value in the callback function.  
var range = { minimum: 10, maximum: 20 };  
  
// Bind the checkNumericRange function.  
var boundCheckNumericRange = checkNumericRange.bind(range);  
  
// Use the new function to check whether 12 is in the numeric range.  
var result = boundCheckNumericRange (12);  
document.write(result);  
  
// Output: true  
```  
  
## <a name="example"></a>示例  
 在下面的示例中，`thisArg` 对象与包含原始方法的对象不同。  
  
```JavaScript  
// Create an object that contains the original function.  
var originalObject = {  
    minimum: 50,  
    maximum: 100,  
    checkNumericRange: function (value) {  
        if (typeof value !== 'number')  
            return false;  
        else  
            return value >= this.minimum && value <= this.maximum;  
    }  
}  
  
// Check whether 10 is in the numeric range.  
var result = originalObject.checkNumericRange(10);  
document.write(result + " ");  
// Output: false  
  
// The range object supplies the range for the bound function.  
var range = { minimum: 10, maximum: 20 };  
  
// Create a new version of the checkNumericRange function that uses range.  
var boundObjectWithRange = originalObject.checkNumericRange.bind(range);  
  
// Check whether 10 is in the numeric range.  
var result = boundObjectWithRange(10);  
document.write(result);  
// Output: true  
```  
  
## <a name="example"></a>示例  
 以下代码演示如何使用 `arg1[,arg2[,argN]]]` 参数。 绑定函数将 `bind` 方法中指定的参数用作第一个参数和第二个参数。 在调用绑定函数时指定的任何参数将用作第三个、第四个参数（依此类推）。  
  
```JavaScript  
// Define the original function with four parameters.  
var displayArgs = function (val1, val2, val3, val4) {  
    document.write(val1 + " " + val2 + " " + val3 + " " + val4);  
}  
  
var emptyObject = {};  
  
// Create a new function that uses the 12 and "a" parameters  
// as the first and second parameters.  
var displayArgs2 = displayArgs.bind(emptyObject, 12, "a");  
  
// Call the new function. The "b" and "c" parameters are used  
// as the third and fourth parameters.  
displayArgs2("b", "c");  
// Output: 12 a b c   
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [函数对象](../../javascript/reference/function-object-javascript.md)   
 [filter 方法 (Array)](../../javascript/reference/filter-method-array-javascript.md)   
 [使用 bind 方法](../../javascript/advanced/using-the-bind-method-javascript.md)   
 [Hilo JavaScript 示例应用程序 （Windows 应用商店）](http://hilojs.codeplex.com/SourceControl/latest)