---
title: "依赖关系图︰ 参考 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.teamarch.layerdiagram.layerexplorer.artifactlink
- vs.teamarch.layerdiagram.layerexplorer.artifactlink.properties
- vs.teamarch.layerdiagram.diagram
- vs.teamarch.UMLModelExplorer.layerdiagram
- vs.teamarch.layerdiagram.layerexplorer
- vs.teamarch.layerdiagram.shapes.properties
- vs.teamarch.layerdiagram.toolbox
helpviewer_keywords:
- architecture, dependency diagrams
- dependency diagrams
- diagrams - modeling, layer
- constraints, architectural
ms.assetid: f26c986c-1e79-420e-b29a-a283e6d8a71d
caps.latest.revision: 33
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
ms.sourcegitcommit: fd26c504273cae739ccbeef5e406891def732985
ms.openlocfilehash: 74829877befa9f48988d42e04a58e2a418e7d82b
ms.lasthandoff: 02/22/2017

---
# <a name="dependency-diagrams-reference"></a>依赖项关系图︰ 参考
在 Visual Studio 中，您可以使用*依赖项关系图*实现您的系统的高级别、 逻辑体系结构的可视化效果。 依赖项关系图的物理项目组织您的系统中调用的逻辑抽象组到*层*。 这些层用于描述这些项目执行的主要任务或系统的主要组件。 每一层还可以包含描述更详细的任务的嵌套层。  
  
 若要查看哪些版本的 Visual Studio 支持此功能，请参阅[体系结构和建模工具的版本支持](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)。  
  
 你可以指定各层之间的预期或现有依赖项。 这些依赖项（表示为箭头）指示哪些层可以使用或当前正在使用由其他层表示的功能。 通过将您的系统组织到描述不同角色和功能的层，依赖项关系图有助于使您更轻松地理解、 重用和维护您的代码。  
  
 使用依赖项关系图来帮助您执行以下任务︰  
  
-   传达系统的现有或预期逻辑体系结构。  
  
-   发现现有代码和预期体系结构之间的冲突。  
  
-   在重构、更新或改进你的系统时，可视化更改对预期体系结构的影响。  
  
-   在开发和维护你的代码过程中，通过包括对签入的验证来强化预期体系结构并生成操作。  
  
 本主题介绍您可以使用依赖项关系图的元素。 有关详细信息，有关如何创建和绘制依赖项关系图，请参阅[依赖项关系图︰ 准则](../modeling/layer-diagrams-guidelines.md)。 有关分层模式的详细信息，请访问[模式 < 和实施方案网站](http://go.microsoft.com/fwlink/?LinkId=145794)。  
  
## <a name="reading-dependency-diagrams"></a>读取依赖项关系图  
 ![依赖项关系图上的元素](~/modeling/media/uml_layerrefreading.png "UML_LayerRefReading")  
  
 下表描述你可以使用依赖项关系图的元素。  
  
|**形状**|**元素**|**描述**|  
|---------------|-----------------|---------------------|  
|1|**层**|系统中的物理项目的逻辑组。 这些项目可以是命名空间、项目、类、方法等。<br /><br /> 若要查看链接到层的项目，打开层的快捷菜单，然后选择**查看链接**若要打开**层资源管理器**。<br /><br /> 有关详细信息，请参阅[层资源管理器](#Explorer)。<br /><br /> -   **Forbidden Namespace 依赖关系**-指定与此层相关联的项目不能依赖于指定的命名空间。<br />-   **禁止的命名空间**-指定与此层相关联的项目必须不属于指定的命名空间。<br />-   **所需的命名空间**-指定与此层相关联的项目必须属于某个指定的命名空间。|  
|2|**依赖项**|指示某个层可以使用另一层的功能，但反之则不然。<br /><br /> -   **方向**-指定依赖关系的方向。|  
|3|**双向依赖项**|指示某个层可以使用另一层的功能，反之易然。<br /><br /> -   **方向**-指定依赖关系的方向。|  
|4|**注释**|用于将一般注释添加到关系图或关系图上的元素。|  
|5|**注释链接**|用于将注释链接到关系图上的元素。|  
  
##  <a name="a-nameexplorera-layer-explorer"></a><a name="Explorer"></a>层资源管理器  
 在解决方案中，如项目、类、命名空间、项目文件和软件的其他部件，你可以将每个层链接到项目。 层上的数字显示链接到该层的项目数。 但是，在读取层上的项目数时，请记住：  
  
-   如果某个层链接到一个包含其他项目的项目，但该层未直接链接到其他项目，则该数字仅包括链接的项目。 但是，在层验证过程中其他项目包括在分析范围内。  
  
     例如，如果一个层链接到单个命名空间，则链接的项目数是 1，即使该命名空间包含类也是如此。 如果该层还链接到命名空间中的每个类，则该数字将包括链接的类。  
  
-   如果一个层包含链接到项目的其他层，则容器层也链接到这些项目，即使容器层上的数字不包括这些项目。  
  
 有关链接层和项目的详细信息，请参阅：  
  
-   [依赖项关系图︰ 准则](../modeling/layer-diagrams-guidelines.md)  
  
-   [在代码中创建依赖项关系图](../modeling/create-layer-diagrams-from-your-code.md)  
  
#### <a name="to-examine-the-linked-artifacts"></a>若要检查链接的项目  
  
-   在依赖项关系图中，打开一个或多个层的快捷菜单，然后选择**查看链接**。  
  
     **层资源管理器**将打开并显示链接到所选层的项目。 **层资源管理器**有一个列，显示了每个项目链接的属性。  
  
    > [!NOTE]
    >  如果您无法看到所有这些属性，请展开**层资源管理器**窗口。  
  
    |**在层资源管理器中的列**|**描述**|  
    |----------------------------------|---------------------|  
    |**类别**|项目种类，例如类、命名空间、源文件等|  
    |**层**|链接到该项目的层|  
    |**支持验证**|如果**True**，则层验证过程可以验证项目是否符合指向或来自此元素的依赖关系。<br /><br /> 如果**False**，则该链接不参与层验证过程。<br /><br /> 有关详细信息，请参阅[依赖项关系图︰ 准则](../modeling/layer-diagrams-guidelines.md)。|  
    |**标识符**|对链接的项目的引用|  
  
## <a name="see-also"></a>另请参阅  
 [为应用程序创建模型](../modeling/create-models-for-your-app.md)
