---
title: "编写 JavaScript 代码 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.htmldesigner.html"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "代码, JavaScript 语法"
  - "注释, JavaScript 代码"
  - "JavaScript 代码"
ms.assetid: dde28266-0d0f-4460-a819-f931cf0911ad
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# 编写 JavaScript 代码
与许多其他编程语言一样，[!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 按语句、由相关语句集构成的块和注释进行组织。  在一个语句内，可以使用变量、字符串、数字和表达式。  
  
## 语句  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 程序是语句的集合。  [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 语句通过某种方式组合表达式以执行完整任务。  
  
 一个语句由一个或多个表达式、关键字或运算符（符号）组成。  通常，在一个行上书写一个语句，但可在两个行或多个行上书写一个语句。  此外，在同一个行上书写两个或多个语句，用分号分隔。  通常，每个新行都开始一个新语句。  最好是显式终止您的语句。  可使用分号 \(;\) 做到这一点，分号是 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 语句的终止字符。  
  
 以下是 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 语句的两个示例。  字符 \/\/ 后面的语句是*注释*，它们是程序中的说明性备注。  
  
```javascript  
var aBird = "Robin"; // Assign the text "Robin" to the variable aBird.  
var today = new Date(); // Assign today's date to the variable today.  
```  
  
 由括号 \({}\) 包围的一组 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 语句称为一个*块*。  组织在一个块中的语句通常可以视为一个语句。  这就意味着可以在 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 要求使用单个语句的大多数地方使用块。  需要引起注意的例外情况包括 **for** 和 `while` 循环的头。  注意，块中的单个语句以分号结束，但块本身不是这样。  
  
 通常，块在函数和条件中使用。  注意，与 C\+\+ 和一些其他语言不同，[!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 并不将块视为一个新范围；只有函数创建新范围。  
  
 在下面的示例中，`else` 子句包含由大括号括起来的由两个语句构成的块。  该块被视为一个语句。  此外，该函数本身由用大括号括起来的语句块组成。  函数下方的语句位于块外部，因此不是函数定义的一部分。  
  
```javascript  
function inchestometers(inches)  
   {  
   if (inches < 0)  
      return -1;  
   else  
      {  
      var meters = inches / 39.37;  
      return meters;  
      }  
   }  
  
var inches = 12;  
var meters = inchestometers(inches);  
document.write("the value in meters is " + meters);  
```  
  
## 注释  
 单行 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 注释以两个正斜杠 \(\/\/\) 开始。  以下是单行注释的一个示例。  
  
```javascript  
var aGoodIdea = "Comment your code thoroughly."; // This is a single-line comment.  
```  
  
 多行 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 注释以正斜杠和星号 \(\/\*\) 开头，以相反的顺序 \(\*\/\) 结束。  
  
```javascript  
/*  
This is a multiline comment that explains the preceding code statement.  
  
The statement assigns a value to the aGoodIdea variable. The value,   
which is contained between the quote marks, is called a literal. A   
literal explicitly and directly contains information; it does not   
refer to the information indirectly. The quote marks are not part   
of the literal.  
*/  
```  
  
> [!NOTE]
>  如果尝试在一个多行注释中嵌入另一个多行注释，[!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 将以一种意想不到的方式解释生成的多行注释。  标记嵌入的多行注释结尾的 \*\/ 将被解释为整个多行注释的结尾。  这意味着，不会注释掉已嵌入的多行注释后面的文本；相反，它将被解释为 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 代码并将生成语法错误。  
  
 建议将所有注释编写为单行注释的块。  这样就允许随后用一个多行注释来注释大段代码。  
  
```javascript  
// This is another multiline comment, written as a series of single-line comments.  
// After the statement is executed, you can refer to the content of the   
// aGoodIdea variable by using its name.  
var extendedIdea = aGoodIdea + " You never know when you'll have to figure out what it does.";  
```  
  
## 赋值和等号  
 等号 \(\=\) 在 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 语句中用于为变量赋值：它是赋值运算符。  \= 运算符的左操作数始终为 Lvalue。  Lvalue 的示例包括：  
  
-   变量，  
  
-   数组元素，  
  
-   对象属性。  
  
 \= 运算符的右操作数始终为 Rvalue。  Rvalue 可以是任何类型的任意值，包括表达式的值。  下面是 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 赋值语句的一个示例。  
  
```javascript  
var anInteger = 3;  
```  
  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 编译器将该语句解释为：“将值 3 赋给变量 **anInteger**”，或“**anInteger** 采用值 3。”  
  
 一定要确保理解 \= 运算符（赋值）和 \=\= 运算符（相等）之间的差异。  当您希望比较两个值以确定二者是否相等时，请使用双等号 \(\=\=\)。  这将在[控制程序流](../javascript/controlling-program-flow-javascript.md)中详细讨论。  
  
## 表达式  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 表达式值可以是任何有效的 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 类型，即数字、字符串、对象等。  最简单的表达式是文本。  以下是 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 文本表达式的一些示例。  
  
```javascript  
3.9                       // numeric literal  
"Hello!"                  // string literal  
false                     // boolean literal  
null                      // literal null value  
{x:1, y:2}                // Object literal  
[1,2,3]                   // Array literal  
function(x){return x*x;}  // function literal  
```  
  
 更复杂的表达式可包含变量、函数调用和其他表达式。  可以使用运算符组合表达式来创建复杂的表达式。  运算符的示例包括：`+`（加法）、`-`（减法）、`*`（乘法）和 `/`（除法）。  
  
 以下是 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 复杂表达式的一些示例。  
  
```javascript  
var anExpression = 3 * (4 / 5) + 6;  
var aSecondExpression = Math.PI * radius * radius;  
var aThirdExpression = aSecondExpression + "%" + anExpression;  
var aFourthExpression = "(" + aSecondExpression + ") % (" + anExpression + ")";  
```