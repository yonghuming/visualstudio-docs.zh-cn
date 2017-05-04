---
title: "switch 语句 (JavaScript) | Microsoft Docs"
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
  - "switch_JavaScriptKeyword"
  - "default_JavaScriptKeyword"
  - "case_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "switch 语句"
ms.assetid: 61f80e8b-3739-4146-a893-c2832d92b28c
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# switch 语句 (JavaScript)
当指定的表达式的值与一个标签匹配时，使一条或多条语句得以执行。  
  
## 语法  
  
```  
switch (expression) {  
    case label :  
        statementlist  
    case label :  
    default :  
        statementlist  
}   
```  
  
## 参数  
 `expression`  
 要计算的表达式。  
  
 `label`  
 要与 `expression` 相匹配的标识符。  如果 `label` 是 `expression`，则从冒号后面紧接的 `statementlist` 开始执行，并继续此执行，直到遇到一个可选 `break` 语句，或到达 `switch` 语句的末尾为止。  
  
 `statementlist`  
 要执行的一个或多个语句。  
  
## 备注  
 使用 `default` 子句来提供一个语句，该语句只在没有任何一个标签值与 `expression` 匹配时才执行。  它可以出现在 `switch` 代码块内的任何地方。  
  
 可以指定零个或多个 `label` 块。  如果没有 `label` 与 `expression` 的值匹配，并且没有提供 `default` 示例，则不执行任何语句。  
  
 `switch` 语句将按如下流程执行：  
  
-   计算 `expression` 的值并按顺序查看 `label`，直到找到一个匹配项。  
  
-   如果 `label` 值等于 `expression`，则执行其附带的 `statementlist`。  
  
     继续执行，直到遇到一个 `break` 语句，或直到 `switch` 语句结束。  这意味着，如果没有使用 `break` 语句，则将执行多个 `label` 块。  
  
-   如果任何 `label` 均不等于 `expression`，则转到 `default` 示例。  如果没有 `default` 示例，则转到最后一步。  
  
-   在 `switch` 代码块末尾之后的语句处继续执行过程。  
  
## 示例  
 下面的示例将测试一个对象的类型。  
  
```javascript  
function MyObjectType(obj) {  
    switch (obj.constructor) {  
        case Date:  
            document.write("Object is a Date.");  
            break;  
        case Number:  
            document.write("Object is a Number.");  
            break;  
        case String:  
            document.write("Object is a String.");  
            break;  
        default:  
            document.write("Object is unknown.");  
    }  
}  
  
// Output when obj is a Date:  
// Object is a Date.  
  
// Output when obj is a Number:  
// Object is a Number.  
  
// Output when obj is a String:  
// Object is a String.  
  
// Output when obj is something other than a Date, Number, or String:  
// Object is unknown.  
  
```  
  
## 示例  
 如果您未使用 `break` 语句，则以下代码将显示发生的情况。  
  
```javascript  
function MyObjectType(obj) {  
    switch (obj.constructor) {  
        case Date:  
            document.write("Object is a Date.");  
        case Number:  
            document.write("Object is a Number.");  
        case String:  
            document.write("Object is a String.");  
        default:  
            document.write("Object is unknown.");  
    }  
}  
  
// Output when obj is a Date:  
// Object is a Date.Object is a Number.Object is a String.Object is unknown.  
  
// Output when obj is a Number:  
// Object is a Number.Object is a String.Object is unknown.  
  
// Output when obj is a String:  
// Object is a String.Object is unknown.  
  
// Output when obj is something other than a Date, Number, or String:  
// Object is unknown.  
  
```  
  
## 要求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## 请参阅  
 [break 语句](../../javascript/reference/break-statement-javascript.md)   
 [if...else 语句](../../javascript/reference/if-dot-dot-dot-else-statement-javascript.md)