---
title: "Option Strict On 不允许后期绑定 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30574"
  - "vbc30574"
helpviewer_keywords: 
  - "BC30574"
ms.assetid: 9da4b826-2e12-4a5d-9e17-762b0b68fc9b
caps.latest.revision: 11
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Option Strict On 不允许后期绑定
[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 允许将任何数据类型隐式转换为任何其他数据类型。 但是，如果一种数据类型的值转换为精度较低或容量较小的数据类型，则会发生数据丢失。`Option Strict On` 可确保在这些类型的转换时提供编译时通知，因此可避免这些类型。 不能将 `Option Strict On` 与后期绑定配合使用。  
  
 以下的代码示例使用后期绑定，在将 `Option Strict` 设置为 `On` 时会导致此错误。  
  
 [!CODE [VbVbalrOptionStrictError#1](VbVbalrOptionStrictError#1)]  
  
 **错误 ID：**BC30574  
  
### 更正此错误  
  
-   修改对象声明以使用显式类型，如以下示例所示：  
  
     [!CODE [VbVbalrOptionStrictError#2](VbVbalrOptionStrictError#2)]  
  
 \- 或 \-  
  
-   修改后期绑定表达式以指定显式类型，如以下示例所示：  
  
     [!CODE [VbVbalrOptionStrictError#3](VbVbalrOptionStrictError#3)]  
  
 \- 或 \-  
  
-   让编译器推断特定的类型，如以下示例所示：  
  
     [!CODE [VbVbalrOptionStrictError#4](VbVbalrOptionStrictError#4)]  
  
 \- 或 \-  
  
-   通过随后删除词 `On` 或通过显式指定 `Off` 关闭 `Option Strict`。  
  
## 请参阅  
 [类型转换函数](/dotnet/visual-basic/language-reference/functions/type-conversion-functions)   
 [Option Strict 语句](/dotnet/visual-basic/language-reference/statements/option-strict-statement)   
 [扩大转换和收缩转换](/dotnet/visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions)