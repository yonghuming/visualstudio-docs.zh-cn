---
title: "使用规则集组合代码分析规则 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.codeanalysis.rulesets.learnmore
helpviewer_keywords: code analysis, rule sets
ms.assetid: ed0f3a2a-1516-42e2-92de-b8986dc75d42
caps.latest.revision: "36"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 44d64b7371f1b27afaa7796dc42d4b7864d20819
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="using-rule-sets-to-group-code-analysis-rules"></a>使用规则集对代码分析规则进行分组
当你配置中的代码分析[!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)]， [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)]，或[!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]，你可以从 Microsoft 内置列表中选择*规则集*。 规则集是标识目标的问题和特定条件的代码分析规则的逻辑分组。 例如，可以应用一种旨在扫描公开可用 Api 代码的规则集，也可以应用只包括最少建议规则的规则集。 你还可以应用包含所有规则的规则集。  
  
 你可以自定义规则集通过添加或删除规则，或者通过更改规则显示在**错误列表**窗口警告或错误。 自定义的规则集可以满足为特定的开发环境的需要。 自定义规则集时，规则集页将提供搜索和筛选工具来帮助你在过程中。  
  
## <a name="common-tasks"></a>常规任务  
  
|任务|相关内容|  
|----------|---------------------|  
|**获取的实例实践：**使用代码分析工具，以指定自定义规则集以查找并修复简单的.NET Framework 应用程序中的问题。|-   [演练： 配置和使用自定义规则集](../code-quality/walkthrough-configuring-and-using-a-custom-rule-set.md)|  
|**配置项目的代码分析：**选择现有规则设置为项目、 Web 站点或解决方案。|-   [如何： 配置托管的代码项目的代码分析](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)<br />-   [使用规则集指定运行的 c + + 规则](../code-quality/using-rule-sets-to-specify-the-cpp-rules-to-run.md)<br />-   [如何： 为 ASP.NET Web 应用程序配置代码分析](../code-quality/how-to-configure-code-analysis-for-an-aspnet-web-application.md)<br />-   [如何： 个解决方案中的多个项目指定规则集](../code-quality/how-to-specify-managed-code-rule-sets-for-multiple-projects-in-a-solution.md)|  
|**自定义规则集：**指定规则以应用于你的项目。|-   [创建自定义规则集](../code-quality/creating-custom-code-analysis-rule-sets.md)|  
|**了解内置规则集：**查看构成内置规则集的代码分析规则。|-   [代码分析规则集参考](../code-quality/code-analysis-rule-set-reference.md)|  
|**与 Team Foundation Server 集成的代码分析：** [!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)]签入策略让开发团队，以确保所有的代码签入行为满足一组通用的代码分析标准。|-   [如何： 将代码项目规则集与团队项目签入策略同步](../code-quality/how-to-synchronize-code-project-rule-sets-with-team-project-check-in-policy.md)|