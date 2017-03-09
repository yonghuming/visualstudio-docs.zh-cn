---
title: "MSBuild 错误 MSB1039 | Microsoft Docs"
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
  - "MSB1039"
ms.assetid: 0e22161d-2c8b-4ca6-a7b7-73e23e082667
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 错误 MSB1039
**MSB1039: 指定工具集的版本。**  
  
 使用 **\/ToolsVersion** 开关时未指定任何值。  
  
### 更正此错误  
  
-   使用 **\/ToolsVersion** 开关时，请确保为 `ToolsVersion` 指定一个有效的非空值。  
  
## 请参阅  
 [工具集 \(ToolsVersion\)](../msbuild/msbuild-toolset-toolsversion.md)   
 [Project 元素 \(MSBuild\)](../msbuild/project-element-msbuild.md)   
 [其他资源](../msbuild/additional-msbuild-resources.md)