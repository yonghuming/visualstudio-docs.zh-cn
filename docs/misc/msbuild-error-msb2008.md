---
title: "MSBuild 错误 MSB2008 | Microsoft Docs"
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
  - "MSBuild.UnrecognizedChildElement"
helpviewer_keywords: 
  - "MSB2008"
ms.assetid: 3c2afda0-a116-4b2f-af0c-c0f0d1541325
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 错误 MSB2008
**此 Visual Studio 项目系统无法转换“{0}”项目。  它只能用于转换 C\# 和 VB 客户端项目。**  
  
 只有有效的 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 和 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 项目可以使用 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 进行转换。  
  
### 更正此错误  
  
-   如果项目为 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 或 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 项目，请检查项目文件是已修改还是已损坏。  如果项目已被修改或损坏，请用创建项目所用的 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 版本将项目打开，保存项目，然后尝试再次转换项目。  
  
-   如果项目不是 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 或 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 项目，请使用适当的工具转换项目。  
  
## 请参阅  
 [其他资源](../msbuild/additional-msbuild-resources.md)