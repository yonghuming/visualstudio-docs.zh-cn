---
title: "CA1303：不要将文本作为本地化参数传递 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Do not pass literals as localized parameters"
  - "DoNotPassLiteralsAsLocalizedParameters"
  - "CA1303"
helpviewer_keywords: 
  - "CA1303"
  - "DoNotPassLiteralsAsLocalizedParameters"
ms.assetid: 904d284e-76d0-4b8f-a4df-0094de8d7aac
caps.latest.revision: 22
caps.handback.revision: 22
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1303：不要将文本作为本地化参数传递
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|DoNotPassLiteralsAsLocalizedParameters|  
|CheckId|CA1303|  
|类别|Microsoft.Globalization|  
|是否重大更改|否|  
  
## 原因  
 某方法将一个字符串作为参数传递给 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 类库中的构造函数或方法，该字符串应该是可本地化的。  
  
 此警告的触发条件为，原义字符串在一个或多个以下的情况下为 true 时，其作为值传递给参数或属性：  
  
-   参数或属性的 <xref:System.ComponentModel.LocalizableAttribute> 特性设置为 true。  
  
-   参数或属性名称包含“文本”、“消息”或“标题”。  
  
-   对 Console.Write 或 Console.WriteLine 方法传递的字符串参数的名称是“值”或者“格式”。  
  
## 规则说明  
 嵌入在源代码中的字符串难以进行本地化。  
  
## 如何解决冲突  
 要修复与该规则的冲突，请使用通过 <xref:System.Resources.ResourceManager> 类的实例检索的字符串替换该字符串。  
  
## 何时禁止显示警告  
 如果将不会本地化代码库，或者如果字符串未公开给使用该代码库的最终用户或开发人员，则可以安全地禁止显示此规则发出的警告。  
  
 通过重命名已命名的参数或属性或者通过将这些项设置为条件项，用户可以消除不应传递本地化字符串的方法的影响。  
  
## 示例  
 下面的示例演示在两个参数之一超出范围时引发异常的方法。  对于第一个参数，向异常构造函数传递了字符串，此操作与该规则冲突。  对于第二个参数，向构造函数正确地传递了通过 <xref:System.Resources.ResourceManager> 检索到的字符串。  
  
 [!CODE [FxCop.Globalization.DoNotPassLiterals#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Globalization.DoNotPassLiterals#1)]  
  
## 请参阅  
 [桌面应用程序中的资源](../Topic/Resources%20in%20Desktop%20Apps.md)