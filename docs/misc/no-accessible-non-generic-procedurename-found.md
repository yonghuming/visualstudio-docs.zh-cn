---
title: "未找到可访问的非泛型“&lt;procedurename&gt;” | Microsoft Docs"
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
  - "vbc32117"
  - "bc32117"
helpviewer_keywords: 
  - "BC32117"
ms.assetid: a7bf8b67-8a0a-499e-9992-dc00e09b7ff4
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 未找到可访问的非泛型“&lt;procedurename&gt;”
有语句调用具有多个重载版本的过程，但所有重载版本都是泛型，并且该调用未提供类型实参。  
  
 如果只有一个泛型版本并且你在不提供类型实参的情况下调用它，则编译器可以尝试*类型推理*。 有关详细信息，请参见 [Visual Basic 中的泛型过程](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures) 中的“类型推理”。 但是，如果存在多个泛型版本，则编译器无法从中进行选择，除非你提供类型实参。 如果提供一个类型实参，则必须为重载版本之一定义的每个类型形参提供一个类型实参。  
  
 **错误 ID：**BC32117  
  
### 更正此错误  
  
-   使用类型实参列表调用过程。  
  
## 请参阅  
 [Overloads](/dotnet/visual-basic/language-reference/modifiers/overloads)   
 [过程重载](/dotnet/visual-basic/programming-guide/language-features/procedures/procedure-overloading)   
 [Visual Basic 中的泛型类型](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Visual Basic 中的泛型过程](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)