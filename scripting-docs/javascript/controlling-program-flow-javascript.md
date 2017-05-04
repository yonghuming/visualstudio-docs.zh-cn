---
title: "控制程序流 (JavaScript) | Microsoft Docs"
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
  - "布尔值，程序流"
  - "continue 语句"
  - "break 语句"
  - "控制流，关于控制流"
ms.assetid: 4ef58c82-e5d6-4b09-9458-cf0aa3b39bf5
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# 控制程序流 (JavaScript)
通常，[!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 脚本中的语句将按写入顺序逐个执行。  这称为“顺序执行”，它是程序流程的默认方向。  
  
 顺序执行的一种替代方法是将程序流传输到脚本的另一个部分。  即，不是按顺序执行下一条语句，而是执行另一条语句。  
  
 若要使脚本有用，必须按逻辑方式执行此控制转移。  程序控制的转移是基于判定进行的，判定的结果是一个真实性语句（返回布尔值 **true** 或 **false**）。  创建一个表达式，然后测试其结果是否为 true。  可通过两种主要的程序结构来实现此目的。  
  
 第一种是选择结构。  可以使用该结构通过在程序中创建一个交叉点（类似道路的分岔）来指定程序流的可能方向。  [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 中有四种选择结构。  
  
-   单选结构 \(**if**\)  
  
-   双选结构 \(**if\/else**\)  
  
-   内联三元运算符 `?:`  
  
-   多选结构 \(`switch`\)  
  
 第二种程序控制结构是重复结构。  可以使用该结构来指定要在满足某个条件时重复的操作。  当满足控制语句的条件时（通常，经过特定次数的迭代后），控制转到重复结构之外的下一条语句。  [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 中有四种重复结构。  
  
-   在循环顶部测试表达式 \(`while`\)  
  
-   在循环底部测试表达式 \(**do\/while**\)  
  
-   操作对象的每个属性 \(**for\/in**\)  
  
-   由计数器控制的重复 \(**for**\)  
  
 可以通过嵌套和堆叠选择控制结构以及重复控制结构来创建相当复杂的脚本。  
  
 第三种形式的结构化程序流由异常处理提供，本文档中未对其进行讨论。  
  
## 使用条件语句  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 支持 **if** 和 [if...else](../javascript/reference/if-dot-dot-dot-else-statement-javascript.md) 条件语句。  在 **if** 语句中测试条件，如果该条件满足测试，则执行相关 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 代码。  在 `if...else` 语句中，如果该条件未通过测试，则执行其他代码。  最简单的 **if** 语句形式可以写在一行内，但是通常使用多行 **if** 和 `if...else` 语句。  
  
 以下示例阐释了 **if** 和 `if...else` 语句可以使用的语法。  第一个示例显示最简单一种的布尔测试。  当（且仅当）圆括号内的项计算结果为（或可以强制为）**true** 时，执行 **if** 后面的语句或语句块。  
  
```javascript  
function GetReaction(newShip, color, texture, dayOfWeek)  
{  
   // The test succeeds if the newShip Boolean value is true.  
   if (newShip)  
   {  
      return "Champagne Bottle";  
   }  
  
   // The test succeeds if both conditions are true.  
   if (color == "deep yellow" && texture == "large and small wrinkles")  
   {  
      return "Is it a crenshaw melon?";  
   }  
  
   // The test succeeds if either condition is true.  
   if ((dayOfWeek == "Saturday") || (dayOfWeek == "Sunday"))  
   {  
      return "I'm off to the beach!";  
   }  
   else  
   {  
      return "I'm going to work.";  
   }  
}  
  
var reaction = GetReaction(false, "deep yellow", "smooth", "Sunday");  
document.write(reaction);  
  
// Output: I'm off to the beach!  
```  
  
## 条件运算符  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 还支持隐式条件格式。  它在要测试的条件后使用问号（而不是在条件前的字 **if**）。  它还指定两个替代项，一个在满足条件时使用，一个在不满足条件时使用。  这些替代项必须用冒号分隔开。  
  
```javascript  
var AMorPM = (theHour >= 12) ? "PM" : "AM";  
```  
  
 如果要将几个条件放在一起测试，并且知道其中一个条件比其他条件更可能会通过或失败，则可以使用一种称为“短路计算”的功能加快脚本的执行速度。  当 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 计算逻辑表达式时，它只计算为得出结果而必须计算的子表达式。  
  
 例如，如果有一个 AND 表达式为（\(x \=\= 123\) && \(y \=\= 6\)），则 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 将先检查 x 是否为 123。  如果不是，则整个表达式不能为 true，即使 y 等于 6 也是如此。  因此，绝不会对 y 进行测试，而且 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 返回值 **false**。  
  
 同样，如果仅多个条件中的一个条件必须为 **true**（使用 &#124;&#124; 运算符），则在任一条件通过测试后，测试就会停止。  如果要测试的条件涉及执行函数调用或其他复杂表达式，则这会很有效。  出于这种考虑，在编写 Or 表达式时，应先放置最有可能为 **true** 的条件。  在编写 And 表达式时，应先放置最有可能为 **false** 的条件。  
  
 采用这种方式设计脚本的优点是，如果 **runfirst\(\)** 返回 0，以下示例中将不会执行 **runsecond\(\)**。  
  
```javascript  
if ((runfirst() == 0) || (runsecond() == 0)) {  
    // some code  
}  
```  
  
## 使用循环  
 可通过多种方式来重复执行语句或语句块。  一般，重复执行称为“*循环*”或“*迭代*”。  迭代就是循环的单次执行。  通常，它是由变量测试控制的，每次执行循环时，它的值都会发生变化。  [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 支持四种类型的循环：[for](../javascript/reference/for-statement-javascript.md) 循环、[for...in](../javascript/reference/for-dot-dot-dot-in-statement-javascript.md) 循环、[while](../javascript/reference/while-statement-javascript.md) 循环、[do...while](../javascript/reference/do-dot-dot-dot-while-statement-javascript.md) 循环。  
  
## 用于循环  
 **for** 语句指定一个计数器变量、一个测试条件以及一个更新计数器的操作。  在每次循环迭代之前，先测试条件。  如果测试成功，则执行循环内的代码。  如果测试失败，则不执行循环内的代码，程序继续执行紧靠循环后面的第一行代码。  在循环执行后和下一次迭代开始之前，先更新计数器变量。  
  
 如果循环条件始终不满足，则不执行该循环。  如果始终满足测试条件，则产生无限循环。  在某些情况下，可能希望出现前一种情况，但几乎从不希望出现后一种情况，因此编写循环条件时一定要谨慎。  
  
```javascript  
// The update expression ("icount++" in the following examples)  
// is executed at the end of the loop, after the block of  
// statements that forms the body of the loop is executed, and  
// before the condition is tested.  
  
// Set a limit of 10 on the loop.  
var howFar = 10;  
  
// Create an array called sum with 10 members, 0 through 9.  
var sum = new Array(howFar);  
sum[0] = 0;  
  
// Iterate from 0 through 9.  
var theSum = 0;  
for(var icount = 0; icount < howFar; icount++)  
{  
   theSum += icount;  
   sum[icount] = theSum;  
}  
  
// This code is not executed at all, because icount is not greater than howFar.  
var newSum = 0;  
for(var icount = 0; icount > howFar; icount++)  
{  
   newSum += icount;  
}  
  
// This is an infinite loop.  
var sum = 0;  
for(var icount = 0; icount >= 0; icount++)  
{  
   sum += icount;  
}  
```  
  
## 使用 for...in 循环  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 提供一种特殊的循环，用于单步执行[对象](../javascript/objects-and-arrays-javascript.md)的所有用户定义的属性或数组的所有元素。  `for...in` 循环中的循环计数器为字符串，而非数字。  它包含当前属性的名称或当前数组元素的索引。  
  
```javascript  
// Create an object with some properties  
var myObject = new Object();  
myObject.name = "James";  
myObject.age = "22";  
myObject.phone = "555 1234";  
  
// Enumerate (loop through)_all the properties in the object  
for (var prop in myObject)  
{  
    // This displays "The property 'name' is James", etc.  
    document.write("The property '" + prop + "' is " + myObject[prop]);  
    // New line.  
    document.write("<br />");    
}  
```  
  
 虽然 `for...in` 循环看起来类似于 VBScript 的 `For Each...Next` 循环，但二者的工作方式不同。  [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] **for...in loop** 将循环访问 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 对象的属性。  VBScript **For Each...Next** 循环将循环访问集合中的项。  若要循环 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 中的集合，需使用 [Enumerator 对象](../javascript/reference/enumerator-object-javascript.md) 对象或集合对象的 `forEach` 方法（如果存在）。  虽然某些对象（如 Internet Explorer 中的对象）同时支持 VBScript **For Each...Next** 循环和 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] **for...in** 循环，但大多数对象都无法实现这一点。  
  
## 使用 while 循环  
 `while` 循环类似于 **for** 循环。  差异在于，`while` 循环没有内置计数器变量或更新表达式。  若要控制语句或语句块的重复执行，但需要更复杂的规则而不是仅“运行此代码 n 次”，请使用 `while` 循环。  以下示例使用 Internet Explorer 对象模型和 `while` 循环来向用户询问简单的问题。  
  
```javascript  
var x = 0;  
while ((x != 5) && (x != null))  
{  
    x = window.prompt("What is my favorite number?", x);  
}  
  
if (x == null)  
    window.alert("You gave up!");  
else  
    window.alert("Correct answer!");  
```  
  
> [!NOTE]
>  因为 `while` 循环没有显式的内置计数器变量，所以此循环比其他类型的循环更容易出现无限循环。  再者，因为有时很难发现循环条件是在何时或何处更新的，所以如果使用不慎，编写的 `while` 循环可能从不更新其条件。  因此，设计 `while` 循环时要十分谨慎。  
  
 如上所述，[!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 中还有一个类似于 while 循环的 **do...while** 循环，但此循环能够保证始终至少执行一次，因为将在循环结束而非开始时测试条件。  例如，可以将上面的循环重写为：  
  
```javascript  
var x = 0;  
do  
{  
    x = window.prompt("What is my favorite number?", x);  
} while ((x != 5) && (x != null));  
  
if (x == null)  
    window.alert("You gave up!");  
else  
    window.alert("Correct answer!");  
```  
  
## 使用 break 和 continue 语句  
 如果满足某个条件，则 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 中的 [break](../javascript/reference/break-statement-javascript.md) 语句用于停止执行循环。（请注意，**break** 也用于退出 `switch` 块）。  如果循环是 [for](../javascript/reference/continue-statement-javascript.md) 或 `for...in` 循环，可以使用 **continue** 语句直接跳到下一个迭代，跳过代码块的其余部分，同时更新计数器变量。  
  
 以下示例基于上一示例，使用 **break** 和 **continue** 语句来控制循环。  
  
```javascript  
var x = 0;  
do  
{  
    x = window.prompt("What is my favorite number?", x);  
  
    // Did the user cancel? If so, break out of the loop  
    if (x == null)  
        break;  
  
    // Did they enter a number?  
    // If so, no need to ask them to enter a number.  
    if (Number(x) == x)  
        continue;  
  
    // Ask user to only enter in numbers  
    window.alert("Please only enter in numbers!");  
  
} while (x != 5)  
  
if (x != 5)  
    window.alert("You gave up!");  
else  
    window.alert("Correct answer!");  
```