---
title: "图表属性 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.dsltools.dsldesigner.dsldiagram"
helpviewer_keywords: 
  - "域特定语言, 关系图"
ms.assetid: 00bba4b8-6aa6-4027-96cb-4f4c41a77d3c
caps.latest.revision: 25
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 25
---
# 图表属性
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

可以设置中指定的属性关系图如何将显示一个生成的设计器。  例如，可以为文本指定默认颜色在关系图上。  
  
 有关更多信息，请参见 [如何定义域特定语言](../modeling/how-to-define-a-domain-specific-language.md)。  有关如何使用这些属性的更多信息，请参见 [自定义和扩展域特定语言](../modeling/customizing-and-extending-a-domain-specific-language.md)。  
  
 下表列出了关系图的属性。  
  
|属性|说明|默认|  
|--------|--------|--------|  
|填充颜色|关系图的填充颜色。|白色|  
|文本颜色|在关系图上显示文本的颜色。|Black|  
|访问修饰符|类的访问修饰符 \(公共或内部\)。|Public|  
|自定义特性|用于将特性添加到生成的代码类别。|\<none\>|  
|生成派生的二进制文件|如果 `True`，基类和分部类 \(支持自定义通过重写\) 将生成。  有关更多信息，请参见 [重写和扩展生成的类](../modeling/overriding-and-extending-the-generated-classes.md)。|False|  
|具有自定义构造函数|如果 `True`，自定义构造函数在源代码中提供。  有关更多信息，请参见[重写和扩展生成的类](../modeling/overriding-and-extending-the-generated-classes.md)。|False|  
|继承修饰符|描述用于从关系图源代码类的继承 \(`none`、 `abstract` 或 `sealed`\) 创建。|无|  
|基本关系图|此关系图基类。|（无）|  
|名称|此关系图的名称。|当前名称|  
|命名空间|参与此关系图的命名空间。|当前命名空间|  
|一个类|此关系图表示的根域类。|当前根类 \(如果适用\)。|  
|注释|与此元素关联的非正式的说明。|\<none\>|  
|公开为属性的填充颜色|如果 `True`，用户可以设置由生成的设计器的关系图的填充颜色。  若要设置此属性，请右击关系图形状并单击 **添加 Explosed**。|False|  
|公开为属性的文本颜色|如果 `True`，用户可以设置关系图的文本颜色。此时将生成的设计器的。  若要设置此属性，请右击关系图形状并单击 **添加 Explosed**。|False|  
|说明|用于文档此时将生成的设计器的说明。|\<none\>|  
|显示名称|此关系图上的生成的设计器中显示的名称。|\<none\>|  
|帮助关键字|在索引 F1 帮助涉及此关系图的关键字。|\<none\>|  
  
## 请参阅  
 [Domain\-Specific Language Tools Glossary](http://msdn.microsoft.com/zh-cn/ca5e84cb-a315-465c-be24-76aa3df276aa)