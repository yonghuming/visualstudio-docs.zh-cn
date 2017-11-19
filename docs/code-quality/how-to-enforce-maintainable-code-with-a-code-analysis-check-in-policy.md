---
title: "如何： 使用代码分析签入策略强制实现代码 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: code analysis, check-in policies
ms.assetid: d1b3b04f-4dd9-40e6-b2d4-b414d33fb647
caps.latest.revision: "8"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 39d9697c7d6a216c08e34eb19287d22a76d67a55
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-enforce-maintainable-code-with-a-code-analysis-check-in-policy"></a>如何：使用代码分析签入策略强制实现代码的可维护性
开发人员可以使用代码度量工具来测量的复杂性和可维护性其代码，但不是能调用代码度量值作为签入策略的一部分。 但是，团队可以启用代码分析规则，验证他们的代码与代码度量标准的符合性和强制实施通过签入策略规则。 有关代码度量值的详细信息，请参阅[代码度量值](../code-quality/code-metrics-values.md)。  
  
 开发人员可以使深度的继承、 类耦合、 可维护性指数和复杂性规则来借助代码分析签入策略强制实现代码。 所有四个。 这些规则在代码分析策略编辑器中"可维护性规则"类别下都找到。  
  
 版本控制的管理员为[!INCLUDE[esprfound](../code-quality/includes/esprfound_md.md)]可以将代码分析可维护性规则添加到的签入策略要求。 这些签入策略需要开发人员运行代码分析在启动签入前根据这些规则的更改。  
  
### <a name="to-open-the-code-analysis-policy-editor"></a>若要打开代码分析策略编辑器  
  
1.  在**团队资源管理器**，右键单击团队项目，单击**团队项目设置**，然后单击**源代码管理**。  
  
     **源代码管理**对话框随即出现。  
  
2.  上**签入策略**卡，然后单击**添加**。  
  
     **添加签入策略**对话框随即出现。  
  
3.  在**签入策略**列表中，选择**代码分析**复选框，并依次**确定**。  
  
     **代码分析策略编辑器**对话框随即出现。  
  
### <a name="to-enable-code-analysis-maintainability-rules"></a>若要启用代码分析可维护性规则  
  
1.  在**代码分析策略编辑器**对话框中，在**规则设置**，展开**可维护性规则**节点。  
  
2.  选择以下的规则所对应的复选框：  
  
    -   继承深度： **CA1501 AvoidExcessiveInheritance** -阈值： 在 5 个以上的层深度警告  
  
    -   复杂性： **CA1502 AvoidExcessiveComplexity** -阈值： 多个 25 处出现警告  
  
    -   可维护性指数： **CA1505 AvoidUnmaintainableCode** -阈值： 少于 20 处出现警告  
  
    -   类耦合： **CA1506 AvoidExcessiveClassCoupling** -阈值： 在多个类的 80 和多个方法的 30 警告  
  
    -   此外，如果你想违反规则时禁止生成，则选择**将警告视为错误**规则说明旁边的复选框。  
  
3.  单击“确定”。 现在，新签入策略应用到以后进行签入时。  
  
## <a name="see-also"></a>另请参阅  
 [代码度量值](../code-quality/code-metrics-values.md)   
 [创建和使用代码分析签入策略](../code-quality/creating-and-using-code-analysis-check-in-policies.md)