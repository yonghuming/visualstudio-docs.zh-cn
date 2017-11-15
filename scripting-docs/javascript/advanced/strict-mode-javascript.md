---
title: "严格模式 (JavaScript) | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT1038
- VS.WebClient.Help.SCRIPT1050
- VS.WebClient.Help.SCRIPT1042
- VS.WebClient.Help.SCRIPT1041
- VS.WebClient.Help.SCRIPT1046
- VS.WebClient.Help.SCRIPT1045
- VS.WebClient.Help.SCRIPT1037
- VS.WebClient.Help.SCRIPT1039
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- strict mode
- use strict
ms.assetid: 0f27022a-f41c-4504-965c-5a2701f342cd
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 77ee7d54dd265026b2bf4c9af52a71cccf9a7675
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="strict-mode-javascript"></a>严格模式 (JavaScript)
严格模式是一种将更好的错误检查引入代码中的方法。 在使用严格模式时，你无法使用隐式声明的变量、将值赋给只读属性或将属性添加到不可扩展的对象等。 本主题后面的[代码在严格模式下受到的限制](../../javascript/advanced/strict-mode-javascript.md#rest)部分列出了相关限制。 有关严格模式的更多信息，请参阅 [ECMAScript 语言规范版本 5](http://www.ecma-international.org/publications/standards/Ecma-262.htm)。  
  
> [!WARNING]
>  版本 10 之前的 Internet Explorer 版本不支持严格模式。  
  
## <a name="declaring-strict-mode"></a>声明严格模式  
 可以通过在文件、程序或函数的开头添加 `"use strict";` 来声明严格模式。 此类声明称作“指令序言”。 严格模式声明的范围取决于其上下文。 如果在全局上下文（函数的范围之外）中声明严格模式，则程序中的所有代码都处于严格模式。 如果在函数中声明严格模式，则函数中的所有代码都处于严格模式。 例如，在以下示例中，所有代码都处于严格模式，并且函数外部的变量声明会导致出现语法错误“严格模式下未定义变量”。  
  
```JavaScript  
"use strict";  
function testFunction(){  
    var testvar = 4;  
    return testvar;  
}  
  
// This causes a syntax error.  
testvar = 5;  
  
```  
  
 在以下示例中，仅 `testFunction` 中的代码处于严格模式。 函数外部的变量声明不会导致语法错误，但函数内部的声明会导致语法错误。  
  
```JavaScript  
function testFunction(){  
    "use strict";  
    // This causes a syntax error.  
    testvar = 4;  
    return testvar;  
}  
testvar = 5;  
  
```  
  
<a name="rest"></a>   
## <a name="restrictions-on-code-in-strict-mode"></a>代码在严格模式下受到的限制  
 下表列出了严格模式下适用的最重要的限制。  
  
|||||  
|-|-|-|-|  
|**语言元素**|**限制**|**错误**|**示例**|  
|变量|使用变量但不声明。|SCRIPT5042：严格模式下未定义变量|`testvar = 4;`|  
|只读属性|写入到只读属性。|SCRIPT5045：严格模式下不允许分配到只读属性|`var testObj = Object.defineProperties({}, {     prop1: {         value: 10,         writable: false // by default     },     prop2: {         get: function () {         }     } }); testObj.prop1 = 20;  testObj.prop2 = 30;`|  
|不可扩展的属性|将属性添加到 `extensible` 属性设置为 `false` 的对象。|SCRIPT5046：无法为不可扩展的对象创建属性|`var testObj = new Object();  Object.preventExtensions(testObj);  testObj.name = "Bob";`|  
|`delete`|删除变量、函数或自变量。<br /><br /> 删除 `configurable` 特性设置为 `false` 的属性。|SCRIPT1045：严格模式下不允许对 \<表达式> 调用 Delete|`var testvar = 15; function testFunc() {}; delete testvar; delete testFunc;  Object.defineProperty(testObj, "testvar", {     value: 10,     configurable: false     }); delete testObj.testvar;`|  
|重复属性|在一个对象文本中多次定义某个属性。|SCRIPT1046：严格模式下不允许一个属性有多个定义|`var testObj = {     prop1: 10,     prop2: 15,     prop1: 20 };`|  
|重复参数名|在一个函数中多次使用某个参数名。|SCRIPT1038：严格模式下不允许正式参数名称重复|`function testFunc(param1, param1) {     return 1; };`|  
|未来保留关键字|将未来保留关键字用作变量或函数名。|SCRIPT1050：无法使用标识符的未来保留字。 严格模式下将保留标识符名称。|-                      `implements`<br /><br /> -                      `interface`<br /><br /> -                      `package`<br /><br /> -                      `private`<br /><br /> -                      `protected`<br /><br /> -                      `public`<br /><br /> -                      `static`<br /><br /> -                      `yield`|  
|八进制数|对数值文本分配八进制值，或尝试对八进制值使用转义。|SCRIPT1039：严格模式下不允许使用八进制数字参数和转义字符|`var testoctal = 010; var testescape = \010;`|  
|`this`|当 `this` 的值为 `null` 或 `undefined` 时，该值不会转换为全局对象。||`function testFunc() {     return this; } var testvar = testFunc();`<br /><br /> 在非严格模式下，`testvar` 的值为全局对象，但在严格模式下，该值为 `undefined`。|  
|作为标识符的 `eval`|字符串“eval”不能用作标识符（变量或函数名、参数名等）。||`var eval = 10;`|  
|语句或块中声明的函数|无法在语句或块中声明函数。|SCRIPT1047：在严格模式下，函数声明无法嵌套在语句或块中。 它们只能显示在顶级或直接显示在函数体中。|`var arr = [1, 2, 3, 4, 5]; var index = null; for (index in arr) {     function myFunc() {}; }`|  
|`eval` 函数内声明的变量|如果在 `eval` 函数内声明变量，则不能在此函数外部使用该变量。|SCRIPT1041：严格模式下“eval”用法无效|`eval("var testvar = 10"); testvar = 15;`<br /><br /> 虽然允许间接计算，但你仍无法使用在 `eval` 函数外部声明的变量。<br /><br /> `var indirectEval = eval; indirectEval("var testvar = 10;"); document.write(testVar);`<br /><br /> 此代码会导致错误 SCRIPT5009：“testVar”未定义。|  
|作为标识符的 `Arguments`|字符串“arguments”不能用作标识符（变量或函数名、参数名等）。|SCRIPT1042：严格模式下“arguments”用法无效|`var arguments = 10;`|  
|函数内的 `arguments`|无法更改本地 `arguments` 对象的成员的值。||`function testArgs(oneArg) {     arguments[0] = 20; }`<br /><br /> 在非严格模式下，可以通过更改 `oneArg` 的值来更改 `arguments[0]` 参数的值，从而使 `oneArg` 和 `arguments[0]` 的值都为 20。 在严格模式下，更改 `arguments[0]` 的值不会影响 `oneArg` 的值，因为 `arguments` 对象只是一个本地副本。|  
|`arguments.callee`|不允许。||`function (testInt) {     if (testInt-- == 0)         return;     arguments.callee(testInt--); }`|  
|`with`|不允许。|SCRIPT1037：严格模式下不允许使用“with”语句|`with (Math){     x = cos(3);     y = tan(7); }`|