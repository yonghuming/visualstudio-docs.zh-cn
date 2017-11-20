---
title: "可视化代码 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-techdebt
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- code, understanding
- code, visualizing
- code, exploring
ms.assetid: 0dd7d438-393a-4cd3-b417-9bf37379e1b0
caps.latest.revision: "47"
author: alexhomer1
ms.author: ahomer
manager: douge
ms.openlocfilehash: 0abc0bff93da0944ce7e413a83dafc47e375a8a2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="visualize-code"></a>可视化代码
你可以在 Visual Studio 中使用可视化和建模工具，以帮助你了解现有代码并描述你的应用程序。 这可以让你直观地了解更改可能对代码产生的影响，并帮助你评估更改导致的工作和风险。 例如：  
  
-   了解代码的关系，可以用可视的方式映射这些关系。  
  
-   若要描述系统的体系结构并使代码与其设计保持一致，创建依赖项关系图，并对照这些关系图验证代码。  
  
-   若要描述类结构，请创建类关系图。  
  
 这些工具还可以帮助你更轻松地与参与项目的人员进行沟通。 
  
 若要查看支持每个功能的 Visual Studio 版本，请参阅 [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)  
  
## <a name="what-do-you-want-to-do"></a>你希望做什么？  
  
|||  
|-|-|  
|**了解代码和它的关系：**<br /><br /> 特定代码段之间的代码图关系<br /><br /> 请参阅整个解决方案中的代码关系概述。<br /><br /> **注意**：在此版本的 Visual Studio 中，术语 *代码图* 用于替换 *依赖项关系图*。|-   [映射解决方案中的依赖关系](../modeling/map-dependencies-across-your-solutions.md)<br />-   [使用代码图调试你的应用程序](../modeling/use-code-maps-to-debug-your-applications.md)<br />-   [使用代码图分析器查找潜在问题](../modeling/find-potential-problems-using-code-map-analyzers.md)<br />-   [调试时映射调用堆栈上的方法](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)|  
|**了解类结构：**<br /><br /> 通过从代码创建类关系图，在项目中查看类的结构。|[如何：向项目中添加类图（类设计器）](../ide/how-to-add-class-diagrams-to-projects-class-designer.md)|  
|**描述高级系统设计和验证代码对此设计：**<br /><br /> 创建依赖项关系图来描述高级系统设计和其预期的依赖项。 对此设计进行代码验证，以确保代码中的依赖项与设计保持一致。|-   [在代码中创建依赖项关系图](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [依赖项关系图： 参考](../modeling/layer-diagrams-reference.md)<br />-   [依赖项关系图： 准则](../modeling/layer-diagrams-guidelines.md)<br />-   [使用依赖项关系图验证代码](../modeling/validate-code-with-layer-diagrams.md)|  
  
## <a name="external-resources"></a>外部资源  
  
|**类别**|**Links**|  
|------------------|---------------|  
|**论坛**|-   [Visual Studio 可视化和建模工具](http://go.microsoft.com/fwlink/?LinkId=184720)<br />-   [Visual Studio 可视化和建模 SDK（DSL 工具）](http://go.microsoft.com/fwlink/?LinkId=184721)|  
|**博客**|[Visual Studio ALM + Team Foundation Server 博客](http://go.microsoft.com/fwlink/?LinkID=201340)|  
|**技术文章和日志**|[MSDN 体系结构论坛](http://go.microsoft.com/fwlink/?LinkId=201343)|  
  
## <a name="see-also"></a>另请参阅  
 [方案： 更改设计使用可视化和建模](../modeling/scenario-change-your-design-using-visualization-and-modeling.md)   
 [分析体系结构和建模](../modeling/analyze-and-model-your-architecture.md)   
 [建模应用程序的体系结构](../modeling/model-your-app-s-architecture.md)   
 [在你的开发过程中使用模型](../modeling/use-models-in-your-development-process.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
