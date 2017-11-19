---
title: "分析和建模你的体系结构 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-techdebt
ms.tgt_pltfrm: 
ms.topic: get-started-article
helpviewer_keywords:
- Visual Studio Ultimate, exploring code
- Visual Studio Ultimate, visualizing code
- diagrams - modeling
- Visual Studio ALM, modeling
- application, design
- architecture
- code visualization
- application design
- applications, architecture
- code exploration
- Visual Studio ALM, exploring code
- modeling
- application architecture
- application, modeling
- applications, modeling
- architecture [Visual Studio ALM], modeling
- application modeling
- Visual Studio Ultimate, modeling
- architecture [Visual Studio Ultimate], modeling
- application, architecture
- Visual Studio ALM, visualizing code
- applications, designing
ms.assetid: c9f04cfa-72bd-419d-a952-616eed01472e
caps.latest.revision: "127"
author: alexhomer1
ms.author: ahomer
manager: douge
ms.openlocfilehash: 57d04543cf604ced1b94632c2f2c3bc566267f85
ms.sourcegitcommit: ec1c7e7e3349d2f3a4dc027e7cfca840c029367d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/07/2017
---
# <a name="analyze-and-model-your-architecture"></a>对体系结构进行分析和建模
请确保你的应用通过使用 Visual Studio 体系结构和建模工具进行设计和建模应用程序满足体系结构要求。 

* 通过使用 Visual Studio 来可视化代码结构、行为和关系可使你更容易理解现有程序代码。 

* 对你在需要遵从体系结构依赖项的团队进行培训。  
  
* 作为开发过程的一部分，可以跨整个应用程序生命周期创建不同详细信息级别的模型。

请参阅[方案： 使用可视化和建模更改设计](../modeling/scenario-change-your-design-using-visualization-and-modeling.md)。  
  
## <a name="to"></a>到  
  
|||  
|-|-|  
|**可视化代码**：<br /><br /> -通过创建代码图，请参阅代码的组织和关系。 可视化程序集、命名空间、类、方法等之间的依赖关系。<br />-通过从代码创建类关系图，请参阅类结构和针对某个特定项目的成员。<br />-创建依赖项关系图验证代码来查找代码及其设计之间的冲突。|-   [可视化代码](../modeling/visualize-code.md)<br />-   [使用类和其他类型 （类设计器）](../ide/working-with-classes-and-other-types-class-designer.md)<br />-   [视频： 了解使用 Visual Studio 2015 代码图的代码中的设计](https://channel9.msdn.com/Events/Visual-Studio/Connect-event-2015/502)<br />-   [视频： 验证实时体系结构依赖项](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4)|  
|**定义体系结构**：<br /><br /> -定义并实施对你通过创建依赖项关系图的代码的组件之间的依赖关系的约束。|-   [视频： 验证 Visual Studio (通道 9) 体系结构依赖关系](https://channel9.msdn.com/Events/Connect/2016/170)|  
|**使用要求和预期设计来验证你的系统：**<br /><br /> -验证代码依赖项关系图来描述预期体系结构的依赖关系并防止发生与设计产生冲突的更改。|-   [视频： 验证 Visual Studio (通道 9) 体系结构依赖关系](https://channel9.msdn.com/Events/Connect/2016/170)|  
|**使用 Team Foundation 版本控制共享模型、关系图和代码图**：<br /><br /> -将代码图、 项目和 deoendency 关系图置于 Team Foundation 版本控制下的以便可以共享。| |  
|**自定义模型和关系图**：<br /><br /> -创建你自己的域特定语言。|-   [为 Visual Studio-域特定语言建模 SDK](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)|  
|**使用 T4 模板生成文本**：<br /><br /> -使用文本块和模板内的控制逻辑生成基于文本的文件。<br /> 的使用 Visual Studio 中包含的 MSBuild T4 模板生成|-   [代码生成和 T4 文本模板](../modeling/code-generation-and-t4-text-templates.md)|

若要查看支持每个功能的 Visual Studio 版本，请参阅 [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)  
  
## <a name="types-of-models-and-their-uses"></a>模型类型和用法  
  
|**模型类型和典型用法**|  
|-------------------------------------|  
|**代码图**<br /><br /> 代码图可帮助查看代码中的组织和关系。<br /><br /> 典型用法：<br /><br /> -检查程序代码以便你可以更好地了解其结构及其依赖关系，如何对其进行更新，并估计的成本的建议更改。<br /><br /> 请参阅：<br /><br /> -   [映射解决方案中的依赖关系](../modeling/map-dependencies-across-your-solutions.md)<br />-   [使用代码图调试你的应用程序](../modeling/use-code-maps-to-debug-your-applications.md)<br />-   [使用代码图分析器查找潜在问题](../modeling/find-potential-problems-using-code-map-analyzers.md)|  
|**依赖项关系图**<br /><br /> 依赖项关系图可以让你的应用程序结构定义为一组层或显式依赖关系的块。 你可以运行验证来发现代码中的依赖关系和依赖项关系图中所述依赖项之间的冲突。<br /><br /> 典型用法：<br /><br /> -在其生命周期稳定通过大量的更改应用程序的结构。<br />签入对代码的更改之前发现无意的依赖项冲突。<br /><br /> 请参阅：<br /><br /> -   [在代码中创建依赖项关系图](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [依赖项关系图： 参考](../modeling/layer-diagrams-reference.md)<br />-   [使用依赖项关系图验证代码](../modeling/validate-code-with-layer-diagrams.md)|  
|**域特定语言 (DSL)**<br /><br /> DSL 是为特定目的而设计的一种表示法。 在 Visual Studio 中通常表示为图形。<br /><br /> 典型用法：<br /><br /> 生成或配置应用程序的各部分。 若要开发表示法和工具，则需要进行工作。 其产生的结果，与 UML 自定义相比，会更好地适应你的域。<br />-适用于大型项目或在某些产品系列中开发 DSL 和及其工具的投资由在多个项目中使用它。<br /><br /> 请参阅：<br /><br /> -   [为 Visual Studio-域特定语言建模 SDK](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)|  
  
## <a name="where-can-i-get-more-information"></a>在何处可以获取详细信息？  
  
[Visual Studio 可视化和建模工具论坛](http://go.microsoft.com/fwlink/?LinkId=184720)  
  
## <a name="see-also"></a>另请参阅  
 [新增功能](../modeling/what-s-new-for-design-in-visual-studio.md)   
 [DevOps 和应用程序生命周期管理](http://msdn.microsoft.com/Library/74a1f71d-7f23-4c71-8fd7-89ede614fab6)
