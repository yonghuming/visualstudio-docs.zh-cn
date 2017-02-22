---
title: "CA1307：指定 StringComparison | Microsoft Docs"
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
  - "CA1307"
  - "SpecifyStringComparison"
helpviewer_keywords: 
  - "CA1307"
  - "SpecifyStringComparison"
ms.assetid: 9b0d5e71-1683-4a0d-bc4a-68b2fbd8af71
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1307：指定 StringComparison
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|SpecifyStringComparison|  
|CheckId|CA1307|  
|类别|Microsoft.Globalization|  
|是否重大更改|非重大更改|  
  
## 原因  
 字符串比较运算使用不设置 <xref:System.StringComparison> 参数的方法重载。  
  
## 规则说明  
 许多字符串运算（其中最重要的是 <xref:System.String.Compare%2A> 和 <xref:System.String.Equals%2A> 方法）都提供接受 <xref:System.StringComparison> 枚举值作为参数的重载。  
  
 只要存在接受 <xref:System.StringComparison> 参数的重载，就应用它来代替不接受此参数的重载。  通过显式设置此参数，通常会使代码更清楚，更易于维护。  
  
## 如何解决冲突  
 若要解决与此规则的冲突，请将字符串比较方法更改为接受 <xref:System.StringComparison> 枚举作为参数的重载。  例如，将 `String.Compare(str1, str2)` 更改为 `String.Compare(str1, str2, StringComparison.Ordinal)`。  
  
## 何时禁止显示警告  
 如果库或应用程序面向有限的本地用户并且因此不会进行本地化，则可以安全地禁止显示此规则发出的警告。  
  
## 请参阅  
 [全球化警告](../code-quality/globalization-warnings.md)   
 [CA1309：使用序号 StringComparison](../code-quality/ca1309-use-ordinal-stringcomparison.md)