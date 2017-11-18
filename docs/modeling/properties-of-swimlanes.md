---
title: "泳道属性 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.dsltools.dsldesigner.swimlane
helpviewer_keywords: Domain-Specific Language, swimlane
ms.assetid: 47edbc2d-09e4-48ac-b4d1-5268a06a27e6
caps.latest.revision: "24"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: 1b8eacf8fdd74fc9fe0703dc50beb46a2442e939
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="properties-of-swimlanes"></a>泳道属性
可以向图表添加泳道。 泳道将关系图划分为垂直或水平区域。 你可以定义要显示在泳道内其他形状。 有关详细信息，请参阅[如何定义域特定语言](../modeling/how-to-define-a-domain-specific-language.md)。 有关如何使用这些属性的详细信息，请参阅[自定义和扩展的域特定语言](../modeling/customizing-and-extending-a-domain-specific-language.md)。  
  
 泳道具有下表中列出的属性。  
  
|属性|描述|默认|  
|--------------|-----------------|-------------|  
|正文填充颜色|正文泳道的填充颜色。|空白|  
|标头填充颜色|标头泳道的填充颜色。|DarkGray|  
|分隔符颜色|分隔线的颜色。|LightGray|  
|分隔符的线条样式|分隔线的样式 (`Solid`， `Dash`， `Dot`， `DashDot`， `DashDotDot`，或`Custom`)。|`Dash`|  
|分隔符粗细|以英寸为单位的分隔线的粗细。|0.03125|  
|文本颜色|用于与此泳道关联的文本修饰器颜色。|黑色|  
|访问修饰符|类的访问级别 (`public`或`internal`)。|Public|  
|自定义特性|用于将属性添加到此泳道从生成的代码类。|\<无 >|  
|生成双派生|如果`True`，将生成的基本类和分部类 （以支持通过替代的自定义）。 有关详细信息，请参阅[重写和扩展生成的类](../modeling/overriding-and-extending-the-generated-classes.md)。|False|  
|具有自定义的构造函数|如果`True`，自定义的构造函数将提供的源代码中。 有关详细信息，请参阅[重写和扩展生成的类](../modeling/overriding-and-extending-the-generated-classes.md)。|False|  
|继承修饰符|介绍的从泳道生成源代码类的继承的类型 (`none`，`abstract`或`sealed`)。|无|  
|基泳道|此泳道的基类。|(无)|  
|名称|此泳道的名称。|当前的名称|  
|命名空间|隶属于此泳道命名空间。|当前命名空间|  
|工具提示类型|工具提示的定义方式 (`fixed`， `variable`，或`none`)。 如果`fixed`，然后的值`Fixed Tooltip Text`使用属性; 如果`variable`，然后才能进行自定义代码中定义的工具提示。|\<无 >|  
|说明|与此泳道相关联的非正式说明。|\<无 >|  
|对齐方式|水平或垂直对齐方式。|垂直|  
|初始高度|此泳道，以英寸为单位的初始高度。 仅适用于水平泳道。|0|  
|初始宽度|此泳道，以英寸为单位初始宽度。 仅适用于垂直泳道。|0|  
|公开文本颜色|如果`True`，用户可以在生成的设计器中设置泳道的颜色。 若要对此设置，请右击泳道形状，然后单击**添加公开**。|False|  
|描述|用于记录生成的设计器。|\<无 >|  
|显示名称|将引用此泳道类生成设计器中显示的名称。|\<无 >|  
|固定的工具提示文本|适用于固定的工具提示文本。|\<无 >|  
|帮助关键字|用于编制索引此泳道的 F1 帮助关键字。|\<无 >|  
  
## <a name="see-also"></a>另请参阅  
 [域特定语言工具词汇表](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)