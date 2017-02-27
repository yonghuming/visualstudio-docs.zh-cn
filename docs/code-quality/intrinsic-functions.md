---
title: "内部函数 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_String_length_"
  - "_Param_"
  - "_Curr_"
  - "_Old_"
  - "_Nullterm_length_"
  - "_Inexpressible_"
ms.assetid: adf29f8c-89fd-4a5e-9804-35ac83e1c457
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 内部函数
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

在 SAL 的表达式可以是 C\/ C\+\+ 表达式，只要它是不具有副作用，例如，\+\+，\-\- ，和函数调用都在此上下文中的副作用。但是，SAL 提供可在 SAL 表达式的一些类似于函数的对象和数组保留的符号。  这些函数称为*“内部函数”*。  
  
## 通用  
 以下函数 instrinsic 注释对于 SAL 简要实用工具。  
  
|批注|说明|  
|--------|--------|  
|`_Curr_`|当批注对象的同义词。在 `_At_` 注释正在使用时，`_Curr_` 与 `_At_`的第一个参数相识。否则，它将是参数或在注释关联的整个函数\/返回值。|  
|`_Inexpressible_(expr)`|表示使用的注释表达式示例，为缓冲区的大小太复杂而无法表示的情形，则通过扫描输入数据集然后计数所选成员计算时。|  
|`_Nullterm_length_(param)`|`param` 元素的数量是缓冲区中等于但不包含 null 结束符。  它可能应用到非聚合，非 void 类型所有缓冲区。|  
|`_Old_(expr)`|当在前置条件时，都计算输入值 `_Old_` 返回 `expr`。如果在发送时计算条件，则返回 `expr` 值，因为在前置条件中进行计算。|  
|`_Param_(n)`|`n`为函数参数计数，从 1 到 `n`和 `n` 是整型常数。  如果参数命名，该注释与按名称访问参数相同。 **Note:**  `n` 可能是指由省略号定义的位置参数，也能在不使用名称的函数原型。|  
|`return`|C\/C\+\+ 保留关键字 `return` 可用在 SAL 表达式表示函数的返回值。值只能用在后置状态；为使用它的语法错误在以前的状态。|  
  
## 特定于字符串  
 下面说明内部函数启用字符串的处理。  全部这4个函数为同一个目的服务：返回类型的元素数目在空终结器之前找到。  差异在于这是引用的元素的数据。  请注意，如果要指定不构成字符 null 终止的缓冲区的长度，请使用从前面的 `_Nullterm_length_(param)` 说明。  
  
|批注|说明|  
|--------|--------|  
|`_String_length_(param)`|`param` 元素的数量是字符中等于但不包含 null 结束符。  此注释对于字符串的字符类型保留的。|  
|`strlen(param)`|`param` 元素的数量是字符中等于但不包含 null 结束符。  此注释的保留对字符数组的使用并类似于 C 运行时函数。[strlen\(\)](/visual-cpp/c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l)|  
|`wcslen(param)`|`param` 元素的数量是字符中等于（但不包含） null 结束符。  此注释的保留对宽字符数组的使用并类似于 C 运行时函数。[wcslen\(\)](/visual-cpp/c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l)|  
  
## 请参阅  
 [使用 SAL 批注以减少 C\/C\+\+ 代码缺陷](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [了解 SAL](../code-quality/understanding-sal.md)   
 [对函数参数和返回值进行批注](../code-quality/annotating-function-parameters-and-return-values.md)   
 [对函数行为进行批注](../code-quality/annotating-function-behavior.md)   
 [批注结构和类](../code-quality/annotating-structs-and-classes.md)   
 [对锁定行为进行批注](../code-quality/annotating-locking-behavior.md)   
 [指定何时以及在何处应用批注](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [最佳做法和示例](../code-quality/best-practices-and-examples-sal.md)