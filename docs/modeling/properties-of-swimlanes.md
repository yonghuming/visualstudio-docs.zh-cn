---
title: "泳道属性 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.dsltools.dsldesigner.swimlane"
helpviewer_keywords: 
  - "域特定语言, 泳道"
ms.assetid: 47edbc2d-09e4-48ac-b4d1-5268a06a27e6
caps.latest.revision: 24
caps.handback.revision: 24
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# 泳道属性
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

可以添加泳道到关系图。  泳道除关系图添加到垂直或水平区域。  可以定义要显示的其他形状并在内。  有关更多信息，请参见 [如何定义域特定语言](../modeling/how-to-define-a-domain-specific-language.md)。  有关如何使用这些属性的更多信息，请参见 [自定义和扩展域特定语言](../modeling/customizing-and-extending-a-domain-specific-language.md)。  
  
 泳道具有下表中列出的属性。  
  
|属性|说明|默认|  
|--------|--------|--------|  
|主体填充颜色|条泳道主体的填充颜色。|白色|  
|标头填充颜色|条泳道头的填充颜色。|的深灰色|  
|分隔符颜色|分隔符行的颜色。|浅灰色|  
|分隔符行样式|分隔符行 \(`Solid`、 `Dash`、 `Dot`、 `DashDot`、 `DashDotDot`或 `Custom`\) 的样式。|`Dash`|  
|分隔符粗细|分隔符行的粗细在英寸。|0.03125|  
|文本颜色|为文本修饰器使用与此条泳道的颜色。|Black|  
|访问修饰符|类的访问级别 \(`public` 或 `internal`\)。|Public|  
|自定义特性|用于将特性添加到从此条泳道生成的代码类别。|\<none\>|  
|生成派生的二进制文件|如果 `True`，基类和分部类 \(支持自定义通过重写\) 将生成。  有关更多信息，请参见 [重写和扩展生成的类](../modeling/overriding-and-extending-the-generated-classes.md)。|False|  
|具有自定义构造函数|如果 `True`，自定义构造函数在源代码中提供。  有关更多信息，请参见 [重写和扩展生成的类](../modeling/overriding-and-extending-the-generated-classes.md)。|False|  
|继承修饰符|描述用于从条泳道源代码类的继承 \(`none`、 `abstract` 或 `sealed`\) 创建。|无|  
|基本条泳道|此条泳道基类。|（无）|  
|名称|此条泳道的名称。|当前名称|  
|命名空间|参与此条泳道的命名空间。|当前命名空间|  
|工具提示类型|工具提示的定义方式 \(`fixed`、 `variable`或 `none`\)。  如果为， `Fixed Tooltip Text` 属性的值然后使用 `fixed`;如果 `variable`，工具提示在自定义代码并定义。|\<none\>|  
|注释|与此条泳道的非正式的说明。|\<none\>|  
|对齐方式|水平或垂直对齐方式。|垂直|  
|初始高度|初始高度此条泳道，在英寸。  只适用于级别的泳道。|0|  
|初始宽度|此条泳道的初始宽度，在英寸。  只适用于垂直泳道。|0|  
|公开文本颜色|如果 `True`，用户可以设置一条泳道的颜色在编辑器中生成的设计器的。  若要设置此属性，请右击条泳道形状并单击 **将显示**。|False|  
|说明|用于文档生成的设计器。|\<none\>|  
|显示名称|在编辑器中生成的设计器将显示引用此条泳道类的名称。|\<none\>|  
|内置的工具提示文本|为内置的工具提示使用的文本。|\<none\>|  
|帮助关键字|在索引 F1 帮助对此条泳道的关键字。|\<none\>|  
  
## 请参阅  
 [Domain\-Specific Language Tools Glossary](http://msdn.microsoft.com/zh-cn/ca5e84cb-a315-465c-be24-76aa3df276aa)