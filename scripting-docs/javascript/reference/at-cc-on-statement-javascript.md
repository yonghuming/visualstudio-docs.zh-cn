---
title: "@cc_on 语句 (JavaScript) | Microsoft Docs"
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
  - "@cc_on_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "@cc_on 语句"
  - "@if 语句"
  - "@set 语句"
  - "条件编译, 激活"
ms.assetid: fdeda7ee-b9f4-4e52-8aa2-21c90c02a332
caps.latest.revision: 21
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 21
---
# @cc_on 语句 (JavaScript)
在脚本的注释内激活条件编译支持功能。  
  
> [!WARNING]
>  Internet Explorer 11 标准模式和 [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)]应用不支持条件编译。  Internet Explorer 10 标准模式和所有早期版本支持条件编译。  
  
## 语法  
  
```  
@cc_on   
```  
  
## 备注  
 `@cc_on` 语句在脚本中的注释内激活条件编译。  
  
 在为 ASP 或 ASP.NET 页或命令行程序编写的脚本中很少使用条件编译变量，这是因为可以使用其他方法来确定编译器的功能。  
  
 当编写用于网页的脚本时，始终将条件编译代码放入注释中。  这样，不支持条件编译的主机就可以将其忽略。  
  
 强烈建议在注释中使用 `@cc_on` 语句，这样一来，不支持条件编译的浏览器将接受脚本作为有效语法：  
  
 注释外的 `@if` 或 `@set` 语句也将激活条件编译。  
  
## 示例  
 下面的示例阐释了 `@cc_on` 语句的用法。  
  
```javascript  
/*@cc_on @*/  
/*@  
    document.write("JavaScript version: " + @_jscript_version + ".");  
    document.write("<br />");  
    @if (@_win32)  
        document.write("Running on the 32-bit version of Windows.");  
    @elif (@_win16)  
        document.write("Running on the 16-bit version of Windows.");  
    @else  
        document.write("Running on a different operating system.");  
    @end  
@*/  
```  
  
## 要求  
 在所有版本的 Internet Explorer 中受支持，但在 [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)]应用中不受支持。  
  
## 请参阅  
 [条件编译](../../javascript/advanced/conditional-compilation-javascript.md)   
 [条件编译变量](../../javascript/advanced/conditional-compilation-variables-javascript.md)   
 [@if 语句](../../javascript/reference/at-if-statement-javascript.md)   
 [@set 语句](../../javascript/reference/at-set-statement-javascript.md)