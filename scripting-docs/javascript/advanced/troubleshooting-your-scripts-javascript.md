---
title: "脚本疑难解答 (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "自动类型转换"
  - "脚本疑难解答"
ms.assetid: 0e0545d9-44e5-4179-befc-99a882c5c672
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# 脚本疑难解答 (JavaScript)
任何编程语言都具有惊人之处。  例如，[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 中的 `null` 值与 C 或 C\+\+ 语言中的 `Null` 值的行为不同。  
  
 以下是您编写 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 脚本时可能遇到的一些存在麻烦的方面。  
  
## 语法错误  
 在编写脚本时注意细节很重要。  例如，字符串必须在引号内。  
  
## 脚本解释的顺序  
 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 解释是 Web 浏览器的 HTML 分析过程的一部分。  如果在文档中将脚本置于 \<HEAD\> 标记内，则会先解释该脚本，然后再解释 \<BODY\> 标记的任何部分。  如果具有在 \<BODY\> 标记中创建的对象，则这些对象在分析 \<HEAD\> 时不存在，并且脚本不能对这些对象进行操作。  
  
> [!NOTE]
>  此行为是 Internet Explorer 所特有的。  ASP 和 WSH 具有不同的执行模型（像其他主机一样）。  
  
## 自动类型强制  
 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 是带有自动强制功能的松散类型化语言。  尽管具有不同类型的值不全等，下面的示例中的表达式的计算结果也为 **true**。  
  
```javascript  
"100" == 100;  
false == 0;  
```  
  
 若要检查类型和值是否均相同，请使用全等运算符 \(\=\=\=\)。  以下两个表达式的计算结果均为 false：  
  
```javascript  
"100" === 100;  
false === 0;  
```  
  
## 运算符优先级  
 [运算符优先级](../../javascript/operator-subtractprecedence-javascript.md)确定在计算表达式的过程中执行操作的时间。  在下面的示例中，即使表达式中首先出现减法运算符，也会先计算乘法，再计算减法。  
  
```javascript  
theRadius = aPerimeterPoint - theCenterpoint * theCorrectionFactor;  
```  
  
## 将 for...in 循环用于对象  
 在使用 [for…in](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md) 循环访问对象的属性时，无法预测或控制将对象字段赋给循环计数器变量的顺序。  此外，在不同的语言实现中，顺序可能会有所不同。  
  
## with 关键字  
 虽然 [with](../../javascript/reference/with-statement-javascript.md) 语句为访问已存在于指定对象中的属性带来了方便，但无法用来向对象添加属性。  若要在对象中创建新的属性，必须明确地引用该对象。  
  
## this 关键字  
 虽然您在对象定义中使用 `this` 关键字来引用对象本身，但在当前执行的函数不是对象定义时，您无法使用 `this` 或类似的关键字来引用该函数。  如果将函数作为方法赋给对象，则可以在函数中使用 `this` 关键字来引用该对象。  
  
## 编写在 Internet Explorer 中编写脚本的脚本  
 当解释器遇到 \<\/SCRIPT\> 标记时，该标记将终止当前脚本。  若要显示“\<\/SCRIPT\>”本身，请将其重新书写为至少两个字符串（例如“\<\/SCR”和“IPT\>”），随后可以在写出这两个字符串的语句中将它们串联在一起。  
  
## Internet Explorer 中的隐式窗口引用  
 因为可以一次性打开多个窗口，所以任何隐式窗口引用均指向当前窗口。  对于其他窗口，则必须使用显式引用。