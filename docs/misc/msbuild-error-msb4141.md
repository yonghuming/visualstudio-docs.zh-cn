---
title: "MSBuild 错误 MSB4141 | Microsoft Docs"
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
  - "MSB4141"
ms.assetid: 0d190884-e64d-4d6b-817d-ce4644788fce
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 错误 MSB4141
**MSB4141: 没有为 ToolsVersion“\<x.x\>”指定 MSBuildToolsPath。**  
  
 虽然定义了自定义工具集，但没有为 `MSBuildToolsPath` 指定值。  
  
### 更正此错误  
  
-   当您在注册表或 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 配置文件中定义自定义工具集时，请为 `MSBuildToolsPath` 指定一个有效值。  
  
## 请参阅  
 [标准和自定义工具集配置](../msbuild/standard-and-custom-toolset-configurations.md)   
 [Project 元素 \(MSBuild\)](../msbuild/project-element-msbuild.md)   
 [其他资源](../msbuild/additional-msbuild-resources.md)