---
title: "callee 属性（参数）(JavaScript) | Microsoft Docs"
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
  - "callee"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "callee 属性"
ms.assetid: ad9d4d21-73f0-44f6-8bec-502f3456cd23
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# callee 属性（参数）(JavaScript)
返回正被执行的 `Function` 对象，即指定的 `Function` 对象的正文。  
  
## 语法  
  
```  
[function.]arguments.callee  
```  
  
## 备注  
 可选 *function* 参数是当前执行的 `Function` 对象的名称。  
  
 `callee` 属性是 **arguments** 对象的一个成员，该属性仅当相关函数正在执行时才可用。  
  
 `callee` 属性的初始值是正被执行的 `Function` 对象。  这将允许匿名函数成为递归的。  
  
## 示例  
  
```javascript  
function factorial(n){  
  if (n <= 0)  
     return 1;  
  else  
     return n * arguments.callee(n - 1)  
}  
document.write(factorial(4));  
```  
  
## 要求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **适用于**：[arguments 对象](../../javascript/reference/arguments-object-javascript.md)&#124; [Function 对象](../../javascript/reference/function-object-javascript.md)  
  
## 请参阅  
 [caller 属性（函数）](../../javascript/reference/caller-property-function-javascript.md)