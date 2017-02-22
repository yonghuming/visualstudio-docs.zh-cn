---
title: "CA1309：使用序号 StringComparison | Microsoft Docs"
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
  - "UseOrdinalStringComparison"
  - "CA1309"
helpviewer_keywords: 
  - "UseOrdinalStringComparison"
  - "CA1309"
ms.assetid: 19be0854-cb6e-4efd-a4c8-a5c1fc6f7a71
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1309：使用序号 StringComparison
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|UseOrdinalStringComparison|  
|CheckId|CA1309|  
|类别|Microsoft.Globalization|  
|是否重大更改|非重大更改|  
  
## 原因  
 非语义的字符串比较运算不会将 <xref:System.StringComparison> 参数设置为 **Ordinal** 或 **OrdinalIgnoreCase**。  
  
## 规则说明  
 许多字符串运算（其中最重要的是 <xref:System.String.Compare%2A?displayProperty=fullName> 和 <xref:System.String.Equals%2A?displayProperty=fullName> 方法）现在都提供接受 <xref:System.StringComparision?displayProperty=fullName> 枚举值作为参数的重载。  
  
 当您指定 **StringComparison.Ordinal** 或 **StringComparison.OrdinalIgnoreCase** 时，字符串比较将是非语义的。  也就是说，在进行比较判断时会忽略特定于自然语言的功能。  这意味着，作出的判断基于简单的字节比较，并且忽略大小写或按区域性参数化的等值表。  因此，通过将参数显式设置为 **StringComparison.Ordinal** 或 **StringComparison.OrdinalIgnoreCase**，通常可以提高代码的速度、正确性和可靠性。  
  
## 如何解决冲突  
 若要解决与此规则的冲突，请将字符串比较方法更改为接受 <xref:System.StringComparison?displayProperty=fullName> 枚举作为参数的重载，并指定 **Ordinal** 或 **OrdinalIgnoreCase**。  例如，将 `String.Compare(str1, str2)` 更改为 `String.Compare(str1, str2, StringComparison.Ordinal)`。  
  
## 何时禁止显示警告  
 如果库或应用程序面向有限的本地用户或者应该使用当前区域性的语义时，可以安全地禁止显示此规则发出的警告。  
  
## 请参阅  
 [全球化警告](../code-quality/globalization-warnings.md)   
 [CA1307：指定 StringComparison](../code-quality/ca1307-specify-stringcomparison.md)