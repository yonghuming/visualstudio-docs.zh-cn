---
title: "0...n 属性（参数）(JavaScript) | Microsoft Docs"
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
  - "0...n"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "0 至 n 属性"
ms.assetid: 52857c4b-3d56-4500-93ff-4db4729c2578
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# 0...n 属性（参数）(JavaScript)
返回 **arguments** 对象中的各个参数的实际值，该值是由一个正在执行的函数的 **arguments** 属性返回的。  
  
## 语法  
  
```  
[function.]arguments[[0|1|2|...|n]]  
```  
  
## 参数  
 *function*  
 可选。  当前正在执行的 `Function` 对象的名称。  
  
 0, 1, 2, *, n*  
 必需。  在 0 到 *n* 范围内的非负整数，其中 0 表示第一个参数，*n* 表示最后一个参数。  最后一个参数 *n* 的值为 **arguments.length\-1**。  
  
## 备注  
 由 0 .  .  .  n 属性返回的值就是传递给正在执行的函数的实际值。  虽然实际上不是参数数组，但访问组成 **arguments** 对象的各个元素的方法与访问数组元素的方法相同。  
  
## 示例  
 下面的示例阐释了 **arguments** 对象的 **0 ...** ***n*** 属性的用法。  若要完全理解该示例，请向函数传递一个或多个参数：  
  
```javascript  
function ArgTest(){  
   var s = "";  
   s += "The individual arguments are: "  
   for (n = 0; n < arguments.length; n++){  
      s += ArgTest.arguments[n];  
      s += " ";  
   }  
   return(s);  
}  
document.write(ArgTest(1, 2, "hello", new Date()));  
```  
  
## 要求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **适用于**：[arguments 对象](../../javascript/reference/arguments-object-javascript.md)&#124; [Function 对象](../../javascript/reference/function-object-javascript.md)  
  
## 请参阅  
 [length 属性（参数）](../../javascript/reference/length-property-arguments-javascript.md)   
 [length 属性（函数）](../../javascript/reference/length-property-function-javascript.md)