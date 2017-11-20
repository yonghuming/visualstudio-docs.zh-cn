---
title: "代码度量值 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- code metrics
- code analysis
- measure code quality
ms.assetid: bc38831e-2083-4ea4-8527-ee41499a342f
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 234ec06d47afee3cbde7c2333742fe43ab599219
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="code-metrics-values"></a>代码度量值
代码度量是一组软件度量值，使开发人员可以更好地了解他们正在开发的代码。 通过利用代码度量，开发人员可以了解哪些类型和/或方法应返工或更彻底的测试。 开发团队可以标识潜在的风险，了解的当前状态的一个项目，并在软件开发过程中跟踪进度。  
  
## <a name="software-measurements"></a>软件度量值  
 以下列表显示的代码度量结果[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]计算：  
  
-   **可维护性指数**-计算表示相对易用性的维护代码的索引值介于 0 和 100 之间。 较高的值意味着更好的可维护性。 颜色编码分级可用来快速确定你的代码中的故障点。 绿色等级介于 20 和 100 之间，表示的代码具有良好的可维护性。 黄色分级介于 10 和 19 之间，指示代码可维护性中等。 红色分级是 0 到 9 之间的分级，并指示低的可维护性。  
  
-   **圈复杂度**-衡量代码的结构化的复杂程度。 通过计算的流中的程序不同的代码路径数则创建它。 具有复杂控制流的程序将需要更多测试来实现良好的代码覆盖率，并且不容易维护。  
  
    > [!NOTE]
    >  在某些情况下中的方法的圈复杂度计算[!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)]不同于早期版本。 有关详细信息，请参阅"更改在 Visual Studio 2010 代码复杂性计算部分"的[代码度量值问题疑难解答](../code-quality/troubleshooting-code-metrics-issues.md)。  
  
-   **继承深度**-指示的类层次结构的根到扩展的类定义的数量。 深的层次结构更难有可能是为了了解其中定义特定的方法和字段或 / 和重新定义。  
  
-   **类耦合**-测量与通过参数、 本地变量、 返回类型、 方法调用、 泛型或模板实例化、 基类，这些类、 接口实现、 外部类型上定义的字段的唯一类耦合和特性修饰。 软件良好的设计指出类型和方法应具有高内聚和较低的耦合。 耦合较高指示重复使用和维护由于其他类型其许多依存关系会很困难的设计。  
  
-   **代码行**-指示代码中的行的大致数目。 计数基于 IL 代码，因此不精确的源代码文件中的行数。 非常高的计数可能指示类型或方法尝试执行的操作过多的工作，并且应拆分。 此外，它也可能表示的类型或方法可能难以维护。  
  
## <a name="anonymous-methods"></a>匿名方法  
 *匿名方法*就是没有名称的方法。 匿名方法是最常用于将代码块作为委托参数传递。 匿名方法中的成员，如方法或访问器，声明的度量结果都与声明方法的成员关联。 它们不具有成员的调用的方法相关联。  
  
 有关代码度量如何处理匿名方法的详细信息，请参阅[匿名方法和代码分析](../code-quality/anonymous-methods-and-code-analysis.md)。  
  
## <a name="generated-code"></a>生成的代码  
 某些软件工具和编译器生成的代码，它将添加到项目和项目开发人员看不到或不应更改。 大多数情况下，代码度量忽略生成的代码，当它计算度量值时。 这使度量值以反映开发人员可以查看和更改。  
  
 不忽略生成为 Windows 窗体的代码，因为它是开发人员可以查看和更改的代码。  
  
## <a name="see-also"></a>另请参阅  
 [测量托管代码的复杂性和可维护性](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)