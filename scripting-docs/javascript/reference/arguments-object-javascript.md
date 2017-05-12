---
title: "arguments 对象 (JavaScript) | Microsoft Docs"
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
  - "arguments"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "arguments 对象"
  - "参数, arguments 对象"
ms.assetid: 5eb79ca9-bbb8-4a42-aaf5-16a93ecb425f
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# arguments 对象 (JavaScript)
一个表示当前所执行的函数的参数和调用它的函数的对象。  
  
## 语法  
  
```  
[function.]arguments[n]  
```  
  
## 参数  
 *Function — 函数*  
 可选。  当前正在执行的 `Function` 对象的名称。  
  
 *n*  
 必需。  传递给 `Function` 对象的参数值的从零开始的索引。  
  
## 备注  
 无法显式创建**参数**对象。  **参数**对象仅在开始执行函数时可用。  函数的**参数**对象不是数组，但访问各个参数的方式与访问数组元素的方式相同。  索引 *n* 实际上是对**参数**对象的某个 **0** ***n*** 属性的引用。  
  
## 示例  
 下面的示例阐释 arguments 对象的用法：  
  
```javascript  
function ArgTest(a, b)  
{  
   var s = "";  
  
   s += "Expected Arguments: " + ArgTest.length;  
   s += "<br />";  
   s += "Passed Arguments: " + arguments.length;  
   s += "<br />";  
  
   s += "The individual arguments are: "  
   for (n = 0; n < arguments.length; n++)  
   {  
      s += ArgTest.arguments[n];  
      s += " ";  
   }  
  
   document.write(s);  
}  
  
ArgTest(1, 2, "hello", new Date())  
  
// Output:  
// Expected Arguments: 2  
// Passed Arguments: 4  
// The individual arguments are: 1 2 hello Tues Jan 8 08:27:09 PST 20xx  
  
```  
  
## 要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 请参阅  
 [0...n 属性（参数）](../../javascript/reference/0-dot-dot-dot-n-properties-arguments-javascript.md)   
 [callee 属性（参数）](../../javascript/reference/callee-property-arguments-javascript.md)   
 [length 属性（参数）](../../javascript/reference/length-property-arguments-javascript.md)