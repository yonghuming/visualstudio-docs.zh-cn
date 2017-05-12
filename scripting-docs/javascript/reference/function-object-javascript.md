---
title: "Function 对象 (JavaScript) | Microsoft Docs"
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
  - "function"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Function 对象"
ms.assetid: d3834767-203c-475e-848c-95c423ba15b6
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Function 对象 (JavaScript)
创建新函数。  
  
## 语法  
  
```  
function functionName([argname1  [, ...[, argnameN]]])  
{  
   body  
}  
```  
  
## 语法  
  
```  
  
functionName = new Function( [argname1,  [... argnameN,]] body );  
```  
  
## 参数  
 `functionName`  
 必需。  新创建的函数的名称。  
  
 `argname1...argnameN`  
 可选。  该函数接受的参数的列表。  
  
 `body`  
 可选。  包含在调用函数时要执行的 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 代码块的字符串。  
  
## 备注  
 该函数是 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 中的基本数据类型。  语法 1 创建了一个函数值，[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 可在需要时将其转换为 `Function` 对象。  在调用该函数时，[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 会将根据语法 2 创建的 `Function` 对象转换为函数值。  
  
 语法 1 是在 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 中创建新函数的标准方式。  语法 2 是用于显式创建函数对象的替代形式。  
  
 例如，若要声明一个可将两个传递给它的参数相加的函数，可通过以下两种方法之一实现此目的：  
  
## 示例 1  
  
```javascript  
function add(x, y)  
{  
   return(x + y);  
}  
```  
  
## 示例 2  
  
```  
var add = function(x, y) {  
     return(x+y);  
}  
```  
  
 在任一示例中，您使用类似于以下内容的代码行调用该函数：  
  
```javascript  
add(2, 3);  
```  
  
> [!NOTE]
>  在调用函数时，请确保始终包括圆括号和任何必选参数。  调用不带括号的函数会导致返回函数本身，而不是函数的返回值。  
  
## 属性  
 [0...  
          n 属性](../../javascript/reference/0-dot-dot-dot-n-properties-arguments-javascript.md) &#124;[arguments 属性](../../javascript/reference/arguments-property-function-javascript.md) &#124; [callee 属性](../../javascript/reference/callee-property-arguments-javascript.md) &#124; [caller 属性](../../javascript/reference/caller-property-function-javascript.md) &#124; [constructor 属性](../../javascript/reference/constructor-property-object-javascript.md) &#124; [length 属性（函数）](../../javascript/reference/length-property-function-javascript.md) &#124; [prototype 属性](../../javascript/reference/prototype-property-object-javascript.md)  
  
## 方法  
 [apply 方法](../../javascript/reference/apply-method-function-javascript.md) &#124; [bind 方法](../../javascript/reference/bind-method-function-javascript.md) &#124; [call 方法](../../javascript/reference/call-method-function-javascript.md) &#124; [toString 方法](../../javascript/reference/tostring-method-object-javascript.md) &#124; [valueOf 方法](../../javascript/reference/valueof-method-object-javascript.md)  
  
## 要求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## 请参阅  
 [function 语句](../../javascript/reference/function-statement-javascript.md)   
 [new 运算符](../../javascript/reference/new-operator-decrementjavascript.md)   
 [var 语句](../../javascript/reference/var-statement-javascript.md)