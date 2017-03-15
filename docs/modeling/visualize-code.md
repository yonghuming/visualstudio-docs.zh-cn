---
title: "可视化代码 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-techdebt
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- code, understanding
- code, visualizing
- code, exploring
ms.assetid: 0dd7d438-393a-4cd3-b417-9bf37379e1b0
caps.latest.revision: 47
author: alexhomer1
ms.author: ahomer
manager: douge
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 3d07f82ea737449fee6dfa04a61e195654ba35fa
ms.openlocfilehash: aa7e0e7e9bbd4d4a3f8a1b2fa82f1ce7a6ba3e53
ms.lasthandoff: 02/22/2017

---
# <a name="visualize-code"></a>可视化代码
你可以在 Visual Studio 中使用可视化和建模工具，以帮助你了解现有代码并描述你的应用程序。 这可以让你直观地了解更改可能对代码产生的影响，并帮助你评估更改导致的工作和风险。 例如：  
  
-   了解代码的关系，可以用可视的方式映射这些关系。  
  
-   若要描述您的系统体系结构并使该代码与其设计保持一致，创建依赖项关系图，并针对这些关系图验证代码。  
  
-   若要描述类结构，请创建类关系图。  
  
 这些工具还可以帮助你更轻松地与参与项目的人员进行沟通。 
  
 若要查看哪些版本的 Visual Studio 支持每项功能，请参阅[体系结构和建模工具的版本支持](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)  
  
## <a name="what-do-you-want-to-do"></a>你希望做什么？  
  
|||  
|-|-|  
|**了解代码和其关系︰**<br /><br /> 特定代码段之间的代码图关系<br /><br /> 请参阅整个解决方案中的代码关系概述。<br /><br /> **注意**：在此版本的 Visual Studio 中，术语 *代码图* 用于替换 *依赖项关系图*。|-   [映射解决方案之间的依赖关系](../modeling/map-dependencies-across-your-solutions.md)<br />-   [使用代码图调试应用程序](../modeling/use-code-maps-to-debug-your-applications.md)<br />-   [使用代码图分析器发现潜在问题](../modeling/find-potential-problems-using-code-map-analyzers.md)<br />-   [调试时映射调用堆栈上的方法](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)|  
|**了解类结构︰**<br /><br /> 通过从代码创建类关系图，在项目中查看类的结构。|[如何：向项目中添加类图（类设计器）](../ide/how-to-add-class-diagrams-to-projects-class-designer.md)|  
|**描述高级系统设计和验证对此设计的代码︰**<br /><br /> 通过创建依赖项关系图来描述高级系统设计及其预期依赖项。 对此设计进行代码验证，以确保代码中的依赖项与设计保持一致。|-   [在代码中创建依赖项关系图](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [依赖项关系图︰ 参考](../modeling/layer-diagrams-reference.md)<br />-   [依赖项关系图︰ 准则](../modeling/layer-diagrams-guidelines.md)<br />-   [使用依赖项关系图验证代码](../modeling/validate-code-with-layer-diagrams.md)|  
  
## <a name="external-resources"></a>外部资源  
  
|**类别**|**链接**|  
|------------------|---------------|  
|**论坛**|-   [Visual Studio 可视化 < 建模工具](http://go.microsoft.com/fwlink/?LinkId=184720)<br />-   [Visual Studio 可视化 < 建模 SDK （DSL 工具）](http://go.microsoft.com/fwlink/?LinkId=184721)|  
|**博客**|[Visual Studio ALM + Team Foundation Server 博客](http://go.microsoft.com/fwlink/?LinkID=201340)|  
|**技术文章和日志**|[MSDN 体系结构论坛](http://go.microsoft.com/fwlink/?LinkId=201343)|  
  
## <a name="see-also"></a>另请参阅  
 [方案︰ 更改设计使用可视化和建模](../modeling/scenario-change-your-design-using-visualization-and-modeling.md)   
 [分析和体系结构建模](../modeling/analyze-and-model-your-architecture.md)   
 [应用程序的体系结构的模型](../modeling/model-your-app-s-architecture.md)   
 [在你的开发过程中使用模型](../modeling/use-models-in-your-development-process.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

