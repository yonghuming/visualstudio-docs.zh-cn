---
title: "MSBuild 错误 MSB3252 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSB3252"
helpviewer_keywords: 
  - "MSB3252"
ms.assetid: 4e6982b8-84b3-4d21-94e1-05cc10bf1393
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 错误 MSB3252
**MSB3252：项目具有对程序集 \<名称\> 的引用。  此程序集不是 .NET Framework Client Profile 的一部分。  如果没有此引用，可能出现编译或运行时错误。**  
  
 调用了不属于 [!INCLUDE[net_client_v35_long](../misc/includes/net_client_v35_long_md.md)]的程序集或依赖程序集中的成员。  因此无法解析该调用，无法编译应用程序。  
  
 有关 [!INCLUDE[net_client_v35_long](../misc/includes/net_client_v35_long_md.md)] 的更多信息，请参见[.NET Framework Client Profile](../Topic/.NET%20Framework%20Client%20Profile.md)。  
  
### 更正此错误  
  
-   从项目中移除指定的程序集引用，或将项目设置为以完整的 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]（而不是 [!INCLUDE[net_client_v35_long](../misc/includes/net_client_v35_long_md.md)]子集库）为目标。  有关如何以完整的 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 为目标的信息，请参见[如何：面向 .NET Framework 的某个版本](../ide/how-to-target-a-version-of-the-dotnet-framework.md)。  
  
## 请参阅  
 [目标 Framework 和目标平台](../msbuild/msbuild-target-framework-and-target-platform.md)   
 [Project 元素 \(MSBuild\)](../msbuild/project-element-msbuild.md)   
 [其他资源](../msbuild/additional-msbuild-resources.md)