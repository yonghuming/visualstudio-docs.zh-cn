---
title: "使用代码分析来分析托管代码质量 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "代码分析，托管代码"
  - "托管代码分析"
ms.assetid: 68510a55-da51-4381-81a5-0feba76b8b4f
caps.latest.revision: 24
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 24
---
# 使用代码分析来分析托管代码质量
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可以在 Visual Studio 中使用代码分析工具发现代码中的潜在问题，如不安全的数据访问、使用冲突和设计问题。  代码分析可处理 .NET Framework、本机（C 和 C\+\+）和数据库应用程序。  针对托管代码的代码分析在以特定编码问题为目标的规则集中组织各种规则。  
  
## 常规任务  
  
|常规任务|支持内容|  
|----------|----------|  
|**亲身实践：**通过更正简单 .NET Framework 应用程序中的缺陷，了解代码分析的基本知识。|-   [演练：对托管代码进行代码缺陷分析](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md)|  
|**为项目配置代码分析：**托管代码的各种规则组织为以特定领域（如安全和设计）为目标的规则集。  可以使用某个 Microsoft 标准规则集或创建自己的规则集。|-   [托管代码的代码分析概述](../code-quality/code-analysis-for-managed-code-overview.md)<br />-   [使用规则集对代码分析规则进行分组](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)<br />-   [使用 SuppressMessage 特性禁止显示警告](../code-quality/suppress-warnings-by-using-the-suppressmessage-attribute.md)|  
|**运行代码分析：**可以指定在每次生成项目配置时自动运行代码分析，也可以手动对项目运行代码分析。|-   [如何：启用和禁用自动代码分析](../Topic/How%20to:%20Enable%20and%20Disable%20Automatic%20Code%20Analysis%20for%20Managed%20Code.md)<br />-   [如何：手动运行代码分析](../code-quality/how-to-run-code-analysis-manually-for-managed-code.md)|  
|**分析代码分析结果：** “错误列表”窗口下列出了代码分析产生的警告和错误。  可以选择警告或错误标题显示有关该警告的附加信息同时显示并高亮所符合的源代码行。  可以选择警告 ID 显示 MSDN 中包含解决问题的信息和示例的详细信息。|-   [如何：查看托管代码缺陷](../code-quality/how-to-view-managed-code-defects.md)<br />-   [托管代码的代码分析警告](../code-quality/code-analysis-for-managed-code-warnings.md)<br />-   [按 CheckId 排列的警告](../code-quality/code-analysis-warnings-for-managed-code-by-checkid.md)<br />-   [匿名方法和代码分析](../code-quality/anonymous-methods-and-code-analysis.md)|  
|**将代码分析与开发生命周期集成在一起：**利用 [!INCLUDE[esprscc](../code-quality/includes/esprscc_md.md)]中的签入策略，开发团队可以确保所有代码签入都符合一组常用的代码分析标准。  为代码分析规则冲突创建工作项是一个可在“错误列表”窗口中执行的简单过程。|-   [利用团队项目签入策略提高代码质量](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md)<br />-   [如何：将代码项目规则集与团队项目签入策略同步](../code-quality/how-to-synchronize-code-project-rule-sets-with-team-project-check-in-policy.md)<br />-   [如何：为托管代码缺陷创建工作项](../code-quality/how-to-create-a-work-item-for-a-managed-code-defect.md)|