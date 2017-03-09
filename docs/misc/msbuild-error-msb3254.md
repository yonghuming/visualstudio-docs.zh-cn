---
title: "MSBuild 错误 MSB3254 | Microsoft Docs"
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
  - "MSB3254"
ms.assetid: cb9636b2-d9b3-466d-959c-14c7c8017a78
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 错误 MSB3254
**MSB3254: 将忽略文件 \<名称\>，因为无法读取它。  此文件要么传入到 InstalledAssemblySubsetTables，要么是通过搜索 TargetFrameworkDirectories 中的 \<名称\> 文件夹找到的。**  
  
 当无法读取 [!INCLUDE[net_client_v35_long](../misc/includes/net_client_v35_long_md.md)] XML 文件 client.xml 时将发生此错误。  此文件因损坏、锁定或其他某种问题而不可读取。  
  
 [!INCLUDE[net_client_v35_long](../misc/includes/net_client_v35_long_md.md)]是完整 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 3.5 运行库的子集。  有关 [!INCLUDE[net_client_v35_long](../misc/includes/net_client_v35_long_md.md)] 的更多信息，请参见[.NET Framework Client Profile](../Topic/.NET%20Framework%20Client%20Profile.md)。  
  
 过程  
  
### 更正此错误  
  
-   确保您对该文件具有完全访问权限，或者重新安装 [!INCLUDE[net_client_v35_long](../misc/includes/net_client_v35_long_md.md)]可再发行运行库以替换损坏的文件。  
  
## 请参阅  
 [Project 元素 \(MSBuild\)](../msbuild/project-element-msbuild.md)   
 [其他资源](../msbuild/additional-msbuild-resources.md)