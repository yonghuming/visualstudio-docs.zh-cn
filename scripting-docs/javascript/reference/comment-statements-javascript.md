---
title: "Comment 语句 (JavaScript) | Microsoft Docs"
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
  - "Comment_JavaScript"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "注释语句"
  - "注释, 忽略"
ms.assetid: b604824f-ac17-49d3-bcdb-2a893ab5fff8
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Comment 语句 (JavaScript)
使 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 分析器忽略注释。  
  
## 语法  
  
```  
Single-line Comment:  
// comment   
```  
  
```  
Multiline Comment:  
/*  
comment  
*/  
```  
  
```  
Comments with conditional compilation:  
//@CondStatement   
  
/*@  
condStatement  
@*/  
```  
  
## 备注  
 `comment` 参数是你想包含在脚本中的任何注释的文本。  如果激活条件编译，则将使用 `condStatement` 参数。  如果使用单行注释，则“\/\/”和“@”字符之间没有空格。  
  
 使用注释来防止 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 分析器读取脚本的各部分。  可使用注释将解释性备注包含在程序中。  
  
 如果使用单行注释，分析器将忽略注释标记和行尾间的任何文本。  如果使用单行注释，分析器将忽略开始标记和结束标记间的任何文本。  
  
 注释用于支持条件编译，同时与不支持此功能的浏览器保持兼容。  这些浏览器将这些形式的注释分别视为单行或多行注释。  
  
## 示例  
 下面的示例说明了注释的最常见的用法。  
  
```javascript  
/* This is a multiline comment that  
    can span as many lines as necessary.  */  
function myfunction(arg1, arg2){  
    var r;  
    // This is a single line comment.  
    r = arg1 + arg2  
    return(r);  
}  
```  
  
## 示例  
 下面的示例演示如何使用条件编译。  此示例使用特殊的注释分隔符，仅在 `@cc_on` 语句激活条件编译后使用这些分隔符。  不支持条件编译的脚本引擎仅看到表明条件编译不受支持的消息。  
  
```javascript  
/*@cc_on @*/  
/*@if (@_jscript_version >= 4)  
    alert("JavaScript version 4 or better");  
    @else @*/  
    alert("Conditional compilation not supported by this scripting engine.");  
/*@end @*/  
```  
  
## 要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]