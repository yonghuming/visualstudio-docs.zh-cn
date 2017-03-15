---
title: "创建和使用代码分析签入策略 | Microsoft Docs"
ms.custom: ""
ms.date: "12/12/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "代码分析, 签入策略"
ms.assetid: 3fa5a849-e05f-4e31-8ba3-b014c889d94d
caps.latest.revision: 39
caps.handback.revision: 39
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 创建和使用代码分析签入策略
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

当您使用 Team Foundation 版本控制 \(TFVC\) 时，可以为团队项目中的 .NET Framework 和本机 \(C\/C\+\+\) 代码项目创建一个代码分析签入策略。  代码分析签入策略可用于控制和改进签入到代码库中的代码的质量。  
  
 如果本地生成是最新的，并且已对最新的源文件运行了代码分析，则会通过策略。  在代码项目中启用的代码分析规则至少必须包含与团队项目签入策略中定义的代码分析规则相同的规则。  已在团队项目设置中指定为错误的规则在代码项目中也必须指定为错误  
  
> [!IMPORTANT]
>  代码分析签入策略不能应用于网站项目。  它们可以应用于 Web 应用程序项目。  
  
 通过使用 [!INCLUDE[esprscc](../code-quality/includes/esprscc_md.md)]的团队项目设置创建代码分析签入策略。  签入策略是为团队项目指定和实施的，但代码分析运行是为本地开发计算机上的单个代码项目配置和运行的。  本节介绍如何为团队项目指定代码分析签入策略，以及如何为托管代码实现自定义代码分析策略。  
  
## 本节内容  
 [如何：创建或更新标准代码分析签入策略](../Topic/How%20to:%20Create%20or%20Update%20Standard%20Code%20Analysis%20Check-in%20Policies.md)  
 说明用于为团队项目设置和修改代码分析策略的步骤。  
  
 [对托管代码实施自定义签入策略](../code-quality/implementing-custom-code-analysis-check-in-policies-for-managed-code.md)  
 说明用于为团队项目的签入策略创建自定义规则集的步骤，以及用于将团队项目的代码项目与签入策略同步的步骤。  
  
 [代码分析签入策略的版本兼容性](../code-quality/version-compatibility-for-code-analysis-check-in-policies.md)  
 说明 [!INCLUDE[vstsLong](../code-quality/includes/vstslong_md.md)] 不同版本之间的代码分析签入兼容性问题。  
  
 [如何：自定义代码分析字典](../Topic/How%20to:%20Customize%20the%20Code%20Analysis%20Dictionary.md)  
 说明如何将单词和标记添加到代码分析命名规则所引用的字典中。  
  
## 相关章节  
 [Set and Enforce Quality Gates](../Topic/Set%20and%20Enforce%20Quality%20Gates.md)  
  
 [利用团队项目签入策略提高代码质量](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md)