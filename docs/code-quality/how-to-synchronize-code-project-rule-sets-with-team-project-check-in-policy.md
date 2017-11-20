---
title: "如何： 将代码项目规则集与团队项目签入策略同步 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.codeanalysis.selecttfsruleset
ms.assetid: 9b02f934-2db6-41ec-aaff-9c31ceec2f04
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: de3a7bfaccec45dc6b7fce1def45a6e6de8e75f2
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-synchronize-code-project-rule-sets-with-team-project-check-in-policy"></a>如何：将代码项目规则集与团队项目签入策略同步
通过指定至少包含在规则集签入策略中指定的规则的规则集同步到团队项目的签入策略的代码项目的代码分析设置。 开发主管可以通知你的名称和位置的规则集签入策略。 你可以使用以下选项之一以确保项目的代码分析使用的是正确的规则集：  
  
-   如果签入策略使用 Microsoft 内置规则集之一，打开代码项目的属性对话框、 显示代码分析页和选择的代码项目设置的代码分析页上设置的规则。 标准规则集将随 Visual Studio 自动安装 Microsoft 设置为只读的并且不应进行编辑。 如果不编辑规则集，可保证中的策略和本地规则集的规则，以匹配。  
  
-   如果签入策略使用自定义规则集，请在版本控制中创建的本地副本执行 get 操作的规则集文件。 在代码项目的代码分析设置，然后指定该本地位置。 保证规则都与匹配; 如果的规则集签入策略是最新。  
  
     如果您将版本控制位置映射到在与团队项目根关系与你的代码项目相同的本地文件夹时，规则的位置将由使用相对路径。 相对路径可确保代码分析的代码项目设置，可以移动到其他计算机。  
  
-   自定义代码项目的签入策略设置的规则的副本。 请确保新的规则集包含在签入策略中的所有规则和你想要包括的任何其他规则。 必须确保你的规则集的规则集签入策略中包括的所有规则。  
  
### <a name="to-specify-a-microsoft-standard-rule-set"></a>若要指定 Microsoft 标准规则设置  
  
1.  在**解决方案资源管理器**，右键单击代码项目，然后单击**属性**。  
  
2.  单击**代码分析**。  
  
3.  在**运行此规则集**列表中，单击签入策略规则集。  
  
### <a name="to-specify-a-custom-check-in-policy-rule-set"></a>若要指定自定义签入策略规则设置  
  
1.  如果有必要，请执行 get 操作指定签入策略的规则集文件。  
  
2.  在**解决方案资源管理器**，右键单击代码项目，然后单击**属性**。  
  
3.  单击**代码分析**。  
  
4.  在**运行此规则集**列表中，单击**\<浏览 … >**。  
  
5.  在**打开**对话框框中，指定签入策略规则集文件。  
  
### <a name="to-create-a-custom-rule-set-for-a-code-project"></a>若要创建自定义规则设置为代码项目  
  
1.  按照本主题以选择项目设置对话框的代码分析页上的团队项目签入策略前面的过程之一。  
  
2.  单击**打开**。  
  
3.  添加或删除通过使用规则集编辑器的规则。  
  
     有关详细信息，请参阅[创建自定义规则集](../code-quality/creating-custom-code-analysis-rule-sets.md)。  
  
4.  保存已修改的规则设置为本地计算机上的.ruleset 文件或到 UNC 路径。  
  
5.  打开代码项目中，属性对话框并显示**代码分析**页。  
  
6.  在**运行此规则集**列表中，单击**\<浏览 … >**。  
  
7.  在**打开**对话框框中，指定规则集文件。