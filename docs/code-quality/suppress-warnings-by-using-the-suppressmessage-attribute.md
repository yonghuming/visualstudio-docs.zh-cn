---
title: "使用 SuppressMessage 特性禁止显示警告 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCFxCopTool.InputAssemblyFileName"
  - "VC.Project.VCFxCopTool.FxCopModuleSuppressionsFile"
  - "VC.Project.VCFxCopTool.FxCopUseTypeNameInSuppression"
  - "VC.Project.VCFxCopTool.OutputFile"
helpviewer_keywords: 
  - "代码分析, 禁止显示源"
  - "代码分析, SuppressMessage 特性"
  - "禁止显示源"
  - "SuppressMessage 特性"
ms.assetid: a38c57a2-d29d-43c0-84ff-3308b2484ce6
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 使用 SuppressMessage 特性禁止显示警告
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

通常最好指出警告不适用于代码，这样小组成员可以知道代码已经过检查并已决定取消警告。  利用源代码中禁止显示 \(ISS\) 功能，开发人员可以将禁止显示警告的特性放在生成该警告的位置附近。  可以将 ISS 特性直接添加到源文件中，也可以使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE 中的快捷菜单。  
  
## 本节内容  
  
|||  
|-|-|  
|[“源代码中禁止显示”概述](../code-quality/in-source-suppression-overview.md)|了解 ISS 以及如何在代码中使用它。|  
|[如何：使用菜单项禁止显示警告](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md)|了解如何使用快捷菜单在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE 中禁止显示警告。|  
  
## 相关章节  
 [分析托管代码质量](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)