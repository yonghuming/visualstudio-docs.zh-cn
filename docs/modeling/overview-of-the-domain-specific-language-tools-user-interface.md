---
title: "概述域特定语言工具用户界面 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.dsltools.dsldesigner.editor
helpviewer_keywords:
- Domain-Specific Language Tools, user interface
ms.assetid: 81ae6b35-6819-41d0-953b-6b4ed81f9227
caps.latest.revision: 25
author: alancameronwills
ms.author: awills
manager: douge
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: d76ed4d14e7333678fcf927dfa1b2f21d8573be5
ms.lasthandoff: 02/22/2017

---
# <a name="overview-of-the-domain-specific-language-tools-user-interface"></a>域特定语言工具用户界面的概述
首次打开中的域特定语言工具 （DSL 工具） 解决方案[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]，用户界面将类似于下图。  
  
 ![dsl 设计器](../modeling/media/dsl_designer.png "dsl_designer")  
  
 下表说明了如何使用 UI 的部分。  
  
|**元素**|**定义**|  
|-----------------|--------------------|  
|关系图|此图表显示域模型。<br /><br /> 关系图有两个方面。 一方在模型中定义的元素的类型。 另一侧定义您的模型在屏幕上的显示方式。|  
|工具箱|拖动工具从工具箱添加域类和形状到关系图的类型。 若要添加关系、 连接器和形状映射，单击工具，然后单击关系图中的源节点和目标节点。|  
|DSL 资源管理器|**DSL 资源管理器**DSL 定义的活动窗口时，将出现。 它显示为树的 DSL。 DSL 资源管理器允许您编辑关系图不显示模型的功能。 例如，可以添加工具箱项，并在验证过程使用切换的**DSL 资源管理器**。|  
|DSL 详细信息窗口|**DSL 详细信息**窗口将显示域的属性，可以控制元素的显示方式，以及复制和删除元素的模型的元素。<br /><br /> -默认情况下， **DSL 详细信息**窗口的旁边将出现**错误列表**和**输出**windows。|  
  
## <a name="the-domain-model-diagram"></a>域模型关系图  
 域模型关系图分为两个部分。 关系图的一侧显示模型中的元素和关系。 另一侧显示模型的方式显示，并包含用于显示这些元素和属性的模型关系图的形状。 下图显示关系图中的元素。  
  
 ![具有泳道的 dsl 设计器](../modeling/media/dsl_desinger.png "dsl_desinger")  
  
 下表说明了一些域模型关系图中的元素。  
  
|**术语**|**定义**|  
|--------------|--------------------|  
|域类|域类是在模型中的元素的类型。<br /><br /> 域类可以出现不止一次在关系图中，如果它是多个关系的目标。<br /><br /> 若要添加域类，将从域类工具**工具箱**到**类和关系**侧的关系图。|  
|域之间的关系|域关系都是您的模型中的元素之间的链接类型。<br /><br /> *嵌入关系*表示目标元素是拥有或包含的源元素，并显示为一条实线。 在模型中的每个元素应为一个嵌入关系的目标，以便该模型形成一个树。 一个*引用关系*指示模型元素之间的常规链接，并显示为虚线。 任何元素可以具有任意数量的引用链接。<br /><br /> 通过单击该工具创建的关系**工具箱**，单击源域类中，，然后单击目标类。|  
|形状和连接符|形状指定模型元素 DSL 关系图上的显示方式，可用来显示关系的 DSL 关系图上的连接器指定行。<br /><br /> 若要创建形状或连接线，将工具拖至**关系图元素**侧的关系图。|  
|形状映射|形状映射显示为在域模型关系图中，将形状链接到域类，其中显示或将连接器传递给它显示的域关系上的线条。|  
  
## <a name="see-also"></a>另请参阅  
 [域特定语言工具概述](../modeling/overview-of-domain-specific-language-tools.md)   
 [域特定语言工具词汇表](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)   
 [自定义和扩展域特定语言](../modeling/customizing-and-extending-a-domain-specific-language.md)
