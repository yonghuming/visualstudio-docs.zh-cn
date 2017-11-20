---
title: "连接器的属性 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Domain-Specific Language, connectors
ms.assetid: b1f24e8d-cdd7-4a5d-af37-1038f43b45c7
caps.latest.revision: "21"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: 503f171b2af5e06fd3c890caf07525ba880d0658
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="properties-of-connectors"></a>连接线的属性
连接器表示在生成的设计器中的域关系。  
  
 有关详细信息，请参阅[如何定义域特定语言](../modeling/how-to-define-a-domain-specific-language.md)。 有关如何使用这些属性的详细信息，请参阅[自定义和扩展的域特定语言](../modeling/customizing-and-extending-a-domain-specific-language.md)。  
  
 连接器具有下表中列出的属性。  
  
|属性|描述|默认|  
|--------------|-----------------|-------------|  
|颜色|此连接器的颜色。|黑色|  
|短划线样式|此连接器 （实线、 短划线、 句点、 DashDot、 DashDotDot 或自定义） 的行短划线样式。|单色|  
|源结束样式|此连接器 （HollowArrow、 EmptyArrow、 FilledArrow、 EmptyDiamond、 FilledDiamond，或无） 源最终样式。|无|  
|目标端样式|此连接器 （HollowArrow、 EmptyArrow、 FilledArrow、 EmptyDiamond、 FilledDiamond，或无） 目标结束样式。|无|  
|文本颜色|用于与该连接器关联的文本修饰器颜色。|黑色|  
|Thickness|对于此连接器，以英寸为单位测量线条的粗度。|0.03125|  
|访问修饰符|类的访问级别 (`public`或`internal`)。|Public|  
|自定义特性|用于将属性添加到从此连接器生成的源代码类。|\<无 >|  
|生成双派生|如果`True`，将生成的基本类和分部类 （以支持通过替代的自定义）。 有关详细信息，请参阅[重写和扩展生成的类](../modeling/overriding-and-extending-the-generated-classes.md)。|False|  
|具有自定义的构造函数|如果`True`，自定义的构造函数将提供的源代码中。 有关详细信息，请参阅[重写和扩展生成的类](../modeling/overriding-and-extending-the-generated-classes.md)。|False|  
|继承修饰符|描述从连接器生成源代码类的继承的类型 (`none`，`abstract`或`sealed`)。|无|  
|基连接器|此连接器的基类。|(无)|  
|名称|此连接器的名称。|当前的名称|  
|命名空间|与此连接器关联的命名空间。|当前命名空间|  
|工具提示类型|如何定义工具提示 （固定的变量，或无）。 如果固定，然后的值`Fixed Tooltip Text`属性用作工具提示; 如果变量，工具提示将定义自定义代码中。|\<无 >|  
|说明|与此连接器关联的非正式说明。|\<无 >|  
|路由样式|用于路由连接器样式。 A`Rectilinear`连接器使根据需要; 直角打开`Straight`连接器却没有。|直线|  
|作为属性公开的颜色<br /><br /> 作为属性公开的短划线样式<br /><br /> 作为属性公开的粗细<br /><br /> 公开文本颜色|如果`True`，用户可以设置形状的规定的属性。 若要对此设置，请右击形状定义，然后单击**添加公开**。|False|  
|描述|用于记录生成的设计器。|\<无 >|  
|显示名称|将此连接器的生成设计器中显示的名称。|\<无 >|  
|固定的工具提示文本|适用于固定的工具提示文本。|\<无 >|  
|帮助关键字|用于编制索引此元素的 F1 帮助关键字。|\<无 >|  
  
## <a name="see-also"></a>另请参阅  
 [域特定语言工具词汇表](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)