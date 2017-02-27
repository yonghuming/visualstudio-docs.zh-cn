---
title: "连接线的属性 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "域特定语言, 连接线"
ms.assetid: b1f24e8d-cdd7-4a5d-af37-1038f43b45c7
caps.latest.revision: 21
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 21
---
# 连接线的属性
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

连接表示在一个生成的设计器的域关系。  
  
 有关更多信息，请参见 [如何定义域特定语言](../modeling/how-to-define-a-domain-specific-language.md)。  有关如何使用这些属性的更多信息，请参见 [自定义和扩展域特定语言](../modeling/customizing-and-extending-a-domain-specific-language.md)。  
  
 连接具有下表中列出的属性。  
  
|属性|说明|默认|  
|--------|--------|--------|  
|Color|此连接的颜色。|Black|  
|虚线样式|行的虚线样式此连接 \(纯、短划线、句点、 DashDot、 DashDotDot 或自定义\)。|实心填充|  
|源端的样式|此连接 \(HollowArrow、 EmptyArrow、 FilledArrow、 EmptyDiamond， FilledDiamond 或无\) 源端的样式。|无|  
|以结束样式|此连接 \(HollowArrow、 EmptyArrow、 FilledArrow、 EmptyDiamond， FilledDiamond 或无\) 目标端样式。|无|  
|文本颜色|为文本修饰器使用与此连接的颜色。|Black|  
|Thickness|行的粗细此连接的， \(以英寸。|0.03125|  
|访问修饰符|类的访问级别 \(`public` 或 `internal`\)。|Public|  
|自定义特性|用于将特性添加到从此连接生成的源代码类别。|\<none\>|  
|生成派生的二进制文件|如果 `True`，基类和分部类 \(支持自定义通过重写\) 将生成。  有关更多信息，请参见 [重写和扩展生成的类](../modeling/overriding-and-extending-the-generated-classes.md)。|False|  
|具有自定义构造函数|如果 `True`，自定义构造函数在源代码中提供。  有关更多信息，请参见 [重写和扩展生成的类](../modeling/overriding-and-extending-the-generated-classes.md)。|False|  
|继承修饰符|描述用于从连接源代码类的继承 \(`none`、 `abstract` 或 `sealed`\) 创建。|无|  
|基于连接|此连接基类。|（无）|  
|名称|此连接的名称。|当前名称|  
|命名空间|参与此连接的命名空间。|当前命名空间|  
|工具提示类型|工具提示的定义方式 \(修复，变量或无\)。  如果修复， `Fixed Tooltip Text` 属性的值然后使用作为工具提示;如果变量，工具提示在自定义代码并定义。|\<none\>|  
|注释|与此连接的非正式的说明。|\<none\>|  
|路由样式|为路由连接线使用的样式。  `Rectilinear` 连接进行最后的将变为根据要求; `Straight` 连接不。|线性|  
|为属性显示的颜色<br /><br /> 为属性显示的虚线样式<br /><br /> 为属性显示的粗细<br /><br /> 公开文本颜色|如果 `True`，用户可以设置形状提出的属性。  若要设置此属性，请右击形状定义然后单击 **将显示**。|False|  
|说明|用于文档生成的设计器。|\<none\>|  
|显示名称|此连接的生成的设计器中显示的名称。|\<none\>|  
|内置的工具提示文本|为内置的工具提示使用的文本。|\<none\>|  
|帮助关键字|在索引 F1 帮助涉及此元素的关键字。|\<none\>|  
  
## 请参阅  
 [Domain\-Specific Language Tools Glossary](http://msdn.microsoft.com/zh-cn/ca5e84cb-a315-465c-be24-76aa3df276aa)