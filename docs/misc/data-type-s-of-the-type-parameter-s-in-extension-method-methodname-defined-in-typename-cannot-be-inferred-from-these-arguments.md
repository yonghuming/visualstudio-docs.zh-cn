---
title: "无法从这些实参推断“&lt;typename&gt;”中定义的扩展方法“&lt;methodname&gt;”中类型形参的数据类型 | Microsoft Docs"
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
  - "bc36649"
  - "vbc36646"
  - "bc36646"
  - "vbc36649"
helpviewer_keywords: 
  - "BC36649"
  - "BC36646"
ms.assetid: 55274b01-6d78-4950-861e-07d9273ef76e
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 无法从这些实参推断“&lt;typename&gt;”中定义的扩展方法“&lt;methodname&gt;”中类型形参的数据类型
无法从这些实参推断“\<typename\>”中定义的扩展方法“\<methodname\>”中类型形参的数据类型。 显式指定数据类型可更正此错误。  
  
 在计算对泛型扩展方法的调用时，试图使用类型推断功能来确定类型形参的数据类型。 但是，编译器找不到此方法中的类型形参的数据类型，因此它报告此错误。  
  
> [!NOTE]
>  当无法指定实参时（例如，对于查询表达式中的查询运算符），显示的错误消息不包括第二个句子。  
  
 下面的代码演示了此错误。  
  
```vb#  
Module Module1 Sub Main() Dim classInstance As ClassExample '' Not valid. 'classInstance.GenericExtensionMethod("Hello", "World") End Sub <System.Runtime.CompilerServices.Extension()> _ Sub GenericExtensionMethod(Of T)(ByVal classEx As ClassExample, _ ByVal x As String, ByVal y As _ InterfaceExample(Of T)) End Sub End Module Interface InterfaceExample(Of T) End Interface Class ClassExample End Class  
```  
  
 **错误 ID：**BC36649 和 BC36646  
  
### 更正此错误  
  
-   你或许能够指定类型形参的数据类型，而无需依赖类型推断。  
  
## 请参阅  
 [宽松委托转换](/dotnet/visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion)   
 [扩展方法](/dotnet/visual-basic/programming-guide/language-features/procedures/extension-methods)   
 [Visual Basic 中的泛型过程](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)   
 [Visual Basic 中的类型转换](/dotnet/visual-basic/programming-guide/language-features/data-types/type-conversions)