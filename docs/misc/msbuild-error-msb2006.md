---
title: "MSBuild 错误 MSB2006 | Microsoft Docs"
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
  - "MSBuild.UnrecognizedElement"
helpviewer_keywords: 
  - "MSB2006"
ms.assetid: 89dc1b89-1621-46bc-9fe6-6d98cbcbebc8
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 错误 MSB2006
**项目文件未包含根元素 \<{0}\>。**  
  
 根元素名称拼写不正确或者无法由 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 识别。  
  
### 更正此错误  
  
-   检查元素名称的拼写。  
  
-   检查项目文件是否已被修改或损坏。  如果项目已被修改或损坏，请用创建项目所用的 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 版本将项目打开，保存项目，然后尝试再次转换项目。  
  
## 请参阅  
 [项目文件架构参考](../msbuild/msbuild-project-file-schema-reference.md)   
 [其他资源](../msbuild/additional-msbuild-resources.md)