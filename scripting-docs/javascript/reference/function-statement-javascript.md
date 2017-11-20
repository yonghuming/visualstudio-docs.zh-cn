---
title: "函数语句 (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: function_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- new operator
- declaring functions, syntax
- function statement
- declaring functions
ms.assetid: cc9cfd43-1305-41c8-ad67-545d20f4fafe
caps.latest.revision: "20"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e5fac3647e9374a9c909a420b73b86354cac69b6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="function-statement-javascript"></a>function 语句 (JavaScript)
声明新函数。  
  
## <a name="syntax"></a>语法  
  
```  
function functionname ([arg1 [, arg2 [,...[, argN]]]]) {  
    statements  
}   
```  
  
## <a name="parameters"></a>参数  
 `functionname`  
 必需。 函数名。  
  
 `arg1...argN`  
 可选。 函数可理解的自变量的可选、以逗号分隔的列表。  
  
 `statements`  
 可选。 一个或多个[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]语句。  
  
## <a name="remarks"></a>备注  
 使用`function`语句来声明函数以供将来使用。 中包含的代码`statements`之前在脚本中的其他位置调用该函数不执行。  
  
 [返回](../../javascript/reference/return-statement-javascript.md)语句用于从函数返回一个值。 无需使用`return`语句; 该程序将在到达该函数的末尾时返回。 如果没有`return`语句将在函数中，或者如果`return`语句没有任何表达式，则函数返回值`undefined`。  
  
> [!NOTE]
>  当调用函数时，一定要包括圆括号和任何所需的参数。 调用不带括号的函数返回的函数，不是结果的函数的引用。  
  
## <a name="example"></a>示例  
 下面的示例阐释了 `function` 语句的用法。  
  
```JavaScript  
function myfunction (arg1, arg2) {  
    var r = arg1 * arg2;  
    return(r);  
}  
```  
  
## <a name="example"></a>示例  
 函数可以分配给变量。 下列示例对此进行了阐释。  
  
```JavaScript  
function AddFive(x) {  
    return x + 5;  
}  
  
function AddTen(x) {  
    return x + 10;  
}  
  
var condition = false;  
  
var MyFunc;  
if (condition) {  
    MyFunc = AddFive;  
}  
else {  
    MyFunc = AddTen;  
}  
  
var result = MyFunc(123);  
// Output: 133  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [new 运算符](../../javascript/reference/new-operator-decrementjavascript.md)