---
title: "length 属性 (arguments) (JavaScript) | Microsoft Docs"
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
  - "length Property"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Length 属性"
  - "length 属性（参数）"
ms.assetid: 3cf36823-15bc-489b-a951-24c4923d9dba
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# length 属性 (arguments) (JavaScript)
返回由调用者传递给某个函数的参数的实际数目。  
  
## 语法  
  
```  
[function.]arguments.length  
```  
  
## 备注  
 可选 *function* 参数是当前执行的 `Function` 对象的名称。  
  
 **arguments** 对象的 **length** 属性由脚本引擎初始化为该函数中开始执行时，传递给 `Function` 对象的参数的实际数目。  
  
## 示例  
 下面的示例阐释了 **arguments** 对象的 **length** 属性的用法。  若要完全理解此示例，请将 2 个（预计数目）以上的参数传递给该函数：  
  
```javascript  
function ArgTest(a, b){  
   var s = "";  
  
   s += "Expected Arguments: " + ArgTest.length;  
   s += "<br />";  
   s += "Passed Arguments: " + arguments.length;  
  
   document.write (s);  
}  
```  
  
## 要求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **适用于**：[arguments 对象](../../javascript/reference/arguments-object-javascript.md)&#124; [Function 对象](../../javascript/reference/function-object-javascript.md)  
  
## 请参阅  
 [arguments 属性（函数）](../../javascript/reference/arguments-property-function-javascript.md)   
 [length 属性（数组）](../../javascript/reference/length-property-array-javascript.md)   
 [length 属性（字符串）](../../javascript/reference/length-property-string-javascript.md)