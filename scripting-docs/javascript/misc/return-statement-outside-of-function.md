---
title: "“return”语句在函数之外 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.WebClient.Help.SCRIPT1018"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 03568f9f-5f4f-4a10-a738-9a73f3832b9e
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# “return”语句在函数之外
在代码的全局范围内使用 `return` 语句。  `return` 语句应仅在函数体内出现。  
  
 调用 `()` 运算符为其表达式的函数。  所有表达式都具有值；`return` 语句用于指定函数返回的值。  常规格式为：  
  
```  
  
return [ expression ];  
```  
  
 当执行 `return` 语句时，*expression* 将计算并作为函数的值返回。  如果没有表达式，则返回 **undefined**。  
  
 当执行 `return` 语句时，即使函数体中仍然还有其他语句，此函数也会停止执行。  此规则的例外情况是：如果 **return** 语句出现在 **try** 块内而且有一个相应的 **finally** 块，则 **finally** 块中的代码将在此函数返回之前执行。  
  
 如果函数因其到达函数体的末尾而未执行 `return` 语句而返回，则返回的值为 **undefined** 值（这意味着函数结果不能用作大型表达式的一部分）。  
  
### 更正此错误  
  
-   从代码的主体（全局范围）中移除 `return` 语句。  
  
## 请参阅  
 [return 语句](../../javascript/reference/return-statement-javascript.md)   
 [Function 对象](../../javascript/reference/function-object-javascript.md)   
 [caller 属性（函数）](../../javascript/reference/caller-property-function-javascript.md)