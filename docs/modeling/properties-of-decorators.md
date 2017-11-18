---
title: "修饰器的属性 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Domain-Specific Language, decorators
ms.assetid: f6322fe5-dc08-4d32-a6b3-0bd18879136d
caps.latest.revision: "23"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: 23288d1afe9b9c0a181a5d978b1956071b683218
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="properties-of-decorators"></a>修饰器的属性
修饰符是图标、 文本或可以显示在形状或关系图上的连接器的展开/折叠 v 形。 下表显示三种类型的修饰的属性。 某些属性会显示仅在形状修饰符或仅连接器修饰符。  
  
 有关详细信息，请参阅[如何定义域特定语言](../modeling/how-to-define-a-domain-specific-language.md)。 有关如何使用这些属性的详细信息，请参阅[自定义和扩展的域特定语言](../modeling/customizing-and-extending-a-domain-specific-language.md)。  
  
## <a name="expandcollapse-decorator"></a>展开/折叠修饰器  
  
|属性|描述|默认|  
|--------------|-----------------|-------------|  
|DisplayName|修饰器，将生成的设计器中显示的名称。|展开折叠修饰器|  
|名称|修饰名称。|ExpandCollapseDecorator|  
|说明|与此修饰器相关联的非正式说明。|\<无 >|  
|HorizontalOffset|水平偏移量，相对于修饰器，以英寸为单位的默认位置。 （在形状上仅。）|0|  
|VerticalOffset|垂直偏移量，相对于修饰器，以英寸为单位的默认位置。 （在形状上仅。）|0|  
|OffsetFromLine|从行，相对于其默认位置，以英寸为单位修饰器偏移量。 （在连接器仅。）|0|  
|OffsetFromShape|从该形状，相对于其默认位置，以英寸为单位修饰器偏移量。 （在连接器仅。）|0|  
|位置|修饰器默认位置。|SourceTop|  
  
## <a name="icon-decorator"></a>图标修饰器  
  
|属性|描述|默认|  
|--------------|-----------------|-------------|  
|DefaultIcon|要显示的图标或图像文件的路径。|\<无 >|  
|DisplayName|修饰器要在生成的设计器中显示的名称。|图标修饰器|  
|名称|修饰名称。|IconDecorator|  
|说明|与修饰器相关联的非正式说明。|\<无 >|  
|HorizontalOffset|水平偏移量，相对于修饰器，以英寸为单位的默认位置。 （在形状上仅。）|0|  
|VerticalOffset|垂直偏移量，相对于修饰器，以英寸为单位的默认位置。 （在形状上仅。）|0|  
|OffsetFromLine|从行，相对于其默认位置，以英寸为单位修饰器偏移量。 （在连接器仅。）|0|  
|OffsetFromShape|从该形状，相对于其默认位置，以英寸为单位修饰器偏移量。 （在连接器仅。）|0|  
|位置|修饰器默认位置。|SourceTop|  
  
## <a name="textdecorator"></a>划线 TextDecorator  
  
|属性|描述|默认|  
|--------------|-----------------|-------------|  
|DefaultText|要显示的默认文本。|标签|  
|DisplayName|修饰器要在生成的设计器中显示的名称。|标签|  
|FontSize|如所示修饰器文本的字体大小。|8|  
|FontStyle|如所示修饰器文本的字体样式。|规则|  
|名称|修饰名称。|标签|  
|说明|与修饰器相关联的非正式说明。|\<无 >|  
|HorizontalOffset|水平偏移量，相对于修饰器，以英寸为单位的默认位置。 （在形状上仅。）|0|  
|VerticalOffset|垂直偏移量，相对于修饰器，以英寸为单位的默认位置。 （在形状上仅。）|0|  
|OffsetFromLine|从行，相对于其默认位置，以英寸为单位修饰器偏移量。 （在连接器仅。）|0|  
|OffsetFromShape|从该形状，相对于其默认位置，以英寸为单位修饰器偏移量。 （在连接器仅。）|0|  
|位置|修饰器默认位置。|TargetBottom|  
  
## <a name="see-also"></a>另请参阅  
 [域特定语言工具词汇表](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)