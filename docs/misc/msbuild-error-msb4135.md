---
title: "MSBuild 错误 MSB4135 | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSB4135"
ms.assetid: 9192f772-ad13-42f7-b53f-c5e31846fa5f
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 错误 MSB4135
**MSB4135: 从注册表项“\<项\>”或子项“'  \<项\>”读取工具集信息时出错**  
  
 未能读取在注册表中定义的自定义工具集信息。  
  
### 更正此错误  
  
-   如果在注册表中定义了自定义工具集，请确保其采用有效的注册表格式，具有正确的 `ToolsVersion` 名称以及正确的 `MSBuildBinPath` 或 `MSBuildToolsPath` 值。  
  
## 请参阅  
 [标准和自定义工具集配置](../msbuild/standard-and-custom-toolset-configurations.md)   
 [Project 元素 \(MSBuild\)](../msbuild/project-element-msbuild.md)   
 [其他资源](../msbuild/additional-msbuild-resources.md)