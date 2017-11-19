---
title: "指定何时以及在何处应用批注 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _Group_
- _At_
- _When_
- _At_buffer_
ms.assetid: 8e4f4f9c-5dfa-4835-87df-ecd1698fc650
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 5bfff9eb7e2040d5a4b75fa82c2a504f2aaeceda
ms.sourcegitcommit: fb751e41929f031d1a9247bc7c8727312539ad35
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/15/2017
---
# <a name="specifying-when-and-where-an-annotation-applies"></a>指定何时以及在何处应用批注
条件批注时，则可能需要其他批注以指定的分析器。  例如，如果函数具有可以是同步还是异步的变量，将函数的行为，如下所示： 在同步的情况下始终最终成功，但在异步的情况下它报告错误如果它不能立即成功。 以同步方式调用该函数时，检查的结果值提供到代码分析器的任何值，因为它将不返回。  但是，当以异步方式调用该函数，且还未签函数结果时, 可能发生严重错误。 此示例演示如何在其中你可以使用的情况下`_When_`批注 — 在本文的后面介绍-若要启用检查。  
  
## <a name="structural-annotations"></a>结构化批注  
 若要控制何时以及在何处应用批注，请使用以下结构化批注。  
  
|批注|描述|  
|----------------|-----------------|  
|`_At_(expr, anno-list)`|`expr`是产生左值表达式。 中的批注`anno-list`应用于命名的对象`expr`。 在每个批注`anno-list`，`expr`如果批注解释在前置条件，并在后置条件如果批注解释后置条件中，在前置条件中解释。|  
|`_At_buffer_(expr, iter, elem-count, anno-list)`|`expr`是产生左值表达式。 中的批注`anno-list`应用于命名的对象`expr`。 在每个批注`anno-list`，`expr`如果批注解释在不满足前提条件，并在后置条件如果批注解释后置条件中，在前置条件中解释。<br /><br /> `iter`是的变量的范围限定为批注的名称 (包括`anno-list`)。 `iter`具有隐式类型`long`。 从评估中隐藏任何封闭范围中具有相同名称的变量。<br /><br /> `elem-count`是计算结果为整数的表达式。|  
|`_Group_(anno-list)`|中的批注`anno-list`所有被视为具有适用于应用于每个批注的组批注任何限定符。|  
|`_When_(expr, anno-list)`|`expr`是可以转换为一个表达式`bool`。 当它为非零 (`true`) 中, 指定的批注`anno-list`被视为适用。<br /><br /> 默认情况下，在每个批注`anno-list`，`expr`解释为使用的输入的值，如果批注是前提条件，并且如果使用的输出值的批注不后置条件。 若要重写默认值，可以使用`_Old_`内部函数，当你的计算结果以指示应使用输入的值后置条件。 **注意：**可能是因为使用启用不同的注释`_When_`如果可变值-例如， `*pLength`-因为涉及的计算的结果`expr`前置条件中可能不同于其计算导致后置条件。|  
  
## <a name="see-also"></a>另请参阅  
 [使用 SAL 批注以减少 C/c + + 代码缺陷](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [了解 SAL](../code-quality/understanding-sal.md)   
 [对函数参数和返回值进行批注](../code-quality/annotating-function-parameters-and-return-values.md)   
 [对函数行为进行批注](../code-quality/annotating-function-behavior.md)   
 [批注结构和类](../code-quality/annotating-structs-and-classes.md)   
 [对锁定行为进行批注](../code-quality/annotating-locking-behavior.md)   
 [内部函数](../code-quality/intrinsic-functions.md)   
 [最佳做法和示例](../code-quality/best-practices-and-examples-sal.md)