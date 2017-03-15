---
title: "如何：为解决方案中的多个项目指定托管代码规则集 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.codeanalysis.propertypages.solution"
ms.assetid: 92dc3250-a010-4396-b515-f03a0b30cd2a
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 12
---
# 如何：为解决方案中的多个项目指定托管代码规则集
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

默认情况下，会向解决方案中的所有托管项目分配“Microsoft 最少量建议规则”代码分析规则集。  可以在解决方案的属性对话框中更改分配给解决方案项目的规则集。  
  
> [!NOTE]
>  默认情况下，项目代码分析不会作为一个生成步骤运行。  若要使代码分析成为生成步骤，请参见[如何：配置托管代码项目的代码分析](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)。  
  
### 为托管代码解决方案中的多个项目指定规则集  
  
1.  在 [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)] 中。  在 [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)]或 [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]中，打开解决方案。  
  
2.  在**“分析”**菜单上，单击**“为解决方案配置代码分析”**。  
  
3.  如有必要，请展开**“通用属性”**节点，然后单击**“代码分析设置”**。  
  
4.  可以为一个或多个项目指定规则集。  
  
    -   若要为单个项目指定规则集，请单击项目名称。  
  
    -   若要为多个项目指定规则集，请按住 Ctrl，并单击项目名称。  
  
    -   若要指定解决方案中的所有项目，请按住 Shift，并在项目列表中单击。  
  
5.  单击项目的**“规则集”**字段，然后单击要应用的规则集的名称。