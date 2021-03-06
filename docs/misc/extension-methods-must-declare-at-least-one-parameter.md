---
title: "扩展方法必须声明至少一个参数 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc36552"
  - "bc36552"
helpviewer_keywords: 
  - "BC36552"
ms.assetid: a8cc8cdd-cdb5-42ca-b5a1-c9a71abd46eb
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 扩展方法必须声明至少一个参数
扩展方法必须声明至少一个参数。 第一个参数指定要扩展哪个类型。  
  
 不带参数的扩展方法无效，因为第一个参数指定该方法将扩展的数据类型。 第一个参数绑定到调用方法的数据类型的实例。  
  
 **错误 ID：**BC36552  
  
### 更正此错误  
  
-   添加你的方法将扩展的类型的参数。  
  
## 示例  
 以下示例中的第一个参数指示 `Print` 方法扩展 `String` 数据类型。  
  
```  
<Extension()> _ Public Sub Print (ByVal str As String) Console.WriteLine(str) End Sub  
```  
  
 当如下调用扩展方法时，该方法中的参数 `str` 绑定到 `greeting`，它是调用 `Print` 的 `String` 的实例。 编译器将使用 `greeting` 作为扩展方法 `Print` 的参数。  
  
```  
Dim greeting As String = "Hello" greeting.Print()  
```  
  
## 请参阅  
 [扩展方法](/dotnet/visual-basic/programming-guide/language-features/procedures/extension-methods)   
 [过程参数和自变量](/dotnet/visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments)   
 [过程](/dotnet/visual-basic/programming-guide/language-features/procedures/index)