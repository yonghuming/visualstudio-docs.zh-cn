---
title: "JavaScript 版本信息 |Microsoft 文档"
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
helpviewer_keywords: JavaScript, version information
ms.assetid: 440f4924-f7a9-48e0-873e-bd599a93b437
caps.latest.revision: "93"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b0503abb3d62e9fd61149b884a7b58a685fbc62c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="javascript-version-information"></a>JavaScript 版本信息
不同版本的 JavaScript 支持不同的 JavaScript 元素集。 [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] 应用支持 Internet Explorer 中略微不同的功能集。  
  
> [!IMPORTANT]
>  [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] 应用是一种在 [!INCLUDE[win8](../../javascript/includes/win8-md.md)] 设备上运行的新型应用程序。 若要查找有关 [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] 应用的详细信息，请参见 [What's a Windows Store app?](http://msdn.microsoft.com/en-us/231c1fba-9f87-468e-94aa-45dd57edcc70)  
  
 标准模式（当有 `<!doctype>` 指令时在 Internet Explorer 直至 Internet Explorer 11 的所有版本中使用的模式）支持的元素集与 Quirks 模式（当没有 `<!doctype>` 指令时使用的模式）支持的元素集有所不同。 有关版本控制的详细信息，请参见 [定义文档兼容性](http://go.microsoft.com/fwlink/?LinkId=208537)。  
  
 下表显示支持特定语言元素的 Internet Explorer 文档模式（以及表示 [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] 和 [!INCLUDE[winphone_appname](../../javascript/reference/includes/winphone-appname-md.md)]的应用商店应用）。 支持给定元素的文档模式在显示时带有字母 **Y**，不支持给定元素的文档模式在显示时带有字母 **N**。  
  
> [!IMPORTANT]
>  [!INCLUDE[jsv12text](../../javascript/includes/jsv12text-md.md)]（Windows 10 中的边缘浏览器）不包括对旧的文档模式的支持。 对 [!INCLUDE[winphone_appname](../../javascript/reference/includes/winphone-appname-md.md)] 应用的支持始于 Windows Phone 8.1。 实验功能 (关于： 标志) 由"Exp"指示。  
  
 该表包含摘要信息。 有关更具体的信息，请参阅语言元素的文档。  
  
|语言元素|Quirks、Internet Explorer 6 标准、Internet Explorer 7 标准|Internet Explorer 8 标准|Internet Explorer 9 标准|Internet Explorer 10 标准|Internet Explorer 11 标准|边缘|应用商店应用|  
|----------------------|--------------------------------------------------------------------------|-----------------------------------|-----------------------------------|------------------------------------|------------------------------------|----------|----------------|  
|[__proto\_ \_属性 （对象）](../../javascript/reference/proto-property-object-javascript.md)|N|N|N|N|Y|Y|v8 (Win): N<br />v8.1 (Win): Y<br />v8.1 (Phone): Y|  
|[$1...$9 属性 (RegExp)](../../javascript/reference/dollar-1-dot-dot-dot-dollar-9-properties-regexp-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[0n 属性](../../javascript/reference/0-dot-dot-dot-n-properties-arguments-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[abs 函数](../../javascript/reference/math-abs-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[acos 函数](../../javascript/reference/math-acos-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[acosh 函数](../../javascript/reference/math-acosh-function-javascript.md)|N|N|N|N|N|Y|v8.1: N<br />v10: Y|  
|[ActiveXObject 对象](../../javascript/reference/activexobject-object-javascript.md)|Y|Y|Y|Y|Y|Y|N|  
|[加法赋值运算符 (+=)](../../javascript/reference/addition-assignment-operator-decrement-equal-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[加法运算符 (+)](../../javascript/reference/addition-operator-decrement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[apply 方法](../../javascript/reference/apply-method-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[arguments 对象](../../javascript/reference/arguments-object-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[arguments 属性](../../javascript/reference/arguments-property-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Array 对象](../../javascript/reference/array-object-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Array.from 函数 (Array)](../../javascript/reference/array-from-function-array-javascript.md)|N|N|N|N|N|N|v8.1: N<br />v10: Y|  
|[Array.isArray 函数](../../javascript/reference/array-isarray-function-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[Array.of 函数 (Array)](../../javascript/reference/array-of-function-array-javascript.md)|N|N|N|N|N|N|v8.1: N<br />v10: Y|  
|[ArrayBuffer 对象](../../javascript/reference/arraybuffer-object.md)|N|N|N|Y|Y|Y|Y|  
|[函数](../../javascript/functions-javascript.md)|N|N|N|N|N|N|v8.1: N<br />v10: Y|  
|[asin 函数](../../javascript/reference/math-asin-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Object.assign 函数 (Object)](../../javascript/reference/object-assign-function-object-javascript.md)|N|N|N|N|N|N|v8.1: N<br />v10: Y|  
|[赋值运算符 (=)](../../javascript/reference/assignment-operator-decrement-equal-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[atan 函数](../../javascript/reference/math-atan-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[atan2 函数](../../javascript/reference/math-atan2-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[atEnd 方法](../../javascript/reference/atend-method-enumerator-javascript.md)|Y|Y|Y|Y|Y|Y|N|  
|[bind 方法](../../javascript/reference/bind-method-function-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[按位“与”赋值运算符 (&=)](../../javascript/reference/bitwise-and-assignment-operator-decrement-equal-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[按位“与”运算符 (&)](../../javascript/reference/bitwise-and-operator-decrement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[按位左移运算符 (<\<)](../../javascript/reference/bitwise-left-shift-operator-decrement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[按位“取非”运算符 (~)](../../javascript/reference/bitwise-not-operator-decrement-tilde-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[按位 OR 赋值运算符 (&#124; =)](../../javascript/reference/bitwise-or-assignment-operator-decrement-equal-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[按位 OR 运算符 (&#124;)](../../javascript/reference/bitwise-or-operator-decrement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[按位右移运算符 (>>)](../../javascript/reference/bitwise-right-shift-operator-decrement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[按位 YOR 赋值运算符 (^=)](../../javascript/reference/bitwise-xor-assignment-operator-decrement-hat-equal-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[按位 YOR 运算符 (^)](../../javascript/reference/bitwise-xor-operator-decrement-hat-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[blink 方法](../../javascript/reference/html-tag-methods-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[bold 方法](../../javascript/reference/html-tag-methods-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Boolean 对象](../../javascript/reference/boolean-object-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[break 语句](../../javascript/reference/break-statement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[call 方法](../../javascript/reference/call-method-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[callee 属性](../../javascript/reference/callee-property-arguments-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[caller 属性](../../javascript/reference/caller-property-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[catch 语句](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[ceil 函数](../../javascript/reference/math-ceil-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[charAt 方法](../../javascript/reference/charat-method-string-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[charCodeAt 方法](../../javascript/reference/charcodeat-method-string-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[class 语句](../../javascript/reference/class-statement-javascript.md)|N|N|N|N|N|Exp.|v8.1: N<br />v10: Exp。|  
|[codePointAt 方法（字符串）](../../javascript/reference/codepointat-method-string-javascript.md)|N|N|N|N|N|Y|v8.1: N<br />v10: Y|  
|[逗号运算符 (,)](../../javascript/reference/comma-operator-decrement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[//（单行注释语句）](../../javascript/reference/comment-statements-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[/*..\*/ （多行注释语句）](../../javascript/reference/comment-statements-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[比较运算符](../../javascript/reference/comparison-operators-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[compile 方法](../../javascript/reference/compile-method-regular-expression-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[concat 方法（数组）](../../javascript/reference/concat-method-array-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[concat 方法（字符串）](../../javascript/reference/concat-method-string-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[条件编译](../../javascript/advanced/conditional-compilation-javascript.md)|Y|Y|Y|Y|N|N|N|  
|[条件编译变量](../../javascript/advanced/conditional-compilation-variables-javascript.md)|Y|Y|Y|Y|N|N|N|  
|[条件（三元）运算符 (?:)](../../javascript/reference/conditional-ternary-operator-decrement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[constructor 属性](../../javascript/reference/constructor-property-object-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[const 语句](../../javascript/reference/const-statement-javascript.md)|N|N|N|N|Y|Y|v8 (Win): N<br />v8.1 (Win): Y<br />v8.1 (Phone): Y|  
|[continue 语句](../../javascript/reference/continue-statement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[cos 函数](../../javascript/reference/math-cos-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[create 函数](../../javascript/reference/object-create-function-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[DataView 对象](../../javascript/reference/dataview-object.md)|N|N|N|Y|Y|Y|Y|  
|[Date 对象](../../javascript/reference/date-object-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Debug 对象](../../javascript/reference/debug-object-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Debug.setNonUserCodeExceptions 属性](../../javascript/reference/debug-setnonusercodeexceptions-property.md)|N|N|N|Y|Y|Y|Y|  
|[Debug.setNonUserCodeExceptions 属性](../../javascript/reference/debug-setnonusercodeexceptions-property.md)|N|N|N|Y|Y|Y|Y|  
|[debugger 语句](../../javascript/reference/debugger-statement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[decodeURI 函数](../../javascript/reference/decodeuri-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[DecodeURIComponent 函数](../../javascript/reference/decodeuricomponent-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[减量运算符 (--)](../../javascript/reference/increment-and-decrement-operators-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[函数](../../javascript/functions-javascript.md)|N|N|N|N|N|Exp.|v8.1: N<br />v10: Exp。|  
|[defineProperties 函数](../../javascript/reference/object-defineproperties-function-javascript.md)|N|Y*|Y|Y|Y|Y|Y|  
|[defineProperty 函数](../../javascript/reference/object-defineproperty-function-javascript.md)|N|Y*|Y|Y|Y|Y|Y|  
|[delete 运算符](../../javascript/reference/delete-operator-decrementjavascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[description 属性](../../javascript/reference/description-property-error-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[dimensions 方法](../../javascript/reference/dimensions-method-vbarray-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[除法赋值运算符 (/=)](../../javascript/reference/division-assignment-operator-decrement-equal-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[除法运算符 (/)](../../javascript/reference/division-operator-decrement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[do...while 语句](../../javascript/reference/do-dot-dot-dot-while-statement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[E 常量](../../javascript/reference/math-constants-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[encodeURI 函数](../../javascript/reference/encodeuri-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[encodeURI 组件函数](../../javascript/reference/encodeuricomponent-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[entries 方法 (Array)](../../javascript/reference/entries-method-array-javascript.md)|N|N|N|N|N|N|v8.1: N<br />v10: Y|  
|[Enumerator 对象](../../javascript/reference/enumerator-object-javascript.md)|Y|Y|Y|Y|Y|Y|N|  
|[Number 常量](../../javascript/reference/number-constants-javascript.md)|N|N|N|N|N|N|v8.1: N<br />v10: Y|  
|[相等运算符 (==)](../../javascript/reference/comparison-operators-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[错误对象](../../javascript/reference/error-object-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[stack 属性 (Error)](../../javascript/reference/stack-property-error-javascript.md)|N|N|N|Y|Y|Y|Y|  
|[stackTraceLimit 属性 (Error)](../../javascript/reference/stacktracelimit-property-error-javascript.md)|N|N|N|Y|Y|Y|Y|  
|[escape 函数](../../javascript/reference/escape-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[eval 函数](../../javascript/reference/eval-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[exec 方法](../../javascript/reference/exec-method-regular-expression-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[every 方法](../../javascript/reference/every-method-array-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[exp 函数](../../javascript/reference/math-exp-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[fill 方法 (Array)](../../javascript/reference/fill-method-array-javascript.md)|N|N|N|N|N|N|v8.1: N<br />v10: Y|  
|[filter 方法](../../javascript/reference/filter-method-array-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[finally 语句](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[findIndex 方法 (Array)](../../javascript/reference/findindex-method-array-javascript.md)|N|N|N|N|N|N|v8.1: N<br />v10: Y|  
|[fixed 方法](../../javascript/reference/html-tag-methods-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Float32Array 对象](../../javascript/reference/float32array-object.md)|N|N|N|Y|Y|Y|Y|  
|[Float64Array 对象](../../javascript/reference/float64array-object.md)|N|N|N|Y|Y|Y|Y|  
|[floor 函数](../../javascript/reference/math-floor-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[fontcolor 方法](../../javascript/reference/html-tag-methods-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[fontsize 方法](../../javascript/reference/html-tag-methods-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[for 语句](../../javascript/reference/for-statement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[forEach 方法](../../javascript/reference/foreach-method-array-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[for...in 语句](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[for...of 语句](../../javascript/reference/for-dot-dot-dot-of-statement-javascript.md)|N|N|N|N|N|Y|v8.1: N<br />v10: Y|  
|[freeze 函数](../../javascript/reference/object-freeze-function-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[fromCharCode 函数](../../javascript/reference/string-fromcharcode-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[fromCodePoint 函数](../../javascript/reference/string-fromcodepoint-function-javascript.md)|N|N|N|N|N|Y|v8.1: N<br />v10: Y|  
|[Function 对象](../../javascript/reference/function-object-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[function 语句](../../javascript/reference/function-statement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[生成器](../../javascript/advanced/iterators-and-generators-javascript.md)|N|N|N|N|N|Exp.|v8.1: N<br />v10: Exp。|  
|[getDate 方法](../../javascript/reference/getdate-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[getDay 方法](../../javascript/reference/getday-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[getFullYear 方法](../../javascript/reference/getfullyear-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[getHours 方法](../../javascript/reference/gethours-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[getItem 方法](../../javascript/reference/getitem-method-vbarray-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[getMilliseconds 方法](../../javascript/reference/getmilliseconds-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[getMinutes 方法](../../javascript/reference/getminutes-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[getMonth 方法](../../javascript/reference/getmonth-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[GetObject 函数](../../javascript/reference/getobject-function-javascript.md)|Y|Y|N|N|N|N|N|  
|[getOwnPropertyDescriptor 函数](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md)|N|Y*|Y|Y|Y|Y|Y|  
|[getOwnPropertyNames 函数](../../javascript/reference/object-getownpropertynames-function-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[getPrototypeOf 函数](../../javascript/reference/object-getprototypeof-function-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[getSeconds 方法](../../javascript/reference/getseconds-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[getTime 方法](../../javascript/reference/gettime-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[getTimezoneOffset 方法](../../javascript/reference/gettimezoneoffset-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[getUTCDate 方法](../../javascript/reference/getutcdate-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[getUTCDay 方法](../../javascript/reference/getutcday-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[getUTCFullYear 方法](../../javascript/reference/getutcfullyear-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[getUTCHours 方法](../../javascript/reference/getutchours-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[getUTCMilliseconds 方法](../../javascript/reference/getutcmilliseconds-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[getUTCMinutes 方法](../../javascript/reference/getutcminutes-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[getUTCMonth 方法](../../javascript/reference/getutcmonth-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[getUTCSeconds 方法](../../javascript/reference/getutcseconds-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[getVarDate 方法](../../javascript/reference/getvardate-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|N|  
|[getYear 方法](../../javascript/reference/getyear-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Global 对象](../../javascript/reference/global-object-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[global 属性](../../javascript/reference/global-property-regular-expression-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[大于运算符 (>)](../../javascript/reference/comparison-operators-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[大于或等于运算符 (>=)](../../javascript/reference/comparison-operators-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[hasOwnProperty 方法](../../javascript/reference/hasownproperty-method-object-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[HTML 标记方法](../../javascript/reference/html-tag-methods-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[hypot 函数](../../javascript/reference/math-hypot-function-javascript.md)|N|N|N|N|N|Y|v8.1: N<br />v10: Y|  
|[恒等运算符 (===)](../../javascript/reference/comparison-operators-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[if...else 语句](../../javascript/reference/if-dot-dot-dot-else-statement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[ignoreCase 属性](../../javascript/reference/ignorecase-property-regular-expression-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[imul 函数](../../javascript/reference/math-imul-function-javascript.md)|N|N|N|N|N|Y|v8.1: N<br />v10: Y|  
|[In 运算符](../../javascript/reference/in-operator-decrementjavascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[includes 方法（字符串）](../../javascript/reference/includes-method-string-javascript.md)|N|N|N|N|N|Y|v8.1: N<br />v10: Y|  
|[增量运算符 (++)](../../javascript/reference/increment-and-decrement-operators-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[index 属性](../../javascript/reference/index-property-regexp-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[indexOf 方法（数组）](../../javascript/reference/indexof-method-array-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[indexOf 方法（字符串）](../../javascript/reference/indexof-method-string-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[不等运算符 (!=)](../../javascript/reference/comparison-operators-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Infinity 常数](../../javascript/reference/infinity-constant-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[input 属性 ($_)](../../javascript/reference/input-property-dollar-regexp-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[instanceof 运算符](../../javascript/reference/instanceof-operator-decrementjavascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Int8Array 对象](../../javascript/reference/int8array-object.md)|N|N|N|Y|Y|Y|Y|  
|[Int16Array 对象](../../javascript/reference/int16array-object.md)|N|N|N|Y|Y|Y|Y|  
|[Int32Array 对象](../../javascript/reference/int32array-object.md)|N|N|N|Y|Y|Y|Y|  
|[Intl.Collator 对象](../../javascript/reference/intl-collator-object-javascript.md)|N|N|N|N|Y|Y|v8 (Win): N<br />v8.1 (Win): Y<br />v8.1 (Phone): Y|  
|[Intl.DateTimeFormat 对象](../../javascript/reference/intl-datetimeformat-object-javascript.md)|N|N|N|N|Y|Y|v8: N<br />v8.1: Y|  
|[Intl.NumberFormat 对象](../../javascript/reference/intl-numberformat-object-javascript.md)|N|N|N|N|Y|Y|v8: N<br />v8.1: Y|  
|[isFinite 函数](../../javascript/reference/isfinite-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[isArray 函数](../../javascript/reference/array-isarray-function-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[IsExtensible 函数](../../javascript/reference/object-isextensible-function-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[isFrozen 函数](../../javascript/reference/object-isfrozen-function-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[isInteger 函数](../../javascript/reference/number-isinteger-function-number-javascript.md)|N|N|N|N|N|Y|v8.1: N<br />v10: Y|  
|[isNaN 函数](../../javascript/reference/isnan-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[isNaN 函数（数字）](../../javascript/reference/number-isnan-function-number-javascript.md)|N|N|N|N|N|Y|v8.1: N<br />v10: Y|  
|[ISO 日期格式](../../javascript/date-and-time-strings-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[IsPrototypeOf 方法](../../javascript/reference/isprototypeof-method-object-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[isSealed 函数](../../javascript/reference/object-issealed-function-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[italics 方法](../../javascript/reference/html-tag-methods-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[迭代器](../../javascript/advanced/iterators-and-generators-javascript.md)|N|N|N|N|N|Y|v8.1: N<br />v10: Y|  
|[item 方法](../../javascript/reference/item-method-enumerator-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[join 方法](../../javascript/reference/join-method-array-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[JSON 对象](../../javascript/reference/json-object-javascript.md)|N|Y|Y|Y|Y|Y|Y|  
|[keys 函数](../../javascript/reference/object-keys-function-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[keys 方法 (Array)](../../javascript/reference/keys-method-array-javascript.md)|N|N|N|N|N|Y|v8.1: N<br />v10: Y|  
|[Labeled 语句](../../javascript/reference/labeled-statement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[lastIndex 属性](../../javascript/reference/lastindex-property-regexp-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[lastIndexOf 方法（数组）](../../javascript/reference/lastindexof-method-array-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[lastIndexOf 方法（字符串）](../../javascript/reference/lastindexof-method-string-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[lastMatch 属性 ($&)](../../javascript/reference/lastmatch-property-dollar-regexp-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[lastParen 属性 ($+)](../../javascript/reference/lastparen-property-dollar-regexp-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[lbound 方法](../../javascript/reference/lbound-method-vbarray-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[leftContext 属性 ($')](../../javascript/reference/leftcontext-property-dollar-grave-regexp-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[左移赋值运算符 (<<=)](../../javascript/reference/left-shift-assignment-operator-decrement-equal-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[length 属性（参数）](../../javascript/reference/length-property-arguments-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[length 属性（数组）](../../javascript/reference/length-property-array-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[length 属性（函数）](../../javascript/reference/length-property-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[length 属性（字符串）](../../javascript/reference/length-property-string-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[小于运算符 (<)](../../javascript/reference/comparison-operators-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[小于或等于运算符 (<=)](../../javascript/reference/comparison-operators-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[let 语句](../../javascript/reference/let-statement-javascript.md)|N|N|N|N|Y|Y|v8: N<br />v8.1: Y|  
|[link 方法](../../javascript/reference/html-tag-methods-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[LN2 常量](../../javascript/reference/math-constants-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[LN10 常量](../../javascript/reference/math-constants-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[localeCompare 方法](../../javascript/reference/localecompare-method-string-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[log 函数](../../javascript/reference/math-log-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[LOG2E 常量](../../javascript/reference/math-constants-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[LOG10E 常量](../../javascript/reference/math-constants-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[逻辑“与”运算符 (&&)](../../javascript/reference/logical-and-operator-decrement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[逻辑“非”运算符 (!)](../../javascript/reference/logical-not-operator-decrement-exclpt-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[逻辑或运算符 (&#124; &#124;)](../../javascript/reference/logical-or-operator-decrement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[map 方法](../../javascript/reference/map-method-array-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[Map 对象](../../javascript/reference/map-object-javascript.md)|N|N|N|N|Y|Y|v8: N<br />v8.1: Y|  
|[match 方法](../../javascript/reference/match-method-string-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Math 对象](../../javascript/reference/math-object-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[max 函数](../../javascript/reference/math-max-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[MAX_VALUE 常量](../../javascript/reference/number-constants-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[message 属性](../../javascript/reference/message-property-error-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[min 函数](../../javascript/reference/math-min-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[MIN_VALUE 常量](../../javascript/reference/number-constants-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[取模赋值运算符 (%=)](../../javascript/reference/modulus-assignment-operator-decrement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[取模运算符 (%)](../../javascript/reference/modulus-operator-decrementjavascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[moveFirst 方法](../../javascript/reference/movefirst-method-enumerator-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[moveNext 方法](../../javascript/reference/movenext-method-enumerator-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[multiline 属性](../../javascript/reference/multiline-property-regular-expression-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[乘法赋值运算符 (*=)](../../javascript/reference/multiplication-assignment-operator-decrement-equal-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[乘法运算符 (*)](../../javascript/reference/multiplication-operator-decrement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[name 属性](../../javascript/reference/name-property-error-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[NaN 常量（全局）](../../javascript/reference/nan-constant-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[NaN 常量（数字）](../../javascript/reference/number-constants-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[NEGATIVE_INFINITY 常量](../../javascript/reference/number-constants-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[new 运算符](../../javascript/reference/new-operator-decrementjavascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[非恒等运算符 (!==)](../../javascript/reference/comparison-operators-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[now 函数](../../javascript/reference/date-now-function-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[Number 对象](../../javascript/reference/number-object-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[number 属性](../../javascript/reference/number-property-error-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Object 对象](../../javascript/reference/object-object-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[运算符优先级](../../javascript/operator-subtractprecedence-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Date.parse 函数](../../javascript/reference/date-parse-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[JSON.parse 函数](../../javascript/reference/json-parse-function-javascript.md)|N|Y|Y|Y|Y|Y|Y|  
|[parseFloat 函数](../../javascript/reference/parsefloat-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[parseInt 函数](../../javascript/reference/parseint-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[PI 常量](../../javascript/reference/math-constants-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[pop 方法](../../javascript/reference/pop-method-array-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[POSITIVE_INFINITY 常量](../../javascript/reference/number-constants-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[pow 函数](../../javascript/reference/math-pow-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[preventExtensions 函数](../../javascript/reference/object-preventextensions-function-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[Promise 对象](../../javascript/reference/promise-object-javascript.md)|N|N|N|N|N|Y|v8.1: N<br />v10: Y|  
|[prototype 属性](../../javascript/reference/prototype-property-object-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[propertyIsEnumerable 方法](../../javascript/reference/propertyisenumerable-method-object-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Proxy 对象](../../javascript/reference/proxy-object-javascript.md)|N|N|N|N|N|Y|v8.1: N<br />v10: Y|  
|[push 方法](../../javascript/reference/push-method-array-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[random 函数](../../javascript/reference/math-random-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[raw 函数](../../javascript/reference/string-raw-function-javascript.md)|N|N|N|N|N|Y|v8.1: N<br />v10: Y|  
|[reduce 方法](../../javascript/reference/reduce-method-array-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[reduceRight 方法](../../javascript/reference/reduceright-method-array-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[RegExp 对象](../../javascript/reference/regexp-object-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[正则表达式对象](../../javascript/reference/regular-expression-object-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[正则表达式语法](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)|Y|Y|Y|Y|Y|Y|Y|  
|[正则表达式 /y 标志](../../javascript/reference/regular-expression-object-javascript.md)|N|N|N|N|N|Exp.|v8.1: N<br />v10: Exp。|  
|[repeat 方法（字符串）](../../javascript/reference/repeat-method-string-javascript.md)|N|N|N|N|N|Y|v8.1: N<br />v10: Y|  
|[replace 方法](../../javascript/reference/replace-method-string-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[函数](../../javascript/functions-javascript.md)|N|N|N|N|N|N|v8.1: N<br />v10: Y|  
|[return 语句](../../javascript/reference/return-statement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[reverse 方法](../../javascript/reference/reverse-method-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[rightContext 属性 ($')](../../javascript/reference/rightcontext-property-dollar-regexp-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[右移赋值运算符 (>>=)](../../javascript/reference/right-shift-assignment-operator-decrement-equal-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[round 函数](../../javascript/reference/math-round-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[ScriptEngine 函数](../../javascript/reference/scriptengine-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[ScriptEngineBuildVersion 函数](../../javascript/reference/scriptenginebuildversion-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[ScriptEngineMajorVersion 函数](../../javascript/reference/scriptenginemajorversion-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[ScriptEngineMinorVersion 函数](../../javascript/reference/scriptengineminorversion-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[seal 函数](../../javascript/reference/object-seal-function-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[search 方法](../../javascript/reference/search-method-string-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Set 对象](../../javascript/reference/set-object-javascript.md)|N|N|N|N|Y|Y|v8: N<br />v8.1: Y|  
|[setDate 方法](../../javascript/reference/setdate-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[setFullYear 方法](../../javascript/reference/setfullyear-method-date-javascript.md)||Y|Y|Y|Y|Y|Y|  
|[setHours 方法](../../javascript/reference/sethours-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[setMilliseconds 方法](../../javascript/reference/setmilliseconds-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[setMinutes 方法](../../javascript/reference/setminutes-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[setMonth 方法](../../javascript/reference/setmonth-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[setSeconds 方法](../../javascript/reference/setseconds-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[setTime 方法](../../javascript/reference/settime-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[setUTCDate 方法](../../javascript/reference/setutcdate-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[setUTCFullYear 方法](../../javascript/reference/setutcfullyear-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[setUTCHours 方法](../../javascript/reference/setutchours-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[setUTCMilliseconds 方法](../../javascript/reference/setutcmilliseconds-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[setUTCMinutes 方法](../../javascript/reference/setutcminutes-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[setUTCMonth 方法](../../javascript/reference/setutcmonth-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[setUTCSeconds 方法](../../javascript/reference/setutcseconds-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[setYear 方法](../../javascript/reference/setyear-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[shift 方法](../../javascript/reference/shift-method-array-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[sin 函数](../../javascript/reference/math-sin-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[slice 方法（数组）](../../javascript/reference/slice-method-array-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[slice 方法（字符串）](../../javascript/reference/slice-method-string-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[small 方法](../../javascript/reference/html-tag-methods-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[some 方法](../../javascript/reference/some-method-array-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[sort 方法](../../javascript/reference/sort-method-array-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[source 属性](../../javascript/reference/source-property-regular-expression-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[splice 方法](../../javascript/reference/splice-method-array-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[split 方法](../../javascript/reference/split-method-string-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[函数](../../javascript/functions-javascript.md)|N|N|N|N|N|Y|v8.1: N<br />v10: Y|  
|[sqrt 函数](../../javascript/reference/math-sqrt-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[SQRT1_2 常量](../../javascript/reference/math-constants-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[SQRT2 常量](../../javascript/reference/math-constants-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[使用严格指令](../../javascript/reference/use-strict-directive.md)|N|N|N|Y|Y|Y|Y|  
|[strike 方法](../../javascript/reference/html-tag-methods-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[String 对象](../../javascript/reference/string-object-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[JSON.stringify 函数](../../javascript/reference/json-stringify-function-javascript.md)|N|Y|Y|Y|Y|Y|Y|  
|[sub 方法](../../javascript/reference/html-tag-methods-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[substr 方法](../../javascript/reference/substr-method-string-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[substring 方法](../../javascript/reference/substring-method-string-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[减法赋值运算符 (-=)](../../javascript/reference/subtraction-assignment-operator-decrement-equal-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[减法运算符 (-)](../../javascript/reference/subtraction-operator-decrement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[sup 方法](../../javascript/reference/html-tag-methods-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[switch 语句](../../javascript/reference/switch-statement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Symbol 对象](../../javascript/reference/symbol-object-javascript.md)|N|N|N|N|N|Y|v8.1: N<br />v10: Y|  
|[tan 函数](../../javascript/reference/math-tan-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[模板字符串](../../javascript/advanced/template-strings-javascript.md)|N|N|N|N|N|Y|v8.1: N<br />v10: Y|  
|[test 方法](../../javascript/reference/test-method-regular-expression-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[this 语句](../../javascript/reference/this-statement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[throw 语句](../../javascript/reference/throw-statement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[toArray 方法](../../javascript/reference/toarray-method-vbarray-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[toDateString 方法](../../javascript/reference/todatestring-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[toExponential 方法](../../javascript/reference/toexponential-method-number-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[toFixed 方法](../../javascript/reference/tofixed-method-number-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[toGMTString 方法](../../javascript/reference/togmtstring-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[toISOString 方法](../../javascript/reference/toisostring-method-date-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[toJSON 方法](../../javascript/reference/tojson-method-date-javascript.md)|N|Y|Y|Y|Y|Y|Y|  
|[toLocaleDateString 方法](../../javascript/reference/tolocaledatestring-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[toLocaleLowercase 方法](../../javascript/reference/tolocalelowercase-method-string-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[toLocaleString 方法](../../javascript/reference/tolocalestring-method-object-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[toLocaleTimeString 方法](../../javascript/reference/tolocaletimestring-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[toLocaleUppercase 方法](../../javascript/reference/tolocaleuppercase-method-string-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[toLowerCase 方法](../../javascript/reference/tolowercase-method-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[toPrecision 方法](../../javascript/reference/toprecision-method-number-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[toString 方法](../../javascript/reference/tostring-method-object-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[toTimeString 方法](../../javascript/reference/totimestring-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[toUpperCase 方法](../../javascript/reference/touppercase-method-string-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[toUTCString 方法](../../javascript/reference/toutcstring-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[trim 方法](../../javascript/reference/trim-method-string-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[try 语句](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[typeof 运算符](../../javascript/reference/typeof-operator-decrementjavascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[ubound 方法](../../javascript/reference/ubound-method-vbarray-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Uint8Array 对象](../../javascript/reference/uint8array-object.md)|N|N|N|Y|Y|Y|Y|  
|[Uint16Array 对象](../../javascript/reference/uint16array-object.md)|N|N|N|Y|Y|Y|Y|  
|[Uint32Array 对象](../../javascript/reference/uint32array-object.md)|N|N|N|Y|Y|Y|Y|  
|[Uint8ClampedArray 对象](../../javascript/reference/uint8clampedarray-object-javascript.md)|N|N|N|N|Y|Y|v8: No<br />v8.1 (Win): Yes<br />v8.1 (Phone): No<br />v10: Y|  
|[一元求非运算符 (-)](../../javascript/reference/subtraction-operator-decrement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[undefined 常量](../../javascript/reference/undefined-constant-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[unescape 函数](../../javascript/reference/unescape-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Unicode 码位转义字符](../../javascript/advanced/special-characters-javascript.md)|N|N|N|N|N|Y|v8.1: N<br />v10: Y|  
|[unshift 方法](../../javascript/reference/unshift-method-array-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[无符号右移赋值运算符 (>>>=)](../../javascript/reference/unsigned-right-shift-assignment-operator-decrement-equal-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[无符号右移运算符 (>>>)](../../javascript/reference/unsigned-right-shift-operator-decrement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[使用严格指令](../../javascript/reference/use-strict-directive.md)|N|N|N|Y|Y|Y|Y|  
|[UTC 函数](../../javascript/reference/date-utc-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[valueOf 方法](../../javascript/reference/valueof-method-object-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[values 方法 (Array)](../../javascript/reference/values-method-array-javascript.md)|N|N|N|N|N|Y|v8.1: N<br />v10: Y|  
|[var 语句](../../javascript/reference/var-statement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[VBArray 对象](../../javascript/reference/vbarray-object-javascript.md)|Y|Y|Y|Y|Y|Y|N|  
|[void 运算符](../../javascript/reference/void-operator-decrementjavascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[WeakMap 对象](../../javascript/reference/weakmap-object-javascript.md)|N|N|N|N|Y|Y|v8: N<br />v8.1: Y|  
|[WeakSet 对象](../../javascript/reference/weakset-object-javascript.md)|N|N|N|N|N|Y|v8.1: N<br />v10: Y|  
|[while 语句](../../javascript/reference/while-statement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[WinRTError 对象](../../javascript/reference/winrterror-object-javascript.md)|N|N|N|Y|Y|Y|Y|  
|[with 语句](../../javascript/reference/with-statement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[write 函数](../../javascript/reference/debug-write-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[writeln 函数](../../javascript/reference/debug-writeln-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
  
 \*支持 DOM 对象，但不是用户定义的对象。 可以指定 `enumerable` 和 `configurable` 特性，但不使用它们。  
  
## <a name="see-also"></a>另请参阅  
 [定义文档兼容性](http://go.microsoft.com/fwlink/?LinkId=208537)