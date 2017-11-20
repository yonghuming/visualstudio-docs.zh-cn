---
title: "代码分析规则集参考 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: code analysis, rule sets
ms.assetid: 5874e854-e298-4d2e-bbe4-95e899d22587
caps.latest.revision: "43"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 5a0f290fa42a04ddf60a49282d2f350111076ab0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="code-analysis-rule-set-reference"></a>代码分析规则集参考
当你配置托管代码分析的代码项目中的[!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)]， [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)]，或[!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]将向你提供的内置列表*规则集*。 你可以使用某一标准规则集，或者你可以自定义规则集以适合您项目的要求。  
  
## <a name="available-rule-sets"></a>可用的规则集  
 下表列出了默认规则集：  
  
|||  
|-|-|  
|[“所有规则”规则集](../code-quality/all-rules-rule-set.md)|此规则集包含所有规则。 运行此规则集可能会导致大量的报告的警告。 使用此规则集要全面了解的所有问题在代码中。 这可以帮助你确定哪个更有针对性的规则集是最适合运行你的项目。|  
|[托管代码的“基本更正规则”规则集](../code-quality/basic-correctness-rules-rule-set-for-managed-code.md)|这些规则侧重于逻辑错误和在 framework Api 的使用情况中进行的常见错误。 包含此规则集以展开上的报告的最少量建议规则的警告的列表。|  
|[托管代码的“基本设计准则规则”规则集](../code-quality/basic-design-guideline-rules-rule-set-for-managed-code.md)|这些规则侧重于实施最佳做法，以使代码更易于了解和使用。 包含此规则集如果你的项目包括库代码，或者如果你想要强制执行的代码更易于维护的最佳实践。|  
|[托管代码的“扩展的更正规则”规则集](../code-quality/extended-correctness-rules-rule-set-for-managed-code.md)|这些规则展开基本更正规则，以最大化报告逻辑和 framework 用法错误。 侧重于特定的方案，例如 COM 互操作和移动应用程序。 请考虑加入此规则集如果其中一种情形适用于你的项目，或在你的项目中查找其他问题。|  
|[托管代码的“扩展的设计准则规则”规则集](../code-quality/extended-design-guidelines-rules-rule-set-for-managed-code.md)|在基本设计准则规则，以最大化报告的可用性和可维护性问题上展开这些规则。 额外的强调置于命名规则。 考虑包含此设置，如果你的项目包括库代码，或者如果你想要强制实施有关编写更容易维护的代码最高标准的规则。|  
|[托管代码的“全球化规则”规则集](../code-quality/globalization-rules-rule-set-for-managed-code.md)|这些规则侧重于防止在不同语言、 区域设置中和区域性中使用时无法正确显示应用程序中的数据的问题。 包含此规则集如果本地化或全球化你的应用程序。|  
|[托管最少量规则的规则集托管代码](../code-quality/managed-minimun-rules-rule-set-for-managed-code.md)|这些规则专注于你的代码分析是最准确的代码中的最关键问题。  这些规则是小数并且它们应仅在有限的 Visual Studio 版本中运行。  与其他 Visual Studio 版本使用 MinimumRecommendedRules.ruleset。|  
|[托管代码的“托管建议规则”规则集](../code-quality/managed-recommended-rules-rule-set-for-managed-code.md)|这些规则侧重于在代码中，包括潜在的安全漏洞、 应用程序崩溃和其他重要的逻辑和设计错误的最关键问题。 应包括在任何自定义规则集中设置为你的项目创建此规则。|  
|[“混合最少量规则”规则集](../code-quality/mixed-minimum-rules-rule-set.md)|这些规则侧重于支持公共语言运行时，包括潜在安全漏洞和应用程序崩溃在 c + + 项目中的最关键问题。 应包括在任何自定义规则集中设置为 c + + 项目支持公共语言运行时创建此规则。|  
|[“混合建议规则”规则集](../code-quality/mixed-recommended-rules-rule-set.md)|这些规则侧重于支持公共语言运行时，包括潜在的安全漏洞、 应用程序崩溃和其他重要的逻辑和设计错误在 c + + 项目中的最常见和关键问题。 应包括在任何自定义规则集中设置为 c + + 项目支持公共语言运行时创建此规则。  此规则集被设计与 Visual Studio 专业版和更高版本进行配置。|  
|[“本机最少量规则”规则集](../code-quality/native-minimum-rules-rule-set.md)|这些规则侧重于在本机代码中，包括潜在安全漏洞和应用程序崩溃的最关键问题。 应在你为本机项目创建的任何自定义规则集中包含此规则集。|  
|[“本机建议规则”规则集](../code-quality/native-recommended-rules-rule-set.md)|这些规则侧重于在本机代码中，包括潜在安全漏洞和应用程序崩溃的最关键和常见的问题。  应在你为本机项目创建的任何自定义规则集中包含此规则集。  此规则集用于处理与 Visual Studio 专业版和更高版本。|  
|[托管代码的“安全规则”规则集](../code-quality/security-rules-rule-set-for-managed-code.md)|此规则集包含所有 Microsoft 安全规则。 包含此规则集以最大化的报告的潜在安全问题数。|
