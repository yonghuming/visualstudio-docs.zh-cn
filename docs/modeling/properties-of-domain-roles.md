---
title: "域角色的属性 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5a7bb18c-638e-45e8-9d79-9aa6a9e14b0e
caps.latest.revision: "9"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: e85c47133509e3f7bf7c54b8cfa7f2121a26b04b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="properties-of-domain-roles"></a>域角色的属性
下表中的属性是与域角色关联。 有关域角色的信息，请参阅[了解模型、 类和关系](../modeling/understanding-models-classes-and-relationships.md)。 有关如何使用这些属性的详细信息，请参阅[自定义和扩展的域特定语言](../modeling/customizing-and-extending-a-domain-specific-language.md)。  
  
|属性|描述|默认|  
|--------------|-----------------|-------------|  
|集合类型|如果此角色的重数为 0..* 或 1...\*，此属性自定义的泛型类型的用于存储的链接集合。|`(none)` - <xref:Microsoft.VisualStudio.Modeling.LinkedElementCollection%601>使用|  
|自定义特性|你在此处指定的属性将作为属性添加到生成的代码类。|< 无\>|  
|属性是可浏览|如果`True`，如果关系的多重性为 0..1 或 1..1，可浏览的角色属性中的用户和**属性**窗口。 属性显示在另一端的关系链接的元素的名称。|`True`|  
|为属性生成器|如果`True`，对于此角色，你可以使用遍历关系在程序代码中的生成角色属性。 如果设置 false，则你可以通过使用静态方法的域关系效率较低的方式遍历关系。|`True`|  
|属性 Getter 的访问修饰符|为生成的属性 getter 的访问修饰符 (`public`， `internal`， `private`， `protected`，或`protected internal`)。|`public`|  
|属性 Setter 的访问修饰符|生成的属性的 setter 的访问修饰符 (`public`， `internal`， `private`， `protected`，或`protected internal`)。|`public`|  
|重数|这可以播放相反的角色的模型元素的数目 (`0..1`， `1..1`， `0..*`，或`1..*`)。 如果重数`0..*`或`1..*`，则生成的属性表示的集合; 否则，生成的属性表示单个模型元素。|依赖于的关系类型和是否这是关系中的源或目标的角色。|  
|名称|域角色的名称。 此属性不能包含空格。|此角色的角色扮演者域类的名称。|  
|传播复制|`DoNotPropagateCopy`-复制的角色扮演者将拥有此链接的任何副本。<br /><br /> `PropagateCopyToLinkOnly`-将复制的链接将指向现有相反角色扮演者。<br /><br /> `PropagateCopyToLinkAndOppositeRolePlayer`-将复制的链接指向一份相反角色扮演者。|`PropagateCopyToLinkAndOppositeRolePlayer`嵌入的源角色。<br /><br /> `DoNotPropagateCopy`对于其他角色。<br /><br /> 有关详细信息，请参阅[自定义复制行为](../modeling/customizing-copy-behavior.md)|  
|传播删除|`True`若要删除在此角色时删除的关联的链接，播放的元素。|`True`对于嵌入的角色的目标。<br /><br /> `False`对于其他角色。<br /><br /> 有关详细信息，请参阅[自定义删除行为](../modeling/customizing-deletion-behavior.md)。|  
|属性名|角色扮演者的代码中生成的属性名称。 此名称不能包含空格。|如果此角色具有零到一个相反的角色的名称或一对一的重数;否则为 pluralized 相反的角色的名称。|  
|角色扮演者|元素可在关系中充当此角色的域类。 此属性是只读的。|为此角色的角色扮演者域类。|  
|说明|与域角色关联的非正式说明。|< 无\>|  
|类别|在其下生成的属性将显示在类别**属性**生成设计器窗口中的。 如果此属性为空，则生成的属性显示在**杂项**类别|< 无\>|  
|描述|说明用于记录的代码并在生成的设计器 UI 中使用。<br /><br /> 描述将显示在角色播放器类上生成的属性的 Intellisense 工具提示。|`Description for`*角色的完整名称*|  
|显示名称|域角色的生成设计器中显示的名称。|Name 属性的调整后的值。|  
|帮助关键字|可选关键字用于编制索引的域角色的 F1 帮助。|\<无 >|  
|属性显示名称|生成的角色属性的生成设计器中显示的名称。|调整后的值的属性名称属性。|  
  
> [!NOTE]
>  显示名称的默认值基于关联的属性值插入每个大写字符小写字符前面和不跟另一个大写字符之前的空格。  
  
## <a name="see-also"></a>另请参阅  
 [域关系的属性](../modeling/properties-of-domain-relationships.md)