---
title: "如何： 创建或更新标准代码分析签入策略 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.codeanalysis.policyeditor
helpviewer_keywords: code analysis, migrating check-in policy
ms.assetid: 458eb3b8-bb5e-4056-82b7-7079ce9c4089
caps.latest.revision: "29"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6396b698a5f4d2602c9969d6cab0422832b3e6dc
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-create-or-update-standard-code-analysis-check-in-policies"></a>如何：创建或更新标准代码分析签入策略
你可以要求，代码分析运行的所有代码项目的团队项目中使用代码分析签入策略。 需要代码分析可以提高签入代码库的代码的质量。  
  
> [!NOTE]
>  仅当你使用 Team Foundation Server 提供了此功能。  
  
 代码分析签入策略在团队项目设置中设置，并将应用于每个代码项目的团队项目中。 代码分析运行的代码项目的项目 (.xxproj) 文件中的代码项目的配置。 代码分析运行在本地计算机上执行。 中的团队项目设置的规则时启用代码分析签入策略、 签入代码项目中的文件必须在其最后一次编辑后编译和运行代码分析包含，至少必须执行的计算机上，changes 进行了。  
  
-   通过指定的签入策略设置对于托管代码，*规则集*，其中包含的代码分析规则子集。  
  
-   对于 C/c + + 代码，签入策略要求，所有代码分析规则会都运行。 你可以添加预处理器指令，以禁用在你的团队项目中的单个代码项目的特定规则。  
  
 指定用于托管代码签入策略后，团队成员可以同步其设置为对团队项目的策略设置的代码项目的代码分析。  
  
### <a name="to-open-the-check-in-policy-editor"></a>若要打开签入策略编辑器  
  
1.  在团队资源管理器，右键单击该团队项目名称，指向**团队项目设置**，然后单击**源代码管理**。  
  
2.  在**源代码管理**对话框中，选择**签入策略**选项卡。  
  
3.  执行下列操作之一：  
  
    -   单击**添加**来创建新的签入策略。  
  
    -   双击现有**代码分析**中项**策略类型**列表更改的策略。  
  
### <a name="to-set-policy-options"></a>若要设置策略选项  
  
-   选中或清除以下选项：  
  
    |选项|描述|  
    |------------|-----------------|  
    |**执行签入以只包含属于当前解决方案的文件。**|只能对解决方案和项目配置文件中指定的文件，可以运行代码分析。 此策略可确保所有代码都是解决方案的一部分进行都分析。|  
    |**强制实施 C/c + + 代码分析 （/分析）**|需要所有 C 或 c + + 项目用都生成 /analyze 编译器选项，它们可以签入前运行代码分析。|  
    |**为托管代码强制实施代码分析**|需要所有的托管的项目运行代码分析和生成，然后才能签入。|  
  
-  
  
### <a name="to-specify-a-managed-rule-set"></a>若要指定托管的规则设置  
  
-   从**运行此规则集**列表中，使用以下方法之一：  
  
    -   选择 Microsoft 标准规则集。  
  
    -   若要选择自定义规则集，请单击**\<选择规则集从源代码管理...>**，然后键入源代码管理浏览器中的规则集的版本控制路径。 版本控制路径的语法是：  
  
    -   **$/** `TeamProjectName` **/** `VersionControlPath`  
  
    -   有关如何创建和实现自定义签入策略规则的详细信息，请参阅[适用于托管代码实施自定义签入策略](../code-quality/implementing-custom-code-analysis-check-in-policies-for-managed-code.md)。  
  
## <a name="see-also"></a>另请参阅  
 [创建和使用代码分析签入策略](../code-quality/creating-and-using-code-analysis-check-in-policies.md)