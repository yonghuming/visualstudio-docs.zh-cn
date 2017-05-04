---
title: "function 语句 (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "function_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "声明函数"
  - "声明函数, 语法"
  - "function 语句"
  - "new 运算符"
ms.assetid: cc9cfd43-1305-41c8-ad67-545d20f4fafe
caps.latest.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 20
---
# function 语句 (JavaScript)
声明一个新函数。  
  
## 语法  
  
```  
function functionname ([arg1 [, arg2 [,...[, argN]]]]) {  
    statements  
}   
```  
  
## 参数  
 `functionname`  
 必需。  函数的名称。  
  
 `arg1...argN`  
 可选。  函数理解的参数的可选的用逗号分隔的列表。  
  
 `statements`  
 可选。  一个或多个 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 语句。  
  
## 备注  
 使用 `function` 语句来声明一个以后要使用的函数。  在脚本的其他地方调用该函数前，不执行 `statements` 中包含的代码。  
  
 [return](../../javascript/reference/return-statement-javascript.md) 语句用于从函数返回值。  您不必使用 `return` 语句；程序将在到达函数结尾时返回。  如果未在函数中执行 `return` 语句，或如果 `return` 语句没有表达式，则函数返回值 `undefined`。  
  
> [!NOTE]
>  在调用函数时，请确保包括圆括号和任何所需的参数。  调用不带括号的函数将返回对函数的引用，而不是函数的结果。  
  
## 示例  
 下面的示例阐释了 `function` 语句的用法。  
  
```javascript  
function myfunction (arg1, arg2) {  
    var r = arg1 * arg2;  
    return(r);  
}  
```  
  
## 示例  
 可将函数分配给变量。  下面的示例阐释了这一过程。  
  
```javascript  
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
  
## 要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 请参阅  
 [new 运算符](../../javascript/reference/new-operator-decrementjavascript.md)