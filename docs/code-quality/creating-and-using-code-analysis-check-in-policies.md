---
title: "创建和使用代码分析签入策略 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: code analysis, check-in policies
ms.assetid: 3fa5a849-e05f-4e31-8ba3-b014c889d94d
caps.latest.revision: "39"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b16b7e9f4dba55babfc7ad2ad90affe0ca93c508
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="creating-and-using-code-analysis-check-in-policies"></a>创建和使用代码分析签入策略
当你使用 Team Foundation 版本控制 (TFVC) 时，你可以为.NET Framework 和本机 （C/c + +） 代码项目的团队项目中创建代码分析签入策略。 可以使用代码分析签入策略以控制和改进的签入代码库的代码质量。  
  
 本地生成是最新，并且已最新的源代码文件上运行代码分析时，将通过策略。 在最低限度上，在代码项目中启用代码分析规则必须包含与在团队项目签入策略中定义的那些相同的规则。 已指定为团队项目设置中的错误的规则也必须指定为代码项目中的错误  
  
> [!IMPORTANT]
>  代码分析签入策略无法应用于网站项目。 它们可以应用于 web 应用程序项目。  
  
 通过使用团队项目设置的创建代码分析签入策略[!INCLUDE[esprscc](../code-quality/includes/esprscc_md.md)]。 签入策略指定并强制实施的团队项目，但配置并在本地开发计算机上运行各个代码项目的代码分析运行。 本部分介绍如何指定代码分析签入策略为团队项目以及如何实现托管代码的自定义代码分析策略。  
  
## <a name="in-this-section"></a>本节内容  
 [如何：创建或更新标准代码分析签入策略](../code-quality/how-to-create-or-update-standard-code-analysis-check-in-policies.md)  
 说明用于设置和修改为团队项目代码分析策略的步骤。  
  
 [对托管代码实施自定义签入策略](../code-quality/implementing-custom-code-analysis-check-in-policies-for-managed-code.md)  
 说明使用来创建自定义规则为团队项目签入策略设置，并与签入策略同步的团队项目的代码项目的步骤。  
  
 [代码分析签入策略的版本兼容性](../code-quality/version-compatibility-for-code-analysis-check-in-policies.md)  
 说明的不同版本之间的代码分析签入兼容性问题[!INCLUDE[vstsLong](../code-quality/includes/vstslong_md.md)]。  
  
 [如何：自定义代码分析字典](../code-quality/how-to-customize-the-code-analysis-dictionary.md)  
 说明如何将单词和令牌添加到代码分析命名规则中引用的字典。  
  
## <a name="related-sections"></a>相关章节  
 [设置并强制实施质量要求](http://msdn.microsoft.com/Library/bdc5666e-6cf0-45b2-a0a1-133c3f61e852)  
  
 [利用团队项目签入策略提高代码质量](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md)