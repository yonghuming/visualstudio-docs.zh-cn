---
title: "如何： 设置 C/c + + 项目的代码分析属性 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.codeanalysis.propertypages.native
- VC.Project.VCCLCompilerTool.EnablePrefast
- VC.Project.VCFxCopTool.EnablePREfast
- VC.Project.VCFxCopTool.IgnoreGeneratedCode
helpviewer_keywords:
- properties, C/C++ Code Analysis
- properties, Code Analysis
- code analysis properties
- C/C++ code analysis properties
ms.assetid: 7af52097-6d44-4785-9b9f-43b7a7d447d7
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b2ad22eccb561bf58ee845d58268620aad778a20
ms.sourcegitcommit: fb751e41929f031d1a9247bc7c8727312539ad35
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/15/2017
---
# <a name="how-to-set-code-analysis-properties-for-cc-projects"></a>如何：设置 C/C++ 项目的代码分析属性
你可以配置使用哪些规则的代码分析工具来分析你的项目的每个配置中的代码。 此外，你可以指示代码分析，以禁止显示警告的代码与已生成并由第三方工具添加到你的项目。  
  
## <a name="code-analysis-property-page"></a>代码分析属性页  
 **代码分析**属性页包含一个项目的所有代码分析配置设置。 若要打开的项目中的代码分析属性页**解决方案资源管理器**，右键单击项目，然后单击**属性**。 接下来，展开**配置属性**和选择**代码分析**选项卡。  
  
## <a name="project-configuration-and-platform"></a>项目配置和平台  
 **配置**列表和**平台**列表，可以将不同的代码分析设置应用于不同的项目配置和平台组合。 例如，你可以指示代码分析，以将一组规则应用于用于调试的项目生成和生成一组不同的版本。  
  
## <a name="enabling-code-analysis"></a>启用代码分析  
 你可以决定是否启用通过选择为你的项目代码分析**启用代码分析的 C/c + + 生成**。 结合**配置**列表中，你无法，例如，决定禁用调试版本并启用为发布版本的代码分析。  
  
 如果你的项目包含托管的代码，你可以决定是否要启用或禁用通过选择代码分析**生成时启用代码分析**。  
  
 代码分析旨在帮助您提高代码质量并避免常见的问题。 因此，请仔细考虑是否禁用代码分析。 通常，最好禁用规则集或你不希望的单个规则应用到你的项目。  
  
## <a name="generated-code"></a>生成的代码  
 开发人员经常使用工具来帮助快速开发应用程序。 这些工具可以生成添加到项目的代码。 你可能想要看到生成的代码中的代码分析发现的规则冲突。 但是，你可能不想以查看它们，如果你不想要维护代码。  
  
 **禁止显示所生成代码的结果**上的复选框**常规**属性页中，可以选择是否想要查看从由第三方工具生成的托管代码的代码分析警告.  
  
## <a name="rule-sets"></a>规则集  
 如果你的项目包含托管的代码，你可以选择通过选择规则集从应用中的代码分析规则**运行此规则集**列表。  
  
## <a name="see-also"></a>另请参阅  
 [分析托管的代码质量](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)   
 [C/C++ 代码分析警告](../code-quality/code-analysis-for-c-cpp-warnings.md)