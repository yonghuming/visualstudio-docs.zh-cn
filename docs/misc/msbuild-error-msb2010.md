---
title: "MSBuild 错误 MSB2010 | Microsoft Docs"
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
  - "MSBuild.MultipleLanguageNodesNotAllowed"
helpviewer_keywords: 
  - "MSB2010"
ms.assetid: 925cc6a7-1410-42c7-9c23-7d1797a705d9
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 错误 MSB2010
**元素 \<{1}\> 的子元素 \<{0}\> 无效。**  
  
 指定的元素不是有效的子元素。  
  
### 更正此错误  
  
-   检查指定元素的拼写。  
  
-   检查项目文件是否已被修改或损坏。  如果项目已被修改或损坏，请用创建项目所用的 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 版本将项目打开，保存项目，然后尝试再次转换项目。  
  
## 请参阅  
 [项目文件架构参考](../msbuild/msbuild-project-file-schema-reference.md)   
 [其他资源](../msbuild/additional-msbuild-resources.md)