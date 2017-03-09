---
title: "MSBuild 错误 MSB3255 | Microsoft Docs"
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
  - "MSB3255"
ms.assetid: baac844e-a662-4421-bed1-2bc98f2e1cdf
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 错误 MSB3255
**MSB3255: 未能在目标 Framework 目录中或 InstalledAssemblySubsetTables 中指定的位置处找到任何目标 Framework 子集文件。**  
  
 将名称传入 <xref:Microsoft.Build.Tasks.ResolveAssemblyReference.FullTargetFrameworkSubsetNames%2A> 属性但找不到具有该名称的子集时将发生此错误。  
  
 [!INCLUDE[net_client_v35_long](../misc/includes/net_client_v35_long_md.md)]是完整 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 3.5 运行库的子集。  有关 [!INCLUDE[net_client_v35_long](../misc/includes/net_client_v35_long_md.md)] 的更多信息，请参见[.NET Framework Client Profile](../Topic/.NET%20Framework%20Client%20Profile.md)。  
  
 过程  
  
### 更正此错误  
  
-   将子集文件的副本放入目标框架文件夹或 <xref:Microsoft.Build.Tasks.ResolveAssemblyReference.InstalledAssemblySubsetTables%2A> 中所指定的某个位置。  
  
## 请参阅  
 [Project 元素 \(MSBuild\)](../msbuild/project-element-msbuild.md)   
 [其他资源](../msbuild/additional-msbuild-resources.md)