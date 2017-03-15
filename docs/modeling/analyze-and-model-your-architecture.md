---
title: "分析和建模您的体系结构 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-techdebt
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
caps.latest.revision: 127
author: alexhomer1
ms.author: ahomer
manager: douge
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 98d1214d1cda81102f9e03a8ce8b83886aa2c0ec
ms.openlocfilehash: 78217396085aa5531ec2cbdd5dff522201287777
ms.lasthandoff: 02/22/2017

---
# <a name="analyze-and-model-your-architecture"></a>对体系结构进行分析和建模
请确保您的应用程序通过使用 Visual Studio 体系结构和建模工具来设计和建模应用程序满足架构要求。 

* 通过使用 Visual Studio 来可视化代码结构、行为和关系可使你更容易理解现有程序代码。 

* 告诉您的团队需要尊重体系结构的依赖关系。  
  
* 作为开发过程的一部分，可以跨整个应用程序生命周期创建不同详细信息级别的模型。

请参阅[方案︰ 更改设计使用可视化和建模](../modeling/scenario-change-your-design-using-visualization-and-modeling.md)。  
  
## <a name="to"></a>到  
  
|||  
|-|-|  
|**可视化代码**：<br /><br /> -通过创建代码图，请参阅代码的组织和关系。 可视化程序集、命名空间、类、方法等之间的依赖关系。<br />-通过从代码创建类关系图，请参见类结构和针对某个特定项目的成员。<br />-通过创建依赖项关系图验证代码来查找您的代码和它的设计之间的冲突。|-   [可视化代码](../modeling/visualize-code.md)<br />-   [使用类和其他类型 （类设计器）](../ide/working-with-classes-and-other-types-class-designer.md)<br />-   [视频︰ 了解使用 Visual Studio 2015 代码图的代码中的设计](https://channel9.msdn.com/Events/Visual-Studio/Connect-event-2015/502)<br />-   [视频︰ 验证实时您体系结构的依赖关系](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4)|  
|**定义体系结构**：<br /><br /> 定义并实施对您的代码通过创建依赖项关系图的组件之间的依赖关系的约束。|-   [视频︰ 验证体系结构依赖项与 Visual Studio (第 9 频道)](https://channel9.msdn.com/Events/Connect/2016/170)|  
|**验证您的系统要求和预期设计︰**<br /><br /> 验证代码与描述预期体系结构的依赖项关系图的依赖项，以防止可能与设计发生冲突的修改。|-   [视频︰ 验证体系结构依赖项与 Visual Studio (第 9 频道)](https://channel9.msdn.com/Events/Connect/2016/170)|  
|**使用 Team Foundation 版本控制共享模型、关系图和代码图**：<br /><br /> -将代码图、 项目和 Team Foundation 版本控制下的 deoendency 关系图以便您可以共享它们。|当多个用户使用 Team Foundation 版本控制下的这些项时，使用这些指南会有助于避免版本控制问题：<br /><br /> -   [管理模型和版本控制下的关系图](../modeling/manage-models-and-diagrams-under-version-control.md)|  
|**自定义模型和关系图**：<br /><br /> -创建您自己的域特定语言。|-   [Visual Studio-域特定语言的建模 SDK](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)|  
|**使用 T4 模板生成文本**：<br /><br /> -使用文本块和控制逻辑深入了解模板可生成基于文本的文件。<br /> 的使用 Visual Studio 中包含的 MSBuild T4 模板生成|-   [代码生成和 T4 文本模板](../modeling/code-generation-and-t4-text-templates.md)|

若要查看哪些版本的 Visual Studio 支持每项功能，请参阅[体系结构和建模工具的版本支持](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)  
  
## <a name="types-of-models-and-their-uses"></a>模型类型和用法  
  
|**模型类型和典型用法**|  
|-------------------------------------|  
|**代码映射**<br /><br /> 代码图可帮助查看代码中的组织和关系。<br /><br /> 典型用法：<br /><br /> -检查程序代码，以便您能够更好地了解其结构和其依赖关系，如何更新它，并估计成本为建议的更改。<br /><br /> 请参阅：<br /><br /> -   [映射解决方案之间的依赖关系](../modeling/map-dependencies-across-your-solutions.md)<br />-   [使用代码图调试应用程序](../modeling/use-code-maps-to-debug-your-applications.md)<br />-   [使用代码图分析器发现潜在问题](../modeling/find-potential-problems-using-code-map-analyzers.md)|  
|**依赖项关系图**<br /><br /> 依赖项关系图使您的应用程序结构定义为一组层或显式依赖关系的块。 您可以运行验证来发现代码中的依赖关系和依赖项关系图中所述依赖项之间的冲突。<br /><br /> 典型用法：<br /><br /> -在其生命周期稳定通过大量更改，应用程序的结构。<br />在签入代码更改之前发现无意的依赖项冲突。<br /><br /> 请参阅：<br /><br /> -   [在代码中创建依赖项关系图](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [依赖项关系图︰ 参考](../modeling/layer-diagrams-reference.md)<br />-   [使用依赖项关系图验证代码](../modeling/validate-code-with-layer-diagrams.md)|  
|**域特定语言 (DSL)**<br /><br /> DSL 是为特定目的而设计的一种表示法。 在 Visual Studio 中通常表示为图形。<br /><br /> 典型用法：<br /><br /> 生成或配置应用程序的各部分。 若要开发表示法和工具，则需要进行工作。 其产生的结果，与 UML 自定义相比，会更好地适应你的域。<br />— 对于大型项目或产品系列中开发 DSL 和及其工具的投资由在多个项目中使用它。<br /><br /> 请参阅：<br /><br /> -   [Visual Studio-域特定语言的建模 SDK](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)|  
  
## <a name="where-can-i-get-more-information"></a>在何处可以获取详细信息？  
  
[Visual Studio 可视化 & 建模工具论坛](http://go.microsoft.com/fwlink/?LinkId=184720)  
  
## <a name="see-also"></a>另请参阅  
 [新增功能](../modeling/what-s-new-for-design-in-visual-studio.md)   
 [DevOps 和应用程序生命周期管理](http://msdn.microsoft.com/Library/74a1f71d-7f23-4c71-8fd7-89ede614fab6)

