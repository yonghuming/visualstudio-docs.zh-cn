---
title: "compile 方法（正则表达式）(JavaScript) | Microsoft Docs"
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
  - "compile"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Compile 方法"
  - "编译源代码, 正则表达式"
  - "正则表达式, 编译"
ms.assetid: dc28cae3-478d-49b5-b5ea-203e5edfe195
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# compile 方法（正则表达式）(JavaScript)
将正则表达式编译为内部格式，从而更快地执行。  
  
## 语法  
  
```  
  
rgExp.compile(pattern, [flags])   
```  
  
## 参数  
 `rgExp`  
 必需。  **Regular Expression** 对象的一个实例。  可以是变量名或文本。  
  
 *pattern*  
 必需。  一个字符串表达式，包含要编译的正则表达式模式  
  
 `flags`  
 可选。  可以组合使用的可用标志有：  
  
-   g（全局搜索出现的所有*模式*）  
  
-   i（忽略大小写）  
  
-   m（多行搜索）  
  
## 备注  
 **compile** 方法将 *pattern* 转换为内部的格式，从而执行得更快。  例如，这允许在循环中更有效地使用正则表达式。  当重复使用相同的表达式时，编译过的正则表达式使执行加速。  然而，如果正则表达式发生更改，则这种编译毫无益处。  
  
## 示例  
 下面的示例阐释了 **compile** 方法的用法：  
  
```javascript  
function CompileDemo(){  
   var rs;  
   var s = "AaBbCcDdEeFfGgHhIiJjKkLlMmNnOoPp"  
   // Create regular expression for uppercase only.  
   var r = new RegExp("[A-Z]", "g");  
   var a1 = s.match(r)              // Find matches.  
   // Compile the regular expression for lowercase only.  
   r.compile("[a-z]", "g");  
// Find matches.  
   var a2 = s.match(r)                
   return(a1 + "\n" + a2);  
}  
```  
  
## 要求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **适用于**：[正则表达式对象](../../javascript/reference/regular-expression-object-javascript.md)  
  
## 请参阅  
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/zh-cn/ab0766e1-7037-45ed-aa23-706f58358c0e)