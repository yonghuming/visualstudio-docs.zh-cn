---
title: "变量 (JavaScript) | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- coercion
- case sensitivity, JavaScript variable name
ms.assetid: 12a450e5-4818-4a09-9878-cd7c6cd2a248
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: f30946899ad35286dfb1e786cf903d58f5c98cb6
ms.contentlocale: zh-cn
ms.lasthandoff: 08/11/2017

---
# <a name="variables-javascript"></a>变量 (JavaScript)
在 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 中，变量包含一个值，如“hello”或 5。 使用变量时，会引用其所代表的数据，例如 `NumberOfDaysLeft = EndDate - TodaysDate`。  
  
 可以使用变量来存储、检索和操作代码中显示的值。 尝试为变量赋予有意义的名称，方便其他人理解代码的功能。  
  
## <a name="declaring-variables"></a>声明变量  
 变量首次在脚本中出现就是对其进行声明。 首次涉及变量时会在内存中对其进行设置，以便稍后在脚本中引用它。 使用变量之前应先声明它们。 可使用 `var` 关键字进行声明。  
  
```JavaScript  
// A single declaration.  
var count;    
// Multiple declarations with a single var keyword.  
var count, amount, level;      
// Variable declaration and initialization in one statement.  
var count = 0, amount = 100;   
```  
  
 如果不在 `var` 语句中初始化变量，它将自动应用值 `undefined`。  
  
## <a name="naming-variables"></a>命名变量  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 是区分大小写的语言。 这表示诸如 myCounter 的变量名称与变量名称 MYCounter 不同。 变量名称可以是任何长度。 创建合法变量名称的规则如下所示：  
  
-   第一个字符必须是 ASCII 字母（大写或小写），或下划线 (_) 字符。 请注意，不能将数字用作第一个字符。  
  
-   后续字符必须是字母、数字或下划线 (_)。  
  
-   变量名不能是[保留字](../javascript/reference/javascript-reserved-words.md)。  
  
 以下是有效变量名称的一些示例：  
  
```  
_pagecount   
Part9   
Number_Items   
```  
  
 以下是无效变量名称的一些示例：  
  
```JavaScript  
// Cannot begin with a number.   
99Balloons     
// The ampersand (&) character is not a valid character for variable names.   
Alpha&Beta   
```  
  
 在想声明一个变量并初始化它，但是不想赋予它任何特定值时，可为其赋值 `null`。 这是一个示例。  
  
```JavaScript  
var bestAge = null;  
var muchTooOld = 3 * bestAge; // muchTooOld has the value 0.  
```  
  
 如果声明一个变量而不给它赋值，则它的值为 `undefined`。 这是一个示例。  
  
```JavaScript  
var currentCount;  
// finalCount has the value NaN because currentCount is undefined.  
var finalCount = 1 * currentCount;   
```  
  
 `null` 值的行为类似于数字 0，而 `undefined` 的行为类似于特殊值 `NaN`（不是数字）。 如果比较 `null` 值和 `undefined` 值，则会发现它们是相等的。  
  
 可以在声明中不使用 `var` 关键字声明一个变量，并为其赋值。 这是一个隐式声明。  
  
```JavaScript  
// The variable noStringAtAll is declared implicitly.  
noStringAtAll = "";   
```  
  
 无法使用从未声明过的变量。  
  
```JavaScript  
// Error. Length and width do not yet exist.  
var area = length * width;   
```  
  
## <a name="coercion"></a>强制转换  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 是一种松散类型的语言，而不是类似于 C++ 这样的强类型语言。 这意味着 JavaScript 变量不具有任何预先确定的类型。 相反，变量类型是其值的类型。 此行为允许用户将值视为不同类型的值。  
  
 在 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 中，可以在不引发异常的情况下对不同类型的值执行操作。 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 解释器将其中一个数据类型隐式转换或强制转换为另一种数据类型，然后执行该操作。 字符串、数字和布尔值的强制转换规则如下所示：  
  
-   如果添加一个数字和一个字符串，则会将数字强制转换为字符串。  
  
-   如果添加一个布尔值和一个字符串，则会将布尔值强制转换为字符串。  
  
-   如果添加一个数字和一个布尔值，则会将布尔值强制转换为数字。  
  
 在下面的示例中，添加到字符串的数字会转换为字符串。  
  
```JavaScript  
var x = 2000;  
var y = "Hello";  
// The number is coerced to a string.  
x = x + y;  
document.write(x);   
  
// Output:  
// 2000Hello  
```  
  
 字符串将自动转换为等效数字以便进行比较。 若要显式地将字符串转换为整数，则使用 [parseInt 函数](../javascript/reference/parseint-function-javascript.md)。 若要显式地将字符串转换为数字，则使用 [parseFloat 函数](../javascript/reference/parsefloat-function-javascript.md)。
