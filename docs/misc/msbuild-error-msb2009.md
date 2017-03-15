---
title: "MSBuild 错误 MSB2009 | Microsoft Docs"
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
  - "MSBuild.UnrecognizedAttribute"
helpviewer_keywords: 
  - "MSB2009"
ms.assetid: 34fd83b4-dead-49e5-b1ee-b23dc5a95244
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 错误 MSB2009
**元素“\<元素名\>”的特性“\<特性名\>”无效。**  
  
 该特性名的拼写不正确或者无法由 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 识别。  
  
### 更正此错误  
  
-   检查特性名的拼写是否正确。  
  
-   检查项目文件是否已被修改或损坏。  如果项目已被修改或损坏，请用创建项目所用的 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 版本将项目打开，保存项目，然后尝试再次转换项目。  
  
## 请参阅  
 [项目文件架构参考](../msbuild/msbuild-project-file-schema-reference.md)