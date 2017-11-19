---
title: "关系图的属性 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.dsltools.dsldesigner.dsldiagram
helpviewer_keywords: Domain-Specific Language, diagram
ms.assetid: 00bba4b8-6aa6-4027-96cb-4f4c41a77d3c
caps.latest.revision: "25"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: fcd30a30bdae896be5aceb9dc685a5fb762ee4af
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="properties-of-diagrams"></a>图表属性
你可以设置指定在生成的设计器中显示关系图的外观的属性。 例如，你可以在关系图中指定文本的默认颜色。  
  
 有关详细信息，请参阅[如何定义域特定语言](../modeling/how-to-define-a-domain-specific-language.md)。 有关如何使用这些属性的详细信息，请参阅[自定义和扩展的域特定语言](../modeling/customizing-and-extending-a-domain-specific-language.md)。  
  
 下表列出的属性关系图。  
  
|属性|描述|默认|  
|--------------|-----------------|-------------|  
|填充颜色|关系图填充颜色。|空白|  
|文本颜色|关系图显示的文本颜色。|黑色|  
|访问修饰符|类 （公共或内部） 的访问修饰符。|Public|  
|自定义特性|用于将属性添加到生成的代码类。|\<无 >|  
|生成双派生|如果`True`，将生成的基本类和分部类 （以支持通过替代的自定义）。 有关详细信息，请参阅[重写和扩展生成的类](../modeling/overriding-and-extending-the-generated-classes.md)。|False|  
|具有自定义的构造函数|如果`True`，自定义的构造函数将提供的源代码中。 有关详细信息，请参阅[重写和扩展生成的类](../modeling/overriding-and-extending-the-generated-classes.md)...|False|  
|继承修饰符|描述的关系图生成源代码类的继承的类型 (`none`，`abstract`或`sealed`)。|无|  
|基本图|此关系图的基类。|(无)|  
|名称|此关系图的名称。|当前的名称|  
|命名空间|与此关系图关联的命名空间。|当前命名空间|  
|表示类|此关系图表示根域类。|如果适用的当前根类|  
|说明|与此元素关联的非正式说明。|\<无 >|  
|公开为属性填充颜色|如果`True`，用户可以设置生成的设计器的关系图的填充颜色。 若要对此设置，请右键单击关系图形状，然后单击**添加 Explosed**。|False|  
|将作为属性公开文本颜色|如果`True`，用户可以在生成的设计器中设置关系图的文本颜色。 若要对此设置，请右键单击关系图形状，然后单击**添加 Explosed**。|False|  
|描述|用于记录生成的设计器的说明。|\<无 >|  
|显示名称|将显示在生成的设计器中为此关系图名称。|\<无 >|  
|帮助关键字|用于编制索引为此关系图的 F1 帮助关键字。|\<无 >|  
  
## <a name="see-also"></a>另请参阅  
 [域特定语言工具词汇表](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)