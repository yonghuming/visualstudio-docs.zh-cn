---
title: "arguments 属性（函数）(JavaScript) | Microsoft Docs"
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
  - "arguments，arguments 属性"
  - "Arguments 属性"
ms.assetid: efc7a1ee-0880-4f05-b0f2-808f31a4af1d
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# arguments 属性（函数）(JavaScript)
获取当前正在执行的 `Function` 对象的参数。  
  
## 语法  
  
```  
  
function.arguments  
```  
  
## 备注  
 `function` 参数是当前正在执行的函数的名称，且可以省略。  
  
 此属性使函数可以处理可变数量的参数。  `arguments` 对象的 **length** 属性包含了传递给函数的参数数目。  `arguments` 对象中包含的各个参数的访问方式与数组元素的访问方式相同。  
  
## 示例  
 下面的示例阐释了 `arguments` 属性的用法：  
  
```javascript  
function ArgTest(arg1, arg2){  
   var s = "";  
   s += "The individual arguments are: "  
   for (n = 0; n < arguments.length; n++){  
      s += ArgTest.arguments[n];  
      s += " ";  
   }  
   return(s);  
}  
document.write(ArgTest(1, 2, "hello"));  
  
//Output: function ArgTest(arg1, arg2){  
   var s = "";  
   s += "The individual arguments are: "  
   for (n = 0; n < arguments.length; n++){  
      s += ArgTest.arguments[n];  
      s += " ";  
   }  
   return(s);  
}  
document.write(ArgTest(1, 2, "hello"));  
  
// Output: The individual arguments are: 1 2 hello  
```  
  
## 要求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## 请参阅  
 [arguments 对象](../../javascript/reference/arguments-object-javascript.md)   
 [function 语句](../../javascript/reference/function-statement-javascript.md)