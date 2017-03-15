---
title: "MSBuild 错误 MSB3253 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSB3253"
ms.assetid: d4b5eb5b-703b-4b80-aa5d-6c70ff9fe84d
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 错误 MSB3253
**MSB3254: 项目中引用的程序集 \<名称\> 依赖未包含在 .NET Framework 客户端配置文件中的 \<名称2\>。\[MSB3254: The assembly \<name\> referenced in the project depends on \<name2\> which is not contained in the .NET Framework Client Profile.\]**  
  
 项目中引用的某个程序集或依赖程序集依赖于未包含在 [!INCLUDE[net_client_v35_long](../misc/includes/net_client_v35_long_md.md)]中的另一个程序集。  
  
 当项目引用第三方控件或 DLL，而该控件或 DLL 自身又引用外部程序集时，通常会出现此消息。  例如，项目使用一个控件，该控件又使用包含在完整 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 中的功能。  如果应用程序重新设置为以 [!INCLUDE[net_client_v35_long](../misc/includes/net_client_v35_long_md.md)]为目标，并且安装在没有 [!INCLUDE[net_v35_long](../misc/includes/net_v35_long_md.md)]的系统上，那么该应用程序在尝试访问 [!INCLUDE[net_client_v35_long](../misc/includes/net_client_v35_long_md.md)]子集中不包含的功能时可能无法正常工作。  
  
 此“错误”消息实际只是一个警告；应用程序仍将进行编译。  但如果包含该控件或 DLL 所引用的功能的程序集不存在，则该应用程序在以后可能会失败。  
  
 [!INCLUDE[net_client_v35_long](../misc/includes/net_client_v35_long_md.md)]是完整 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 3.5 运行库的子集。  有关 [!INCLUDE[net_client_v35_long](../misc/includes/net_client_v35_long_md.md)] 的更多信息，请参见[.NET Framework Client Profile](../Topic/.NET%20Framework%20Client%20Profile.md)。  
  
### 更正此错误  
  
-   从项目中移除指定的程序集引用，或将项目设置为以完整的 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]（而不是 [!INCLUDE[net_client_v35_long](../misc/includes/net_client_v35_long_md.md)]子集库）为目标。  有关如何以完整的 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 为目标的信息，请参见[如何：面向 .NET Framework 的某个版本](../ide/how-to-target-a-version-of-the-dotnet-framework.md)。  
  
## 请参阅  
 [目标 Framework 和目标平台](../msbuild/msbuild-target-framework-and-target-platform.md)   
 [Project 元素 \(MSBuild\)](../msbuild/project-element-msbuild.md)   
 [其他资源](../msbuild/additional-msbuild-resources.md)