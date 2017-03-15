---
title: "如何：使用代码分析签入策略强制实现代码的可维护性 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "代码分析，签入策略"
ms.assetid: d1b3b04f-4dd9-40e6-b2d4-b414d33fb647
caps.latest.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 8
---
# 如何：使用代码分析签入策略强制实现代码的可维护性
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

开发人员可以使用代码度量工具来测量其代码的复杂性和可维护性，但不能将代码度量作为签入策略的一部分来调用。  然而，一个团队可以启用验证其代码是否遵从代码度量标准的代码分析规则，并且可以通过签入策略强制执行这些规则。  有关代码度量的更多信息，请参见[代码度量值](../code-quality/code-metrics-values.md)。  
  
 开发人员可以启用继承深度、类耦合、可维护性指数和复杂性规则，并借助代码分析签入策略强制实现代码的可维护性。  这四个规则全部都可以在代码分析策略编辑器中的“可维护性规则”类别下找到。  
  
 [!INCLUDE[esprfound](../code-quality/includes/esprfound_md.md)] 版本控制的管理员可以将代码分析可维护性规则添加到签入策略要求中。  这些签入策略要求开发人员在启动签入操作前根据这些规则的更改运行代码分析。  
  
### 打开代码分析策略编辑器  
  
1.  在**“团队资源管理器”**中，右击团队项目，单击**“团队项目设置”**，然后单击**“源代码管理”**。  
  
     将出现**“源代码管理”**对话框。  
  
2.  在**“签入策略”**选项卡上，单击**“添加”**。  
  
     **“添加签入策略”**对话框出现。  
  
3.  在**“签入策略”**列表中，选中**“代码分析”**复选框，然后单击**“确定”**。  
  
     将出现**“代码分析策略编辑器”**对话框。  
  
### 启用代码分析可维护性规则  
  
1.  在**“代码分析策略编辑器”**对话框的**“规则设置”**下，展开**“可维护性规则”**节点。  
  
2.  选中下列规则的复选框：  
  
    -   继承深度：**CA1501 AvoidExcessiveInheritance** \- 阈值：超过 5 级深度时警告  
  
    -   复杂性：**CA1502 AvoidExcessiveComplexity** \- 阈值：超过 25 时警告  
  
    -   可维护性指数：**CA1505 AvoidUnmaintainableCode** \- 阈值：低于 20 时警告  
  
    -   类耦合：**CA1506 AvoidExcessiveClassCoupling** \- 阈值：类超过 80、方法超过 30 时警告  
  
    -   此外，如果您希望当违反规则时禁止生成，请选中规则说明旁边的**“将警告视为错误”**复选框。  
  
3.  单击**“确定”**。  现在，新的签入策略即应用于以后的签入。  
  
## 请参阅  
 [代码度量值](../code-quality/code-metrics-values.md)   
 [创建和使用代码分析签入策略](../code-quality/creating-and-using-code-analysis-check-in-policies.md)