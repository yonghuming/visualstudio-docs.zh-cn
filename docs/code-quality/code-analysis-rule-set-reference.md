---
title: "代码分析规则集参考 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "代码分析, 规则集"
ms.assetid: 5874e854-e298-4d2e-bbe4-95e899d22587
caps.latest.revision: 43
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 43
---
# 代码分析规则集参考
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

当您在 [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)] 或 [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]中配置托管代码项目的代码分析时，将看到内置的 *规则集* 列表。  可以使用一 standar 规则集，也可以自定义规则集以适合您的项目要求。  
  
## 可用的规则集  
 下表列出了默认规则集：  
  
|||  
|-|-|  
|[“所有规则”规则集](../code-quality/all-rules-rule-set.md)|此规则集包含所有规则。  运行此规则集可能导致报告大量警告。  使用此规则集可获得代码中所有问题的概况。  这可帮助您确定最适合为您的项目运行的更为专注的规则集。|  
|[托管代码的“基本更正规则”规则集](../code-quality/basic-correctness-rules-rule-set-for-managed-code.md)|这些规则重点针对在使用框架 API 时出现的逻辑错误和常见错误。  包含此规则集以便在由最少量建议规则所报告的警告列表中进行扩展。|  
|[托管代码的“基本设计准则规则”规则集](../code-quality/basic-design-guideline-rules-rule-set-for-managed-code.md)|这些规则主要用于强制实施最佳做法，使您的代码易于理解和使用。  如果项目包含库代码或者您希望强制实施最佳做法以获得易于维护的代码，请包含此规则集。|  
|[托管代码的“扩展的更正规则”规则集](../code-quality/extended-correctness-rules-rule-set-for-managed-code.md)|这些规则基于基本正确性规则进行扩展，以便最大程度地报告逻辑和框架使用错误。  将重点关注某些特定的方案，如 COM 互操作和 Mobile 应用程序。  如果其中的某个方案适用于您的项目或在您的项目中找到其他问题，请考虑包含此规则集。|  
|[托管代码的“扩展的设计准则规则”规则集](../code-quality/extended-design-guidelines-rules-rule-set-for-managed-code.md)|这些规则基于基本设计准则规则进行扩展，以便最大程度地报告可使用性和可维护性问题。  其中尤其侧重于命名准则。  如果您的项目包含库代码或者您要强制实施用于编写可维护代码的最高标准，请考虑包含此规则集。|  
|[托管代码的“全球化规则”规则集](../code-quality/globalization-rules-rule-set-for-managed-code.md)|在不同的语言、区域设置和区域性中使用这些规则时，它们主要针对阻止应用程序中的数据正常显示的问题。  如果对您的应用程序进行本地化或全球化，请包含此规则集。|  
|[托管代码的“托管最少量规则”规则集](../code-quality/managed-minimun-rules-rule-set-for-managed-code.md)|这些规则重点针对代码中代码分析对其最为准确的最关键问题。这些规则为数不多，只可在某些特定 Visual Studio 版本中运行。对于其他 Visual Studio 版本，请使用 MinimumRecommendedRules.ruleset。|  
|[托管代码的“托管建议规则”规则集](../code-quality/managed-recommended-rules-rule-set-for-managed-code.md)|这些规则专注于代码中最关键的问题，包括潜在的安全漏洞、应用程序崩溃和其他重要的逻辑和设计错误。  您应在为项目创建的任何自定义规则集中包含此规则集。|  
|[“混合最少量规则”规则集](../code-quality/mixed-minimum-rules-rule-set.md)|这些规则重点关注支持公共语言运行时的 C\+\+ 项目中的最关键问题，包括潜在安全漏洞和应用程序崩溃。  应在您为支持公共语言运行时的 C\+\+ 项目创建的任何自定义规则集中包含此规则集。|  
|[“混合建议规则”规则集](../code-quality/mixed-recommended-rules-rule-set.md)|这些规则重点针对支持公共语言运行时的 C\+\+ 项目中的最常见问题和最关键问题，其中包括潜在安全漏洞、应用程序崩溃以及其他重要的逻辑错误和设计错误。  应在您为支持公共语言运行时的 C\+\+ 项目创建的任何自定义规则集中包含此规则集。对于此规则集，应当使用 Visual Studio 专业版及更高版本进行配置。|  
|[“本机最少量规则”规则集](../code-quality/native-minimum-rules-rule-set.md)|这些规则重点关注本机代码中的最关键问题，包括潜在安全漏洞和应用程序崩溃。  应在您为本机项目创建的任何自定义规则集中包含此规则集。|  
|[“本机建议规则”规则集](../code-quality/native-recommended-rules-rule-set.md)|这些规则重点针对本机代码中的最关键问题和最常见问题，其中包括潜在安全漏洞和应用程序崩溃。应在您为本机项目创建的任何自定义规则集中包含此规则集。此规则集应与 Visual Studio 专业版及更高版本配合使用。|  
|[托管代码的“安全规则”规则集](../code-quality/security-rules-rule-set-for-managed-code.md)|此规则包含所有 Microsoft 安全性规则。  包含此规则集可最大程度地报告潜在的安全问题。|