---
title: "指定何时以及在何处应用批注 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_Group_"
  - "_At_"
  - "_When_"
  - "_At_buffer_"
ms.assetid: 8e4f4f9c-5dfa-4835-87df-ecd1698fc650
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 指定何时以及在何处应用批注
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

当批注的条件时，可能要求其他注释来指定分析器的这一点。例如，如果函数具有可同步或异步的变量，函数的行为如下所示：在同步的情况下最终总是成功，但是，在异步的情况则将报告错误，则无法立即成功。  当同步函数调用时，检查结果值不为代码分析器提供值，因为它不会返回。但是，当函数异步调用时，并且函数结果未被检查，可能发生一系列的严重错误。  此示例演示可以使用在此文章描述的 `_When_` 注释来启用检查。  
  
## 结构化批注  
 若要控制何时在应用注释，请使用以下结构上的注释。  
  
|批注|说明|  
|--------|--------|  
|`_At_(expr, anno-list)`|`expr` 是为左值的表达式。  `anno-list` 的注释的应用于由 `expr`命名的对象。  对于 `anno-list`的每个注释，`expr` 被解释在前置条件中，如果注释在前置条件解释并在发送条件注释是否在后期条件解释。|  
|`_At_buffer_(expr, iter, elem-count, anno-list)`|`expr` 是为左值的表达式。  `anno-list` 的注释的应用于由 `expr`命名的对象。  对于 `anno-list`的每个注释，`expr` 被解释在前置条件中，如果注释在前置条件解释并在发送条件注释是否在后期条件解释。<br /><br /> `iter` 为应用范围为批注变量名 \( 包含`anno-list`\)。  `iter` 有一种隐式类型 `long`。  在任何封闭范围的同名变量从计算隐藏。<br /><br /> `elem-count`计算结果为一个整数的表达式。|  
|`_Group_(anno-list)`|`anno-list` 的注释都视为具有应用于组说明应用到每个注释的所有限定符。|  
|`_When_(expr, anno-list)`|`expr` 是可转换为 `bool`的表达式。  当它不为零 \(`true`\)，在 `anno-list` 中指定的注释视为是适当的。<br /><br /> 默认情况下，提供 `anno-list`中每个注释，`expr` 被解释使用输入值，如果注释是前置条件，然后使用值，如果输出注释是 POST 条件。  若要重写默认值，则可以使用 `_Old_` 内部，在后期计算条件表示时应使用输入值。 **Note:**  不同的注释可以启用作为使用 `_When_`的结果，如果一个变量值—例如，`*pLength`—包含在内，由于 `expr` 的计算结果在前置条件中可能与其发布在条件的计算的结果不同。|  
  
## 请参阅  
 [使用 SAL 批注以减少 C\/C\+\+ 代码缺陷](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [了解 SAL](../code-quality/understanding-sal.md)   
 [对函数参数和返回值进行批注](../code-quality/annotating-function-parameters-and-return-values.md)   
 [对函数行为进行批注](../code-quality/annotating-function-behavior.md)   
 [批注结构和类](../code-quality/annotating-structs-and-classes.md)   
 [对锁定行为进行批注](../code-quality/annotating-locking-behavior.md)   
 [内部函数](../code-quality/intrinsic-functions.md)   
 [最佳做法和示例](../code-quality/best-practices-and-examples-sal.md)