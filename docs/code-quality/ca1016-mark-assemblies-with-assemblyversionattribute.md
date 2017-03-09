---
title: "CA1016：用 AssemblyVersionAttribute 标记程序集 | Microsoft Docs"
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
  - "MarkAssembliesWithAssemblyVersion"
  - "CA1016"
helpviewer_keywords: 
  - "CA1016"
  - "MarkAssembliesWithAssemblyVersion"
ms.assetid: 4340aed8-d92b-4cde-a398-cb6963c6da5a
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1016：用 AssemblyVersionAttribute 标记程序集
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|MarkAssembliesWithAssemblyVersion|  
|CheckId|CA1016|  
|类别|Microsoft.Design|  
|是否重大更改|非重大更改|  
  
## 原因  
 程序集没有版本号。  
  
## 规则说明  
 程序集标识包含下列信息：  
  
-   程序集名称  
  
-   版本号  
  
-   区域性  
  
-   公钥（适用于具有强名称的程序集）。  
  
 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 使用版本号唯一地标识程序集，并绑定到具有强名称的程序集中的类型。  版本号与版本和发行者策略一起使用。  默认情况下，仅使用用于生成应用程序的程序集版本运行应用程序。  
  
## 如何解决冲突  
 要修复与该规则的冲突，请使用 <xref:System.Reflection.AssemblyVersionAttribute?displayProperty=fullName> 特性将版本号添加到程序集。  请参见下面的示例。  
  
## 何时禁止显示警告  
 不要为第三方使用的程序集禁止显示该规则发出的警告，也不要在生产环境中禁止显示警告。  
  
## 示例  
 下面的示例演示已应用 <xref:System.Reflection.AssemblyVersionAttribute> 特性的程序集。  
  
 [!code-cs[FxCop.Design.AssembliesVersion#1](../code-quality/codesnippet/CSharp/ca1016-mark-assemblies-with-assemblyversionattribute_1.cs)]
 [!code-vb[FxCop.Design.AssembliesVersion#1](../code-quality/codesnippet/VisualBasic/ca1016-mark-assemblies-with-assemblyversionattribute_1.vb)]
 [!code-cpp[FxCop.Design.AssembliesVersion#1](../code-quality/codesnippet/CPP/ca1016-mark-assemblies-with-assemblyversionattribute_1.cpp)]  
  
## 请参阅  
 [程序集版本控制](../Topic/Assembly%20Versioning.md)   
 [如何：创建发行者策略](../Topic/How%20to:%20Create%20a%20Publisher%20Policy.md)