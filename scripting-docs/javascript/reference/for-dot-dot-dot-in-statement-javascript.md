---
title: "为..语句 (JavaScript) |Microsoft 文档"
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
- iteration statements, for...in statement
- loop structures, for...in statements
ms.assetid: 1b51a0ce-89f7-4a69-88ed-017b47dc398f
caps.latest.revision: "20"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a9c3ce78def6ab91256ff724a4acc87b7cf19ba2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="forin-statement-javascript"></a>for...in 语句 (JavaScript)
执行的对象，每个属性或数组的每个元素的一个或多个语句。  
  
## <a name="syntax"></a>语法  
  
```  
for (variable in [object | array]) {  
    statements   
}  
```  
  
## <a name="parameters"></a>参数  
 `variable`  
 必需。 可以是任何属性名称的变量`object`或的任何元素索引`array`。  
  
 `object`, `array`  
 可选。 一个对象或对其进行循环的数组。  
  
 `statements`  
 可选。 要执行的每个属性的一个或多个语句`object`或的每个元素`array`。 可以是复合语句。  
  
## <a name="remarks"></a>备注  
 在循环中的值每次迭代开头`variable`是下一步的属性名称的`object`或下一个元素索引的`array`。 然后，可以使用`variable`任何循环引用的属性中的语句中`object`或者的元素`array`。  
  
 对象的属性不会分配确定的方式。 只能由属性的名称，不能通过其索引，指定的特定属性。  
  
 循环访问数组元素的顺序，即 0、 1、 2 执行。  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用`for...in`用作关联阵列的形式的对象的语句。  
  
```JavaScript  
// Initialize object.  
a = {"a" : "Athens" , "b" : "Belgrade", "c" : "Cairo"}  
  
// Iterate over the properties.  
var s = ""  
for (var key in a) {  
    s += key + ": " + a[key];  
    s += "<br />";  
    }  
document.write (s);  
  
// Output:  
// a: Athens  
// b: Belgrade  
// c: Cairo  
```  
  
## <a name="example"></a>示例  
 此示例演示如何使用`for ... in`语句用于循环访问`Array`具有 expando 属性的对象。  
  
```JavaScript  
// Initialize the array.  
var arr = new Array("zero","one","two");  
  
// Add a few expando properties to the array.  
arr["orange"] = "fruit";  
arr["carrot"] = "vegetable";  
  
// Iterate over the properties and elements.  
var s = "";  
for (var key in arr) {  
    s += key + ": " + arr[key];  
    s += "<br />";  
}  
  
document.write (s);  
  
// Output:  
//   0: zero  
//   1: one  
//   2: two  
//   orange: fruit  
//   carrot: vegetable  
```  
  
> [!NOTE]
>  使用`Enumerator`对象循环访问集合的成员。  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [for 语句](../../javascript/reference/for-statement-javascript.md)   
 [while 语句](../../javascript/reference/while-statement-javascript.md)