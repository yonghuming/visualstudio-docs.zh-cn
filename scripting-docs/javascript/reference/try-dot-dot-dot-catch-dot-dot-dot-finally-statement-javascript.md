---
title: "try...catch...finally 语句 (JavaScript) | Microsoft Docs"
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
  - "try_JavaScriptKeyword"
  - "finally_JavaScriptKeyword"
  - "catch_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "try-catch 异常处理"
  - "try-catch 异常处理, 关于 try-catch 异常处理"
  - "try-catch 异常处理, catch 块"
  - "try-catch 异常处理, finally 块"
ms.assetid: b7a0a54e-dfaa-4e41-bf25-bcaa43e601fb
caps.latest.revision: 28
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 28
---
# try...catch...finally 语句 (JavaScript)
设置代码块，其中一个块中引发的错误将在另一个块中得到处理。  在 `catch` 块中捕获 `try` 块中引发的错误。  [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## 语法  
  
```  
try {  
    tryStatements  
}  
catch(exception){  
    catchStatements  
}  
finally {  
    finallyStatements  
}  
```  
  
## 参数  
 `tryStatements`  
 必需。  可能发生错误的语句。  
  
 `exception`  
 必需。  任何变量名称。  `exception` 的初始值是引发的错误的值。  
  
 `catchStatements`  
 可选。  用于处理关联的 `tryStatements` 中发生的错误的语句。  
  
 `finallyStatements`  
 可选。  发生所有其他错误处理后无条件执行的语句。  
  
## 备注  
 `try...catch...finally` 语句提供了一种在保持代码运行的同时处理给定代码块中可能发生的部分或所有错误的方法。  如果出现了未处理的错误，[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 将提供常规错误消息。  
  
 `try` 块包含可能引发错误的代码，而 `catch` 块包含处理部分或所有错误的代码。  如果 `try` 块中发生错误，则程序控件将传递给 `catch` 块。  `exception` 的值是 `try` 块中发生的错误的值。  如果未发生错误，则绝不执行 `catch` 块中的代码。  
  
 可以通过使用 `throw` 语句重新引发错误来将错误传递到下一级别。  
  
 在执行 `try` 块中的所有语句并在 `catch` 块中完成错误处理后，无论是否已处理错误，都将执行 `finally` 块中的语句。  `finally` 块中的代码保证能运行，除非发生未处理的错误（例如，**catch** 块内发生的运行时错误）。  
  
## 示例  
 以下示例导致引发 `ReferenceError` 异常，并显示错误名称及其消息。  
  
```javascript  
try {  
    addalert("bad call");  
}  
catch(e) {  
    document.write ("Error Message: " + e.message);  
    document.write ("<br />");  
    document.write ("Error Code: ");  
    document.write (e.number & 0xFFFF);  
    document.write ("<br />");  
    document.write ("Error Name: " + e.name);  
}  
  
// Output:  
Error Message: 'addalert' is undefined  
Error Code: 5009  
Error Name: ReferenceError  
  
```  
  
## 示例  
 以下示例演示如何重新引发错误和执行嵌套的 `try…catch` 块。  在从嵌套的 `try` 块引发错误时，会将错误传递给嵌套的 `catch` 块，这将重新引发错误。  嵌套的 `finally` 块运行后，外部 `catch` 块才处理错误，最终外部 `finally` 块将运行。  
  
```javascript  
try {  
    document.write("Outer try running...<br/>");  
  
    try {  
        document.write("Nested try running...<br/>");  
        throw new Error(301, "an error");  
    }  
    catch (e) {  
        document.write ("Nested catch caught " + e.message + "<br/>");  
        throw e;  
    }  
    finally {  
        document.write ("Nested finally is running...<br/>");  
    }  
}  
catch (e) {  
    document.write ("Outer catch caught " + e.message + "<br/>");  
}  
finally {  
    document.write ("Outer finally running");  
}  
  
// Output:  
// Outer try running...  
// Nested try running...  
// Nested catch caught error from nested try  
// Nested finally is running...  
// Outer catch caught error from nested try  
// Outer finally running  
```  
  
## 要求  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
> [!NOTE]
>  从 Internet Explorer 8 标准模式开始，不再需要 **catch** 块来运行 `finally`。  
  
## 请参阅  
 [throw 语句](../../javascript/reference/throw-statement-javascript.md)   
 [Script Junkie 配置向导示例应用](http://code.msdn.microsoft.com/Script-Junkie-Configuration-543ece24)