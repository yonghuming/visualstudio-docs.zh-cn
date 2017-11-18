---
title: "代码分析签入策略的版本兼容性 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- version compatibility, code analysis check-in policy
- check-in policies, version compatibility for code analysis
ms.assetid: 1af376e3-3be7-4445-803b-76a858567a5b
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3b4504d723ed527c53827a5d4035b610e696abae
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="version-compatibility-for-code-analysis-check-in-policies"></a>代码分析签入策略的版本兼容性
如果你必须评估和创作代码分析签入策略使用的不同版本[!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)]，你必须知道方式间的差异[!INCLUDE[vstsTfsOrcasLong](../code-quality/includes/vststfsorcaslong_md.md)]和[!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)]评估签入策略。  
  
## <a name="version-compatibility-for-evaluating-check-in-policies"></a>版本兼容性评估签入策略  
  
-   代码分析签入策略中进行计算时[!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)]中, 存在的任何规则[!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)]但中不存在[!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)]将被忽略。  
  
-   代码分析签入策略中进行计算时[!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)]，专用于的所有新规则[!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)]将被忽略。  
  
-   如果代码分析签入策略指定规则程序集，[!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)]忽略指定的程序集，它无法识别的所有规则。  
  
-   如果代码分析签入策略指定规则程序集的[!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)]无法识别，显示一条消息。  
  
## <a name="version-compatibility-for-authoring-check-in-policies"></a>版本兼容性创作签入策略  
  
-   如果你通过创建代码分析签入策略[!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)]版本[!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)]，不能使用[!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)]版本[!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)]对其进行修改。 同样，[!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)]无法评估的策略。  
  
-   如果你通过创建代码分析签入策略[!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)]中[!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)]，你可以使用[!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)]中[!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)]修改它，并将策略还计算结果可以是通过[!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)]。 通过使用修改策略后[!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)]中[!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)]，你可以通过使用不能再编辑策略[!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)]中[!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)]。 [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] 可以评估策略，而不会出现因不匹配的强名称而引起的问题。  
  
-   若要创建具有同时适用于的规则设置的代码分析签入策略[!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)]和[!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)]，必须创建中的策略[!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)]、 进行需要的全部更改和保存策略。 如果对规则的更改仅在存在[!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)]，修改并保存在策略[!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)]。  
  
     保存中的策略后[!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)]，不再可以更改中存在的规则设置[!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)]仅。