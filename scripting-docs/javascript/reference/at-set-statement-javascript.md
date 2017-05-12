---
title: "@set 语句 (JavaScript) | Microsoft Docs"
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
  - "@set_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "@set 语句"
  - "条件编译, 变量"
ms.assetid: 36f15926-3e69-422d-82a2-d186dc088203
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# @set 语句 (JavaScript)
创建使用条件编译语句的变量。  
  
> [!WARNING]
>  Internet Explorer 11 标准模式和 [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)]应用不支持条件编译。  Internet Explorer 10 标准模式和所有早期版本支持条件编译。  
  
## 语法  
  
```  
  
@set @varname = term   
```  
  
## 参数  
 *varname*  
 必选。  有效的 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 变量名称。  必须始终在前面放置一个“@”字符。  
  
 `term`  
 必选。  零个或多个一元运算符，其后跟一个常量、条件编译变量或用圆括号括起来的表达式。  
  
## 备注  
 条件编译支持数字变量和布尔变量。  不支持字符串。  使用 `@set` 创建的变量通常在条件编译语句中使用，但也可在 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 代码中的任何位置使用。  
  
 变量声明的示例如下所示：  
  
```javascript  
  
        @set @myvar1 = 12  
  
@set @myvar2 = (@myvar1 * 20)  
  
@set @myvar3 = @_jscript_version  
```  
  
 用圆括号括起来的表达式中支持下列运算符：  
  
-   `!  ~`  
  
-   `* / %`  
  
-   `+ -`  
  
-   `<< >> >>>`  
  
-   `< <= > >=`  
  
-   `== != === !==`  
  
-   `& ^ |`  
  
-   `&& | |`  
  
 如果在定义一个变量之前就使用它，则它的值为 `NaN`。  可通过使用 `@if` 语句检查 `NaN`：  
  
```javascript  
@if (@newVar != @newVar)  
   ...  
```  
  
 之所以能这样做是因为 `NaN` 是唯一一个不等于其自身的值。  
  
## 要求  
 在所有版本的 Internet Explorer 中受支持，但在 [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)]应用中不受支持。  
  
## 请参阅  
 [条件编译](../../javascript/advanced/conditional-compilation-javascript.md)   
 [条件编译变量](../../javascript/advanced/conditional-compilation-variables-javascript.md)   
 [@cc\_on 语句](../../javascript/reference/at-cc-on-statement-javascript.md)   
 [@if 语句](../../javascript/reference/at-if-statement-javascript.md)