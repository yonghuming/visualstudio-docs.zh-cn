---
title: "如何：配置托管代码项目的代码分析 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.codeanalysis.propertypages.csvb"
helpviewer_keywords: 
  - "代码分析, 选择规则集"
  - "代码分析, 规则集"
ms.assetid: 618f6ff3-db0e-46cb-b08d-dfa35e62c9e7
caps.latest.revision: 33
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 33
---
# 如何：配置托管代码项目的代码分析
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

在 [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)] 和 [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)] 中，可以从代码分析列表中选择用于管理代码项目的 *规则集*.  默认的规则集是“Microsoft 最少量建议规则”。  可以将另一个规则集应用于一个项目或解决方案中的所有项目。  
  
> [!NOTE]
>  有关如何为 ASP.NET Web 应用程序配置规则集的信息，请参见[如何：为 ASP.NET Web 应用程序配置代码分析](../code-quality/how-to-configure-code-analysis-for-an-aspnet-web-application.md)。  
  
### 为 .NET Framework 项目配置规则集  
  
1.  在**“解决方案资源管理器”**中，单击该项目。  
  
2.  在**“分析”**菜单上，单击**“为配置代码分析”**  *ProjectName* .  
  
3.  在**“配置”**和**“平台”**列表中，单击生成配置和目标平台。  
  
4.  若要在每次使用所选配置生成项目时运行代码分析，请选中**“生成时启用代码分析\(定义 CODE\_ANALYSIS 常量\)”**复选框。  还可以手动运行代码分析，具体方法是打开**“分析”**菜单，然后单击**“对运行代码分析”***ProjectName* .  
  
5.  默认情况下，代码分析不报告由外部工具自动生成的代码所产生的警告。  若要查看所生成代码所产生的警告，请清除**“取消显示由生成代码产生的结果”**复选框。  
  
    > [!NOTE]
    >  当所生成代码中的代码分析错误和警告出现在窗体和模板中时，此选项不会禁止显示它们。  可以查看和维护窗体或模板的源代码。  
  
6.  在**“运行此规则集”**列表中，执行以下操作之一：  
  
    -   单击要使用的规则集。  
  
    -   单击**\<浏览...\>** 指定列表外部的现有自定义规则集。  
  
    -   定义自定义规则集。  
  
         有关详细信息，请参阅[创建自定义规则集](../code-quality/creating-custom-code-analysis-rule-sets.md)。  
  
## 请参阅  
 [演练：配置和使用自定义规则集](../code-quality/walkthrough-configuring-and-using-a-custom-rule-set.md)