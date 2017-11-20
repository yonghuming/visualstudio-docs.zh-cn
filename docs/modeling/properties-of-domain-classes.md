---
title: "域类属性 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Domain-Specific Language, domain class
ms.assetid: a3993995-19e7-4761-a972-b1de89131a1b
caps.latest.revision: "21"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: e9bed31caa63a12677e7b9798e6cf72524500c21
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="properties-of-domain-classes"></a>域类的属性
域类具有下表中的属性。 有关域类的信息，请参阅[了解模型、 类和关系](../modeling/understanding-models-classes-and-relationships.md)。 有关如何使用这些属性的详细信息，请参阅[自定义和扩展的域特定语言](../modeling/customizing-and-extending-a-domain-specific-language.md)。  
  
|属性|描述|默认|  
|--------------|-----------------|-------------|  
|访问修饰符|域类的访问级别（`public` 或 `internal`）。|`public`|  
|自定义特性|用于将属性添加到此域类从生成的源代码类。|\<无 >|  
|生成双派生|如果`True`，将生成的基本类和分部类 （以支持通过替代的自定义）。 有关详细信息，请参阅[重写和扩展生成的类](../modeling/overriding-and-extending-the-generated-classes.md)。|`False`|  
|具有自定义的构造函数|如果`True`，自定义的构造函数将提供的源代码中。 有关详细信息，请参阅[重写和扩展生成的类](../modeling/overriding-and-extending-the-generated-classes.md)。|`False`|  
|继承修饰符|描述的域类从生成的源代码类继承的类型 (`none`，`abstract`或`sealed`)。|`none`|  
|基类|如果此域类派生，类的基类的名称。|\<无 >|  
|名称|此域类的名称。|当前的名称|  
|命名空间|此域类的命名空间。|当前命名空间|  
|说明|与此域类相关联的非正式说明。|\<无 >|  
|描述|用于记录生成的设计器的 UI 中的说明。|\<无 >|  
|显示名称|将此域类的生成设计器中显示的名称。|\<无 >|  
|帮助关键字|可选关键字用于编制索引的此域类 F1 帮助。|\<无 >|  
  
## <a name="see-also"></a>另请参阅  
 [域特定语言工具词汇表](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)