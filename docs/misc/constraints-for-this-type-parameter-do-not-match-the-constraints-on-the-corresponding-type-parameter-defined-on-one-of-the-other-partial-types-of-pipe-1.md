---
title: "此类型参数的约束与在“|1”的某个其他分部类型上定义的相应类型参数的约束不匹配 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30932"
  - "bc30932"
helpviewer_keywords: 
  - "BC30932"
ms.assetid: a38ca4ad-6bbf-421e-a0d7-c5e0a9029160
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 此类型参数的约束与在“|1”的某个其他分部类型上定义的相应类型参数的约束不匹配
当在多个声明中划分类或结构的定义时，编译器将类或结构视为其所有分部声明的联合。 因此，你无法在多个分部声明中定义任何冲突的修饰符或类型形参列表。  
  
 **错误 ID：**BC30932  
  
### 更正此错误  
  
1.  确定哪个类型形参列表是你的类或结构所需的。 这包括参数、参数的顺序及其约束列表。  
  
2.  请确保每个分部定义使用相同的类型形参列表。  
  
## 请参阅  
 [分部](/dotnet/visual-basic/language-reference/modifiers/partial)   
 [Visual Basic 中的泛型类型](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)