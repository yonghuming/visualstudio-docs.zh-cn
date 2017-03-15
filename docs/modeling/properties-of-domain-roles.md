---
title: "域角色的属性 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5a7bb18c-638e-45e8-9d79-9aa6a9e14b0e
caps.latest.revision: 9
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 9
---
# 域角色的属性
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

属性在下表中与字段角色。  有关字段角色的信息，请参见 [了解模型、类和关系](../modeling/understanding-models-classes-and-relationships.md)。  有关如何使用这些属性的更多信息，请参见 [自定义和扩展域特定语言](../modeling/customizing-and-extending-a-domain-specific-language.md)。  
  
|属性|说明|默认|  
|--------|--------|--------|  
|集合类型|如果此角色具有重数为 0。\* 或 1. \*，此属性来自定义用于存储链接的集合的泛型类型。|`(none)`\- 使用 <xref:Microsoft.VisualStudio.Modeling.LinkedElementCollection%601>|  
|自定义特性|属性可以在此处指定要添加为特性到生成的代码类。|\<none\>|  
|可浏览的属性|如果 `True`，并且，如果该关系的重数 0..1 是或 1..1，角色属性可以由 **属性** 窗口的用户浏览。  属性显示该元素的名称在关系链接的另一端。|`True`|  
|是属性生成器|如果 `True`，角色特性为此角色生成，可以使用遍历在程序代码中的关系。  如果将此错误，通过使用域关系的静态方法，可以遍历关系以较低的最有效方法。|`True`|  
|属性 getter 访问修饰符|getter 的访问修饰符生成的属性 \(`public`、 `internal`、 `private`、 `protected`或 `protected internal`\)。|`public`|  
|属性 setter 访问修饰符|setter 的访问修饰符生成的属性 \(`public`、 `internal`、 `private`、 `protected`或 `protected internal`\)。|`public`|  
|重数|可以模拟该对方角色的模型元素个数 \(`0..1`、 `1..1`、 `0..*`或 `1..*`\)。  如果重数是 `0..*` 或 `1..*`，则生成的属性表示集合;否则，所生成的属性表示一个模型元素。|依赖关系类型，并且这是在关系的源或目标效果。|  
|名称|字段角色的名称。  此属性不能包含空格。|角色扮演者的域类的名称此角色的。|  
|传播复制|`DoNotPropagateCopy` \- 复制的角色扮演者没有此链接的副本。<br /><br /> `PropagateCopyToLinkOnly` \- 了复制的链接指向现有角色中扮演者相反。<br /><br /> `PropagateCopyToLinkAndOppositeRolePlayer`\- 了复制的链接指向对方角色的扮演者的副本。|嵌入的源角色的`PropagateCopyToLinkAndOppositeRolePlayer` 。<br /><br /> 其他角色的`DoNotPropagateCopy` 。<br /><br /> 有关更多信息，请参见[自定义复制行为](../modeling/customizing-copy-behavior.md)|  
|传播删除|删除模拟此角色的元素的`True` ，这种关联的链接将被删除。|一个嵌入的角色的目标的`True` 。<br /><br /> 其他角色的`False` 。<br /><br /> 有关更多信息，请参见 [自定义删除行为](../modeling/customizing-deletion-behavior.md)。|  
|属性名|在角色扮演者的代码生成的属性的名称。  此名称不能包含空格。|对方角色的，则此角色具有零到一个或一个对的重数的名称;否则，对方角色的 pluralized 名称。|  
|角色扮演者|在关系可以模拟这种影响元素的字段类。  此属性为只读。|角色扮演者的域类此角色的。|  
|注释|与字段角色的非正式的说明。|\<none\>|  
|类别|下所生成的属性显示在编辑器中生成的设计器的 **属性** 窗口的类别下。  如果此属性为 null，则生成的属性显示在类别下 **杂项**|\<none\>|  
|说明|用于记录代码和用于此时将生成的设计器 UI 的说明。<br /><br /> 图例显示在生成的属性的 Intellisense 工具提示在角色扮演者类。|`Description for` *角色的全名*|  
|显示名称|在字段角色的生成的设计器中显示的名称。|name 属性的调整的值。|  
|帮助关键字|在索引 F1 帮助涉及字段角色可选的关键字。|\<none\>|  
|属性显示名称|在生成的角色属性的生成设计器中显示的名称。|属性名属性的调整的值。|  
  
> [!NOTE]
>  显示名称的默认名称基于关联的属性值通过插入在一个小写字母后，而不是由另一个大写字符的每个大写字符之前的空格。  
  
## 请参阅  
 [域关系的属性](../modeling/properties-of-domain-relationships.md)