---
title: "@if 语句 (JavaScript) | Microsoft Docs"
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
  - "@if_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "@if 语句"
  - "条件语句, if"
  - "elif 语句"
  - "else 语句"
  - "if 语句, @if"
ms.assetid: ff11b29d-c06a-4276-b11d-db73e2da98ac
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# @if 语句 (JavaScript)
根据表达式的值有条件地执行一组语句。  
  
> [!WARNING]
>  Internet Explorer 11 标准模式和 [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)]应用不支持条件编译。  Internet Explorer 10 标准模式和所有早期版本支持条件编译。  
  
## 语法  
  
```  
  
      @if (  
   condition1  
)  
   text1  
[@elif (  
   condition2  
)  
   text2]  
[@else  
   text3]  
@end   
```  
  
## 参数  
 *condition1、condition2*  
 可选。  一个可强迫转换为布尔表达式的表达式。  
  
 `text1`  
 可选。  `condition1` 为 **true** 时要分析的文本。  
  
 `text2`  
 可选。  `condition1` 为 **false** 且 `condition2` 为 **true** 时要分析的文本。  
  
 `text3`  
 可选。  `condition1` 和 `condition2` 均为 **false** 时要分析的文本。  
  
## 备注  
 在编写 `@if` 语句时，不必将每个子句放在独立的行中。  可使用多个 **@elif** 子句。  但是，所有 **@elif** 子句必须在 **@else** 子句之前出现。  
  
 通常使用 `@if` 语句确定应使用若干选项中的哪个文本进行文本输出。  
  
 在为 ASP 或 ASP.NET 页或命令行程序编写的脚本中很少使用条件编译变量。  这是因为编译器的功能可以使用其他方法来确定。  
  
 当编写用于网页的脚本时，始终将条件编译代码添加到注释中。  这样，不支持条件编译的主机就可以将其忽略。  
  
## 示例  
 以下示例阐释了 **@if...@elif…@else...@end** 语句的用法。  
  
```javascript  
/*@cc_on @*/  
/*@  
    document.write("JavaScript version: " + @_jscript_version + ".");  
    document.write("<br />");  
    @if (@_win32)  
        document.write("Running on a 32-bit version of Windows.");  
    @elif (@_win16)  
        document.write("Running on a 16-bit version of Windows.");  
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
 [@cc\_on 语句](../../javascript/reference/at-cc-on-statement-javascript.md)   
 [@set 语句](../../javascript/reference/at-set-statement-javascript.md)