---
title: "使用代码分析来分析托管的代码质量 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- code analysis,managed code
- managed code analyis
ms.assetid: 68510a55-da51-4381-81a5-0feba76b8b4f
caps.latest.revision: "24"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 69cb1ed9c5c8da2ae511d73de45a0567d61236dd
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="analyzing-managed-code-quality-by-using-code-analysis"></a>使用代码分析来分析托管代码质量
你可以在 Visual Studio 中使用代码分析工具发现代码中的潜在问题，如不安全的数据访问、使用冲突和设计问题。 代码分析适用于.NET Framework、 本机 （C 和 c + +） 和数据库应用程序。 针对托管代码的代码分析将组织中的规则*规则集*面向特定编码问题。  
  
## <a name="common-tasks"></a>常规任务  
  
|常规任务|支持内容|  
|------------------|------------------------|  
|**获取的实例实践：**通过更正简单的.NET Framework 应用程序中存在的缺陷了解代码分析的基础知识。|-   [演练： 对托管代码进行代码缺陷分析](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md)|  
|**配置项目的代码分析：**规则针对托管代码组织到指定的目标特定区域，如安全性和设计的规则集。 你可以使用的 Microsoft 标准规则设置或创建你自己之一。|-   [代码分析托管的代码概述](../code-quality/code-analysis-for-managed-code-overview.md)<br />-   [使用规则集组合代码分析规则](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)<br />-   [使用 SuppressMessage 特性禁止显示警告](../code-quality/suppress-warnings-by-using-the-suppressmessage-attribute.md)|  
|**运行代码分析：**可以指定代码分析，以自动生成的项目配置，每次运行，你可以手动运行代码分析的项目。|-   [如何： 启用和禁用自动代码分析](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)<br />-   [如何： 手动运行代码分析](../code-quality/how-to-run-code-analysis-manually-for-managed-code.md)|  
|**分析代码分析结果：**代码分析窗口中将列出代码分析警告和错误。 可以选择警告或错误的标题以显示有关该警告的其他信息，同时突出显示引发规则的源代码行。 可以选择警告 ID 以显示 MSDN Library 的详细信息，其中包含关于如何解决问题的信息和示例。|-   [如何： 查看托管的代码缺陷](../code-quality/how-to-view-managed-code-defects.md)<br />-   [托管的代码的警告的的代码分析](../code-quality/code-analysis-for-managed-code-warnings.md)<br />-   [按 checkid 排列的警告](../code-quality/code-analysis-warnings-for-managed-code-by-checkid.md)<br />-   [匿名方法和代码分析](../code-quality/anonymous-methods-and-code-analysis.md)|  
|**与你开发生命周期集成代码分析：**中执行的签入策略[!INCLUDE[esprscc](../code-quality/includes/esprscc_md.md)]启用开发团队，以确保所有代码签入行为满足一组通用的代码分析标准。 创建代码分析规则冲突的工作项是可以在错误列表窗口中执行的简单过程。|-   [利用团队项目签入策略提高代码质量](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md)<br />-   [如何： 将代码项目规则集与团队项目签入策略同步](../code-quality/how-to-synchronize-code-project-rule-sets-with-team-project-check-in-policy.md)<br />-   [如何： 为托管的代码缺陷创建工作项](../code-quality/how-to-create-a-work-item-for-a-managed-code-defect.md)|