---
title: "MSBuild 错误 MSB4132 | Microsoft Docs"
ms.custom: ""
ms.date: "11/23/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSB4132"
ms.assetid: 4ac265a7-0f8d-4fec-ba6e-cd70cbd5d89e
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 错误 MSB4132
**MSB4132: 无法识别工具版本“\<版本\>”。**  
  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 找不到与指定的 `ToolsVersion` 值对应的工具集。  
  
### 更正此错误  
  
-   使用 MSBuild **\/ToolsVersion** 开关时，请在项目标记或命令行中为 `ToolsVersion` 指定一个有效值。  
  
## 请参阅  
 <xref:Microsoft.Build.Tasks.MSBuild.ToolsVersion%2A>   
 [其他资源](../msbuild/additional-msbuild-resources.md)