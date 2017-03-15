---
title: "使用规则集对代码分析规则进行分组 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.codeanalysis.rulesets.learnmore"
helpviewer_keywords: 
  - "代码分析, 规则集"
ms.assetid: ed0f3a2a-1516-42e2-92de-b8986dc75d42
caps.latest.revision: 36
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 36
---
# 使用规则集对代码分析规则进行分组
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

在 [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)]， [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)]或[!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]中配置代码分析时，可以从 Microsoft 内置 *规则集*列表中进行选择。  规则集是代码分析规则的逻辑组合，用于确定目标问题和特定条件。  例如，您可以应用用于扫描公开 API 的代码的规则集，也可以应用只包括最少建议规则的规则集。  您还可以应用包含所有规则的规则集。  
  
 通过添加或删除规则，或者更改规则以使其在**“错误列表”**窗口中显示为警告或错误，可以对规则集进行自定义。  自定义规则集可满足特定开发环境的需要。  在自定义规则集的过程中，规则集页中的搜索和筛选工具可为您提供帮助。  
  
## 常规任务  
  
|任务|相关内容|  
|--------|----------|  
|**进行动手实践：**使用代码分析工具指定自定义规则集，以在简单的 .NET Framework 应用程序中找到并修复问题。|-   [演练：配置和使用自定义规则集](../code-quality/walkthrough-configuring-and-using-a-custom-rule-set.md)|  
|**为项目配置代码分析：**为项目、网站或解决方案选择一个现有规则集。|-   [如何：配置托管代码项目的代码分析](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)<br />-   [使用规则集指定要运行的 C\+\+ 规则](../code-quality/using-rule-sets-to-specify-the-cpp-rules-to-run.md)<br />-   [如何：为 ASP.NET Web 应用程序配置代码分析](../code-quality/how-to-configure-code-analysis-for-an-aspnet-web-application.md)<br />-   [如何：为解决方案中的多个项目指定规则集](../code-quality/how-to-specify-managed-code-rule-sets-for-multiple-projects-in-a-solution.md)|  
|**自定义规则集：**指定要应用于项目的规则。|-   [创建自定义规则集](../code-quality/creating-custom-code-analysis-rule-sets.md)|  
|**了解内置规则集：**查看构成内置规则集的代码分析规则。|-   [代码分析规则集参考](../code-quality/code-analysis-rule-set-reference.md)|  
|**将代码分析与 Team Foundation Server 集成：利用**  [!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)] 签入策略，开发团队可以确保所有代码签入都符合一组常用的代码分析标准。|-   [如何：将代码项目规则集与团队项目签入策略同步](../code-quality/how-to-synchronize-code-project-rule-sets-with-team-project-check-in-policy.md)|