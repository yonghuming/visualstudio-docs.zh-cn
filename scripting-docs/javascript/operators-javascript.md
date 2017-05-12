---
title: "运算符 (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "JavaScript，运算符"
ms.assetid: b8602b69-aba9-46e8-86e1-cb533ad41410
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# 运算符 (JavaScript)
[!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 具有丰富多样的运算符，包括算术运算符、逻辑运算符、按位运算符、赋值运算符以及一些其他运算符。  有关说明和示例，请参见有关特定运算符的主题。  
  
## 算术运算符  
  
|描述|符号|  
|--------|--------|  
|[一元求反](../javascript/reference/subtraction-operator-decrement-javascript.md)|\-|  
|[递增](../javascript/reference/increment-and-decrement-operators-javascript.md)|\+\+|  
|[递减](../javascript/reference/increment-and-decrement-operators-javascript.md)|\-\-|  
|[乘法](../javascript/reference/multiplication-operator-decrement-javascript.md)|\*|  
|[除法](../javascript/reference/division-operator-decrement-javascript.md)|\/|  
|[取模算法](../javascript/reference/modulus-operator-decrementjavascript.md)|%|  
|[添加](../javascript/reference/addition-operator-decrement-javascript.md)|\+|  
|[减法](../javascript/reference/subtraction-operator-decrement-javascript.md)|\-|  
  
## 逻辑运算符  
  
|描述|符号|  
|--------|--------|  
|[逻辑“非”](../javascript/reference/logical-not-operator-decrement-exclpt-javascript.md)|\!|  
|[小于](../javascript/reference/comparison-operators-javascript.md)|\<|  
|[大于](../javascript/reference/comparison-operators-javascript.md)|\>|  
|[小于或等于](../javascript/reference/comparison-operators-javascript.md)|\<\=|  
|[大于或等于](../javascript/reference/comparison-operators-javascript.md)|\>\=|  
|[相等](../javascript/reference/comparison-operators-javascript.md)|\=\=|  
|[不相等](../javascript/reference/comparison-operators-javascript.md)|\!\=|  
|[逻辑“与”](../javascript/reference/logical-and-operator-decrement-javascript.md)|&&|  
|[逻辑“或”](../javascript/reference/logical-or-operator-decrement-javascript.md)|&#124;&#124;|  
|[有条件的（三元）](../javascript/reference/conditional-ternary-operator-decrement-javascript.md)|?:|  
|[逗号](../javascript/reference/comma-operator-decrement-javascript.md)|,|  
|[严格相等](../javascript/reference/comparison-operators-javascript.md)|\=\=\=|  
|[严格不等](../javascript/reference/comparison-operators-javascript.md)|\!\=\=|  
  
## 位运算符  
  
|描述|符号|  
|--------|--------|  
|[按位“非”](../javascript/reference/bitwise-not-operator-decrement-tilde-javascript.md)|~|  
|[按位左移](../javascript/reference/bitwise-left-shift-operator-decrement-javascript.md)|\<\<|  
|[按位右移](../javascript/reference/bitwise-right-shift-operator-decrement-javascript.md)|\>\>|  
|[无符号右移](../javascript/reference/unsigned-right-shift-operator-decrement-javascript.md)|\>\>\>|  
|[按位“与”](../javascript/reference/bitwise-and-operator-decrement-javascript.md)|&|  
|[按位“异或”](../javascript/reference/bitwise-xor-operator-decrement-hat-javascript.md)|^|  
|[按位“或”](../javascript/reference/bitwise-or-operator-decrement-javascript.md)|&#124;|  
  
## 赋值运算符  
  
|描述|符号|  
|--------|--------|  
|[赋值](../javascript/reference/assignment-operator-decrement-equal-javascript.md)|\=|  
|[复合赋值](../javascript/reference/compound-assignment-operators-javascript.md)|*OP*\=（如 \+\= 和 &\=）|  
  
## 其他运算符  
  
|描述|符号|  
|--------|--------|  
|[删除](../javascript/reference/delete-operator-decrementjavascript.md)|删除|  
|[typeof](../javascript/reference/typeof-operator-decrementjavascript.md)|typeof|  
|[void](../javascript/reference/void-operator-decrementjavascript.md)|void|  
|[instanceof](../javascript/reference/instanceof-operator-decrementjavascript.md)|instanceof|  
|[new](../javascript/reference/new-operator-decrementjavascript.md)|new|  
|[in](../javascript/reference/in-operator-decrementjavascript.md)|in|  
  
## 相等和全等  
 \=\=（相等）和 \=\=\=（全等）之间的差异是相等运算符将在检查是否相等之前强制转换其他类型的值。  例如，将字符串“1”与数字 1 进行比较，比较结果将为 true。  另一方面，全等运算符不会将值强制转换为其他类型，因此字符串“1”的比较结果将不为数字 1。  
  
 基元字符串、数字和布尔值通过值进行比较。  如果它们的值相同，则它们相等。  对象（包括 `Array`、`Function`、`String`、**Number**、`Boolean`、**Error**、`Date` 和 `RegExp` 对象）是根据引用来进行比较的。  即使这些类型的两个变量具有相同的值，也只有当引用完全相同的对象时，它们才相等。  
  
 例如：  
  
```javascript  
// Two strings with the same value.  
var string1 = "Hello";  
var string2 = "Hello";  
  
// Two String objects with the same value.  
var StringObject1 = new String(string1);  
var StringObject2 = new String(string2);  
  
if (string1 == string2)  
    document.write("string1 is equal to string2 <br/>");  
  
if (StringObject1 != StringObject2)  
    document.write("StringObject1 is not equal to StringObject2 <br/>");  
  
// To compare the values of String objects, use the toString() or valueOf() methods.  
if (StringObject1.valueOf() == StringObject2.valueOf())  
    document.write("The value of StringObject1 is equal to the value of StringObject2");  
  
//Output:  
// string1 is equal to string2   
// StringObject1 is not equal to StringObject2   
// The value of StringObject1 is equal to the value of StringObject2  
  
```