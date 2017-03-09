---
title: "MSBuild 错误 MSB4136 | Microsoft Docs"
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
  - "MSB4136"
ms.assetid: 6f0543d3-f8c0-44e1-8748-8a71be599bf4
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 错误 MSB4136
**MSB4136: 读取配置信息时出错。**  
  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 在尝试读取 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 配置文件 \(msbuild.exe.config\) 中的工具集信息时收到错误。  
  
### 更正此错误  
  
-   确保配置文件正确无误并且格式完好。  例如，如果您通过添加工具集自定义了 .config 文件，请检查工具集定义。  
  
## 请参阅  
 [重写 ToolsVersion 设置](../msbuild/overriding-toolsversion-settings.md)   
 [Project 元素 \(MSBuild\)](../msbuild/project-element-msbuild.md)   
 [其他资源](../msbuild/additional-msbuild-resources.md)