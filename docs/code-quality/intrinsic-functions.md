---
title: "内部函数 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _String_length_
- _Param_
- _Curr_
- _Old_
- _Nullterm_length_
- _Inexpressible_
ms.assetid: adf29f8c-89fd-4a5e-9804-35ac83e1c457
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: be65ae9177591b015cd8b29b3dbdc262b66a30ab
ms.sourcegitcommit: fb751e41929f031d1a9247bc7c8727312539ad35
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/15/2017
---
# <a name="intrinsic-functions"></a>内部函数
在 SAL 表达式可以是 C/c + + 表达式，前提是它是不具有副作用的表达式-例如，+ +，--，和所有在此上下文中具有副作用的函数调用。  但是，SAL 提供一些类似函数的对象和可以在 SAL 表达式中使用某些保留的符号。 这些被称为*内部函数*。  
  
## <a name="general-purpose"></a>通用  
 以下内部函数批注的 SAL 提供常规实用程序。  
  
|批注|描述|  
|----------------|-----------------|  
|`_Curr_`|要批注的对象的同义词。  当`_At_`批注正在使用，`_Curr_`等同于第一个参数`_At_`。  否则，将参数或批注与词法关联的整个函数/返回值。|  
|`_Inexpressible_(expr)`|表示的缓冲区大小太复杂，无法使用的批注表达式表示的情况-例如，当计算扫描输入的数据集，然后计算所选成员。|  
|`_Nullterm_length_(param)`|`param`是中最多到缓冲区，但不是包括 null 终止符的元素数。 它可应用于任何缓冲区的非聚合、 非 void 类型。|  
|`_Old_(expr)`|在不满足前提条件，计算时`_Old_`返回输入的值`expr`。  当它将计算后置条件中时，会返回值`expr`根据它进行计算中不满足前提条件。|  
|`_Param_(n)`|`n`Th 函数参数，请从 1 到计数`n`，和`n`是文本的整数常量。 如果该参数命名为，此批注等同于按名称访问参数。 **注意：** `n`可能更愿意使用由省略号，或者可能在不使用名称在函数原型中使用的位置参数。  |  
|`return`|C/c + + 保留关键字`return`可以 SAL 表达式中使用以指示函数的返回值。  Post 状态;，值才可用它是导致语法错误的以前状态使用它。|  
  
## <a name="string-specific"></a>特定于字符串  
 以下内部函数批注启用的字符串的操作。 这些函数的所有四个具有相同的用途： 返回之前 null 终止符的占用找到的类型的元素的数目。 差异会引用的元素中的数据类型。 请注意，如果你想要指定以 null 结尾的长度的缓冲区，不由字符，请使用`_Nullterm_length_(param)`注释与上一节。  
  
|批注|描述|  
|----------------|-----------------|  
|`_String_length_(param)`|`param`是中最多到字符串，但不是包括 null 终止符的元素数。 此批注留待字符串的字符类型。|  
|`strlen(param)`|`param`是中最多到字符串，但不是包括 null 终止符的元素数。 此批注保留供使用的字符数组和类似于 C 运行时函数[strlen()](/cpp/c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l)。|  
|`wcslen(param)`|`param`是 （但不是包括） 的字符串中的元素数 null 终止符的占用。 此批注保留为使用宽字符数组和类似于 C 运行时函数[wcslen()](/cpp/c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l)。|  
  
## <a name="see-also"></a>另请参阅  
 [使用 SAL 批注以减少 C/c + + 代码缺陷](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [了解 SAL](../code-quality/understanding-sal.md)   
 [对函数参数和返回值进行批注](../code-quality/annotating-function-parameters-and-return-values.md)   
 [对函数行为进行批注](../code-quality/annotating-function-behavior.md)   
 [批注结构和类](../code-quality/annotating-structs-and-classes.md)   
 [对锁定行为进行批注](../code-quality/annotating-locking-behavior.md)   
 [指定何时以及在何处应用批注](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [最佳做法和示例](../code-quality/best-practices-and-examples-sal.md)