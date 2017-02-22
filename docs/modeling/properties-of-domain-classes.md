---
title: "域类的属性 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "域特定语言, 域类"
ms.assetid: a3993995-19e7-4761-a972-b1de89131a1b
caps.latest.revision: 21
caps.handback.revision: 21
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# 域类的属性
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

域类具有特性在下表中。  有关字段类的信息，请参见 [了解模型、类和关系](../modeling/understanding-models-classes-and-relationships.md)。  有关如何使用这些属性的更多信息，请参见 [自定义和扩展域特定语言](../modeling/customizing-and-extending-a-domain-specific-language.md)。  
  
|属性|说明|默认|  
|--------|--------|--------|  
|访问修饰符|域类的访问级别 \(`public` 或 `internal`\)。|`public`|  
|自定义特性|用于将特性添加到从此字段类生成的源代码类别。|\<none\>|  
|生成派生的二进制文件|如果 `True`，基类和分部类 \(支持自定义通过重写\) 将生成。  有关更多信息，请参见 [重写和扩展生成的类](../modeling/overriding-and-extending-the-generated-classes.md)。|`False`|  
|具有自定义构造函数|如果 `True`，自定义构造函数在源代码中提供。  有关更多信息，请参见 [重写和扩展生成的类](../modeling/overriding-and-extending-the-generated-classes.md)。|`False`|  
|继承修饰符|描述用于从域类源代码类的继承 \(`none`、 `abstract` 或 `sealed`\) 创建。|`none`|  
|基类|如果此字段类派生，基类的名称。|\<none\>|  
|名称|此字段类的名称。|当前名称|  
|命名空间|此字段类命名空间。|当前命名空间|  
|注释|与此字段类的非正式的说明。|\<none\>|  
|说明|用于文档此时将生成的设计器 UI 的说明。|\<none\>|  
|显示名称|此字段类的生成的设计器中显示的名称。|\<none\>|  
|帮助关键字|在索引 F1 帮助了该字段类可选的关键字。|\<none\>|  
  
## 请参阅  
 [Domain\-Specific Language Tools Glossary](http://msdn.microsoft.com/zh-cn/ca5e84cb-a315-465c-be24-76aa3df276aa)