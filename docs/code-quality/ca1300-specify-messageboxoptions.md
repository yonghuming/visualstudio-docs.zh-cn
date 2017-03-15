---
title: "CA1300：指定 MessageBoxOptions | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SpecifyMessageBoxOptions"
  - "CA1300"
helpviewer_keywords: 
  - "SpecifyMessageBoxOptions"
  - "CA1300"
ms.assetid: 9357a724-026e-4a3d-a03a-f14635064ec6
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1300：指定 MessageBoxOptions
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|SpecifyMessageBoxOptions|  
|CheckId|CA1300|  
|类别|Microsoft.Globalization|  
|是否重大更改|非重大更改|  
  
## 原因  
 某方法调用了未采用 <xref:System.Windows.Forms.MessageBoxOptions?displayProperty=fullName> 参数的 <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=fullName> 方法的重载。  
  
## 规则说明  
 要为使用从右向左阅读顺序的区域性正确显示消息框，必须将 <xref:System.Windows.Forms.MessageBoxOptions> 枚举的 <xref:System.Windows.Forms.MessageBoxOptions> 和 <xref:System.Windows.Forms.MessageBoxOptions> 成员传递给 <xref:System.Windows.Forms.MessageBox.Show%2A> 方法。  检查包含控件的 <xref:System.Windows.Forms.Control.RightToLeft%2A?displayProperty=fullName> 属性以确定是否使用从右向左的阅读顺序。  
  
## 如何解决冲突  
 要修复与该规则的冲突，请调用采用 <xref:System.Windows.Forms.MessageBoxOptions> 参数的 <xref:System.Windows.Forms.MessageBox.Show%2A> 方法的重载。  
  
## 何时禁止显示警告  
 如果不是针对使用从右向左阅读顺序的区域性来本地化代码库，则可以安全地禁止显示此规则发出的警告。  
  
## 示例  
 下面的示例演示消息框的显示方法，该消息框带有适用于从右向左阅读顺序的区域性的选项。  需要资源文件（未显示）才能生成此示例。  按照示例中的注释进行操作，可以不使用资源文件生成示例并测试从右向左功能。  
  
 [!code-vb[FxCop.Globalization.SpecifyMBOptions#1](../code-quality/codesnippet/VisualBasic/ca1300-specify-messageboxoptions_1.vb)]
 [!code-cs[FxCop.Globalization.SpecifyMBOptions#1](../code-quality/codesnippet/CSharp/ca1300-specify-messageboxoptions_1.cs)]  
  
## 请参阅  
 <xref:System.Resources.ResourceManager?displayProperty=fullName>   
 [桌面应用程序中的资源](../Topic/Resources%20in%20Desktop%20Apps.md)