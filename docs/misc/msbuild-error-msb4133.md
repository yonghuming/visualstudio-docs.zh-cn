---
title: "MSBuild 错误 MSB4133 | Microsoft Docs"
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
  - "MSB4133"
ms.assetid: 5f18937a-fda1-4315-81f9-7cee02802a6d
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 错误 MSB4133
**MSB4133: 指定了默认工具版本“\<x.x.\>”，但未能找到其定义。**  
  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 找不到在项目文件中定义为 `DefaultToolsVersion` 的工具集。  
  
### 更正此错误  
  
-   确保正确指定了 `DefaultToolsVersion`，并且此工具集在注册表中或在 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 配置文件中定义。  
  
## 请参阅  
 <xref:Microsoft.Build.BuildEngine.Toolset>   
 [Project 元素 \(MSBuild\)](../msbuild/project-element-msbuild.md)   
 [其他资源](../msbuild/additional-msbuild-resources.md)