---
title: "几何形状的属性 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.dsltools.dsldesigner.geometryshape
helpviewer_keywords:
- Domain-Specific Language, geometry shape
ms.assetid: 3993a23e-eab3-4ceb-b475-c395d5992bfc
caps.latest.revision: 21
author: alancameronwills
ms.author: awills
manager: douge
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 54e600e5d626828824d5a2584e1ff4f7fdc09810
ms.lasthandoff: 02/22/2017

---
# <a name="properties-of-geometry-shapes"></a>几何形状的属性
几何形状可用于指定的域类的实例在域特定语言中的显示方式。 有关详细信息，请参阅[如何定义 Domain-specific Language](../modeling/how-to-define-a-domain-specific-language.md)。 有关如何使用这些属性的详细信息，请参阅[自定义和扩展域特定语言](../modeling/customizing-and-extending-a-domain-specific-language.md)。  
  
 几何形状具有下表中列出的属性。  
  
|属性|说明|默认|  
|--------------|-----------------|-------------|  
|填充颜色|此形状的填充颜色。|白色|  
|填充渐变的模式|此形状 （水平、 垂直、 正向对角线、 后向对角线或无） 填充渐变的模式。|水平|  
|几何|此形状 （矩形、 圆角矩形、 椭圆或圆） 的几何图形。|矩形|  
|具有默认连接点|如果`True`，形状将使用顶部、 底部、 左侧，以及在生成的设计器中正确的连接点。|False|  
|轮廓颜色|此形状的轮廓颜色。|黑色|  
|轮廓短划线样式|此形状 （实线、 虚线、 圆点、 DashDot、 DashDotDot 或自定义） 轮廓短划线样式。|单色|  
|轮廓粗细|此形状轮廓粗细。|0.03125|  
|文本颜色|用于与此形状相关联的文本修饰器颜色。|黑色|  
|访问修饰符|类 （公共或内部） 的访问修饰符。|Public|  
|自定义特性|用于将属性添加到此形状为生成的源代码类。|\<无&1;>|  
|生成双派生|如果`True`，将生成基类的类和分部类 （以支持通过重写的自定义）。 有关详细信息，请参阅[重写和扩展生成的类](../modeling/overriding-and-extending-the-generated-classes.md)。|False|  
|具有自定义构造函数|如果`True`，将在源代码中提供一个自定义的构造函数。 有关详细信息，请参阅[重写和扩展生成的类](../modeling/overriding-and-extending-the-generated-classes.md)。|False|  
|继承修饰符|描述的源的代码生成的类的是从 shape 继承的类型 (`none`，`abstract`或`sealed`)。|无|  
|基本几何形状|此形状的基类。|（无）|  
|名称|此形状的名称。|当前的名称|  
|Namespace|与此形状相关联的命名空间。|当前命名空间|  
|工具提示类型|如何为工具提示定义的 （固定的变量，或无）。 如果修复，然后的值`Fixed Tooltip Text`属性用作工具提示; 如果变量时，工具提示定义自定义代码中。|无|  
|备注|与此元素相关联的非正式说明。|\<无&1;>|  
|初始高度|此形状，以英寸为单位的初始高度。|1|  
|初始宽度|此形状，以英寸为单位的初始宽度。|1.5|  
|作为属性公开的填充颜色<br /><br /> 公开的填充渐变模式<br /><br /> 作为属性公开轮廓颜色<br /><br /> 作为属性公开轮廓短划线样式<br /><br /> 公开为属性的轮廓粗细<br /><br /> 显示的文本颜色|如果`True`，用户可以设置形状的规定的属性。 若要设置此，右键单击形状定义，然后单击**公开添加**。|False|  
|说明|用于记录生成的设计器中的说明。|\<无&1;>|  
|显示名称|将此形状的生成设计器中显示的名称。|\<无&1;>|  
|固定的工具提示文本|用于固定的工具提示文本。|\<无&1;>|  
|帮助关键字|用于索引此形状的 F1 帮助关键字。|\<无&1;>|  
  
## <a name="see-also"></a>另请参阅  
 [域特定语言工具词汇表](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)
