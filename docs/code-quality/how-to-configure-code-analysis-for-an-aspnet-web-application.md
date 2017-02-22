---
title: "如何：为 ASP.NET Web 应用程序配置代码分析 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.codeanalysis.propertypages.asp"
ms.assetid: b3000b31-fd9d-489e-81a2-a4bee49453ba
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 如何：为 ASP.NET Web 应用程序配置代码分析
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

在 [!INCLUDE[vsPreShort](../code-quality/includes/vspreshort_md.md)]和 [!INCLUDE[vsUltShort](../code-quality/includes/vsultshort_md.md)]中，您可以从代码分析规则集列表中选出要应用于 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web 应用程序的规则集。  默认的规则集是“Microsoft 最少量建议规则”。  可以选择另一个规则集应用于网站。  
  
### 为 ASP.NET 页框架项目配置规则集÷  
  
1.  在**“解决方案资源管理器”**中选择网站。  
  
2.  在**“分析”**菜单上，单击**“为网站配置代码分析”**。  
  
3.  如果您选择了解决方案，并且所选解决方案中包含多个项目，请从**“配置”**和**“平台”**列表中选择生成配置和目标操作系统。  
  
4.  对于解决方案中的每个项目，请单击**“规则集”**列，然后单击要运行的规则集的名称。  
  
5.  默认情况下，代码分析会对解决方案中的所有项目运行。  若要为特定项目禁用或启用代码分析，请按照以下步骤操作：  
  
    1.  右击项目名称，然后单击“属性”。  
  
    2.  选中或清除**“启用代码分析”**复选框。  还可以手动运行代码分析，方法是从**“分析”**菜单中选择**“对网站运行代码分析”**。  
  
6.  在**“运行此规则集”**下拉列表中，按照以下步骤操作：  
  
    -   选择要使用的规则集。  
  
    -   单击**\<浏览...\>”\>**指定列表外部的现有自定义规则集。  
  
    -   定义自定义规则集。  有关详细信息，请参阅[创建自定义规则集](../code-quality/creating-custom-code-analysis-rule-sets.md)。