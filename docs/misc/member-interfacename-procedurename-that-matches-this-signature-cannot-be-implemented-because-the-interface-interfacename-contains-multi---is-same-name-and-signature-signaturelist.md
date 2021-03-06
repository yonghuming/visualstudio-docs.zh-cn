---
title: "无法实现与此签名匹配的成员“&lt;interfacename&gt;.&lt;procedurename&gt;”，因为接口“&lt;interfacename&gt;”包含多个具有此相同名称和签名 &lt;signaturelist&gt; 的成员 | Microsoft Docs"
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
  - "vbc30937"
  - "bc30937"
helpviewer_keywords: 
  - "BC30937"
ms.assetid: e917d85e-95e0-431a-9d09-39ce5d4fc894
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 无法实现与此签名匹配的成员“&lt;interfacename&gt;.&lt;procedurename&gt;”，因为接口“&lt;interfacename&gt;”包含多个具有此相同名称和签名 &lt;signaturelist&gt; 的成员
过程或属性试图实现在已实现接口中定义的某过程或属性，但编译器找到多个具有相同名称和签名的接口过程或属性的版本。  
  
 如下面的主干声明所示，存在构造的泛型类型的情况下可能出现此错误。  
  
```  
Public Interface baseInterface(Of t) Sub doSomething(ByVal inputValue As String) Sub doSomething(ByVal inputValue As t) End Class Public Class implementingClass Implements baseInterface(Of String) Sub doSomething(ByVal inputValue As String) _ Implements baseInterface(Of String).doSomething End Sub End Class  
```  
  
 因为 `implementingClass` 实现为其类型参数 `t` 提供 `String` 的 `baseInterface`，`baseInterface` 中两个版本的 `doSomething` 使用就 `implementingClass` 而言完全相同的签名。 因此，编译器无法确定要实现的版本。  
  
 **错误 ID：**BC30937  
  
### 更正此错误  
  
-   更改提供给基类的一个或多个类型参数，以确保成员过程或属性的一个或多个签名不相同。  
  
     \- 或 \-  
  
-   不要实现此基类。 不能通过你正在使用的类型参数集来实现它，因为必须实现其全部成员。  
  
## 请参阅  
 [Implements](/dotnet/visual-basic/language-reference/statements/implements-clause)   
 [Implements 语句](/dotnet/visual-basic/language-reference/statements/implements-statement)   
 [不在生成中：Implements 关键字和 Implements 语句](http://msdn.microsoft.com/zh-cn/b96560f7-6413-480f-a1e2-f80253bab5be)