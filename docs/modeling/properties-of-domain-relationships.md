---
title: "属性的域关系 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Domain-Specific Language, domain relationships
ms.assetid: 9ccb3dc2-b80c-4585-932f-3c5f87bafbcd
caps.latest.revision: "20"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: 011be65e453de8f9d8010b74670b4efdf7905d06
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="properties-of-domain-relationships"></a>域关系的属性
下表中的属性是与域关系相关联。 有关域关系的信息，请参阅[了解模型、 类和关系](../modeling/understanding-models-classes-and-relationships.md)。 有关如何使用这些属性的详细信息，请参阅[自定义和扩展的域特定语言](../modeling/customizing-and-extending-a-domain-specific-language.md)。  
  
|属性|描述|默认|  
|--------------|-----------------|-------------|  
|访问修饰符|访问的域关系级别 (`public`或`internal`)。|`public`|  
|自定义特性|用于将属性添加到生成的域关系的源代码类。|\<无 >|  
|生成双派生|如果`True`，生成基类和 （以支持通过替代的自定义） 的分部类。 有关详细信息，请参阅[重写和扩展生成的类](../modeling/overriding-and-extending-the-generated-classes.md)。|`False`|  
|具有自定义的构造函数|如果`True`，指示在源代码中提供的自定义的构造函数。 有关详细信息，请参阅[重写和扩展生成的类](../modeling/overriding-and-extending-the-generated-classes.md)。|`False`|  
|继承修饰符|描述的域关系从生成的源代码类继承的类型 (`none`，`abstract`或`sealed`)。|\<无 >|  
|允许存在重复项|如果`True`，相同的两个元素之间，则可能创建重复的域关系的链接。|`False`|  
|基本关系|如果派生的域关系，域关系的基本关系。|\<无 >|  
|嵌入|如果`True`，域关系是嵌入的关系。 如果`False`，关系是引用关系。|\<同时 >|  
|名称|域关系的名称。|当前的名称|  
|命名空间|隶属于域关系命名空间。|当前命名空间|  
|说明|与域关系相关联的非正式说明。|\<无 >|  
|描述|说明用于记录的代码并在生成的设计器 UI 中使用。|\<无 >|  
|显示名称|域关系的生成设计器中显示的名称。|\<无 >|  
|帮助关键字|可选关键字用于编制索引的域关系的 F1 帮助。|\<无 >|  
  
## <a name="see-also"></a>另请参阅  
 [域特定语言工具词汇表](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)