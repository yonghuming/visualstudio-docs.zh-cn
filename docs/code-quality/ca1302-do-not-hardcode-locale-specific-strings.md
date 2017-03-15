---
title: "CA1302：请不要对区域设置特定的字符串进行硬编码 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DoNotHardcodeLocaleSpecificStrings"
  - "CA1302"
helpviewer_keywords: 
  - "DoNotHardcodeLocaleSpecificStrings"
  - "CA1302"
ms.assetid: 05ed134a-837d-43d7-bf97-906edeac44ce
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 17
---
# CA1302：请不要对区域设置特定的字符串进行硬编码
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|DoNotHardcodeLocaleSpecificStrings|  
|CheckId|CA1302|  
|类别|Microsoft.Globalization|  
|是否重大更改|非重大更改|  
  
## 原因  
 方法使用字符串表示特定系统文件夹路径的一部分。  
  
## 规则说明  
 <xref:System.Environment.SpecialFolder?displayProperty=fullName> 枚举包含表示特殊系统文件夹的成员。  对于不同的操作系统，这些文件夹的位置可能具有不同的值，用户也可能会更改某些位置，或者这些位置已经进行了本地化。  例如，System 文件夹就是一个特殊文件夹，该文件夹在 [!INCLUDE[winxp](../code-quality/includes/winxp_md.md)] 中为“C:\\WINDOWS\\system32”，而在 [!INCLUDE[win2kfamily](../code-quality/includes/win2kfamily_md.md)] 中为“C:\\WINNT\\system32”。  <xref:System.Environment.GetFolderPath%2A?displayProperty=fullName> 方法返回与 <xref:System.Environment.SpecialFolder> 枚举关联的位置。  <xref:System.Environment.GetFolderPath%2A> 返回的位置已进行了本地化，以便与目前运行的计算机相适应。  
  
 该规则将使用 <xref:System.Environment.GetFolderPath%2A> 方法检索的文件夹路径标记到不同的目录级别。  每个字符串都会与这些标记进行比较。  如果找到匹配项，则假定该方法正在生成一个与该标记关联的表示系统位置的字符串。  为了确保可移植性和可本地化性，请使用 <xref:System.Environment.GetFolderPath%2A> 方法来检索特殊文件夹的位置，而不要使用字符串。  
  
## 如何解决冲突  
 要修复与该规则的冲突，请使用 <xref:System.Environment.GetFolderPath%2A> 方法检索位置。  
  
## 何时禁止显示警告  
 如果字符串不用于表示与 <xref:System.Environment.SpecialFolder> 枚举关联的某个系统位置，则可以安全地禁止显示此规则发出的警告。  
  
## 示例  
 下面的示例生成一个指向常规应用程序数据文件夹的路径，它将根据此规则产生三个警告。  然后，该示例使用 <xref:System.Environment.GetFolderPath%2A> 方法检索该路径。  
  
 [!code-cs[FxCop.Globalization.HardcodedLocaleStrings#1](../code-quality/codesnippet/CSharp/ca1302-do-not-hardcode-locale-specific-strings_1.cs)]
 [!code-vb[FxCop.Globalization.HardcodedLocaleStrings#1](../code-quality/codesnippet/VisualBasic/ca1302-do-not-hardcode-locale-specific-strings_1.vb)]  
  
## 相关规则  
 [CA1303：不要将文本作为本地化参数传递](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)