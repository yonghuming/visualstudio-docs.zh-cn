---
title: "变量 (JavaScript) | Microsoft Docs"
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
  - "区分大小写, JavaScript 变量名"
  - "强迫"
ms.assetid: 12a450e5-4818-4a09-9878-cd7c6cd2a248
caps.latest.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 20
---
# 变量 (JavaScript)
在 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 中，变量包含一个值，如“hello”或 5。  在使用该变量时，您会引用该变量表示的数据，例如 `NumberOfDaysLeft = EndDate – TodaysDate`。  
  
 您使用变量存储、检索和操作代码中出现的值。  尝试为您的变量提供有意义的名称以便其他人轻松了解您的代码的行为。  
  
## 声明变量  
 变量在脚本中的首次亮相是在其声明中。  在变量首次出现时将会在内存中设置它，因此您稍后可在脚本中引用它。  应在使用变量之前先声明变量。  可以使用 `var` 关键字实现此目的。  
  
```javascript  
// A single declaration.  
var count;    
// Multiple declarations with a single var keyword.  
var count, amount, level;      
// Variable declaration and initialization in one statement.  
var count = 0, amount = 100;   
```  
  
 如果未在 `var` 语句中初始化您的变量，它将自动采用 `undefined` 值。  
  
## 命名变量  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 是一种区分大小写的语言。  这意味着，变量名 myCounter 与变量名 MYCounter 不同。  变量名可以是任意长度。  创建合法变量名的规则如下：  
  
-   第一个字符必须是 ASCII 字母（大写或小写）或下划线 \(\_\) 字符。  注意，数字不能用作第一个字符。  
  
-   随后的字符必须是字母、数字或下划线 \(\_\)。  
  
-   变量名不得为[保留字](../javascript/reference/javascript-reserved-words.md)。  
  
 下面是有效变量名的一些示例：  
  
```  
_pagecount   
Part9   
Number_Items   
```  
  
 下面是无效变量名的一些示例：  
  
```javascript  
// Cannot begin with a number.   
99Balloons     
// The ampersand (&) character is not a valid character for variable names.   
Alpha&Beta   
```  
  
 当您需要声明并初始化变量，但不需要为变量指定任何特定值时，请为变量分配 `null` 值。  这是一个示例。  
  
```javascript  
var bestAge = null;  
var muchTooOld = 3 * bestAge; // muchTooOld has the value 0.  
```  
  
 如果声明一个变量而不为其赋值，则该变量具有 `undefined` 值。  这是一个示例。  
  
```javascript  
var currentCount;  
// finalCount has the value NaN because currentCount is undefined.  
var finalCount = 1 * currentCount;   
```  
  
 `null` 值的行为与数字 0 类似，而 `undefined` 的行为与特定值 `NaN`（非数字）类似。  如果您比较一个 `null` 值和一个 `undefined` 值，则它们将相等。  
  
 可以在不使用 `var` 关键字的情况下在声明中声明一个变量，并为该变量分配一个值。  这是一个隐式声明。  
  
```javascript  
// The variable noStringAtAll is declared implicitly.  
noStringAtAll = "";   
```  
  
 不能使用从未声明过的变量。  
  
```javascript  
// Error. Length and width do not yet exist.  
var area = length * width;   
```  
  
## 强制转换  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 是松散类型化语言，与强类型语言（如 C\+\+）相反。  这意味着，JavaScript 变量没有预先确定的类型。  相反，变量的类型是其值的类型。  此行为允许您将值当作另外一种类型进行处理。  
  
 在 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 中，可以对不同类型的值执行运算，而不会导致异常。  [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 解释器会将某个数据类型隐式转换或*强制转换* 为其他数据类型，然后执行操作。  以下是适用于字符串、数字和布尔值的强制转换规则：  
  
-   如果添加一个数字和字符串，则该数字会强制转换为字符串。  
  
-   如果添加一个布尔值和字符串，则该布尔值会强制转换为字符串。  
  
-   如果添加一个数字和布尔值，则该布尔值会强制转换为数字。  
  
 在下面的示例中，会将数字添加到字符串中生成的字符串。  
  
```javascript  
var x = 2000;  
var y = "Hello";  
// The number is coerced to a string.  
x = x + y;  
document.write(x);   
  
// Output:  
// 2000Hello  
```  
  
 为了进行比较，字符串将自动转换为等效数字。  若要将字符串显式转换为整数，可以使用 [parseInt 函数](../javascript/reference/parseint-function-javascript.md)。  若要将字符串显式转换为数字，可以使用 [parseFloat 函数](../javascript/reference/parsefloat-function-javascript.md)。