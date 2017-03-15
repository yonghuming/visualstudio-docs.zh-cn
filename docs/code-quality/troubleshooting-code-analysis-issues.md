---
title: "代码分析问题疑难解答 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 61c7e44d-2780-4df5-9bcb-49e40c1152fc
caps.latest.revision: 5
author: "erickson-doug"
ms.author: "douge"
manager: "douge"
caps.handback.revision: 5
---
# 代码分析问题疑难解答
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

本主题包含以下 Visual Studio 代码分析问题的疑难解答信息。  
  
-   [Visual Studio 2010 规则集中的更改未反映在以前的 Visual Studio 版本中](#ChildRuleSetChangesInPreviousVersions)  
  
##  <a name="ChildRuleSetChangesInPreviousVersions"></a> Visual Studio 2010 规则集中的更改未反映在以前的 Visual Studio 版本中  
 如果在 [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] 中创建包含子规则集的规则集，那么，对该子规则集的更改可能不会应用于在使用 Visual Studio 早期版本的计算机上运行的代码分析。  若要解决此问题，必须强制重写父规则集，即包含子规则集的规则集。  
  
1.  打开 [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] 中的父规则集。  
  
2.  进行更改（如添加或移除规则），然后保存该规则集。  
  
3.  重新打开该规则集，撤消所做更改，然后再次保存该规则集。  
  
## 请参阅  
 [分析应用程序质量](../code-quality/analyzing-application-quality-by-using-code-analysis-tools.md)   
 [分析托管代码质量](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)   
 [使用规则集对代码分析规则进行分组](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)