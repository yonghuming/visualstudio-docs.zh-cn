---
title: "修饰器的属性 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "域特定语言, 修饰符"
ms.assetid: f6322fe5-dc08-4d32-a6b3-0bd18879136d
caps.latest.revision: 23
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 23
---
# 修饰器的属性
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

修饰器是图标，文本或展开\/能出现在形状或连接器在关系图的折叠 V 形按钮  下表显示了三的特性修饰器。  某些属性仅出现在形状修饰器或在连接修饰器。  
  
 有关更多信息，请参见 [如何定义域特定语言](../modeling/how-to-define-a-domain-specific-language.md)。  有关如何使用这些属性的更多信息，请参见 [自定义和扩展域特定语言](../modeling/customizing-and-extending-a-domain-specific-language.md)。  
  
## 展开\/折叠修饰器  
  
|属性|说明|默认|  
|--------|--------|--------|  
|DisplayName|在编辑器中生成的设计器将显示修饰器的名称。|展开折叠修饰器|  
|名称|修饰器的名称。|ExpandCollapseDecorator|  
|注释|与此修饰器的非正式的说明。|\<none\>|  
|HorizontalOffset|级别的偏移量，相对于修饰器的默认位置，在英寸。  \(仅在形状。\)|0|  
|VerticalOffset|垂直偏移量，相对于修饰器的默认位置，在英寸。  \(仅在形状。\)|0|  
|OffsetFromLine|修饰器的偏移量行的，相对于其默认位置，在英寸。  \(仅在连接。\)|0|  
|OffsetFromShape|修饰器的偏移量形状的，相对于其默认位置，在英寸。  \(仅在连接。\)|0|  
|Position|修饰器的默认位置。|SourceTop|  
  
## 图标修饰器  
  
|属性|说明|默认|  
|--------|--------|--------|  
|DefaultIcon|要显示的图标或图像文件的路径。|\<none\>|  
|DisplayName|在生成的设计器中显示的修饰器的名称。|图标修饰器|  
|名称|修饰器的名称。|IconDecorator|  
|注释|与一个修饰器的非正式的说明。|\<none\>|  
|HorizontalOffset|级别的偏移量，相对于修饰器的默认位置，在英寸。  \(仅在形状。\)|0|  
|VerticalOffset|垂直偏移量，相对于修饰器的默认位置，在英寸。  \(仅在形状。\)|0|  
|OffsetFromLine|修饰器的偏移量行的，相对于其默认位置，在英寸。  \(仅在连接。\)|0|  
|OffsetFromShape|修饰器的偏移量形状的，相对于其默认位置，在英寸。  \(仅在连接。\)|0|  
|Position|修饰器的默认位置。|SourceTop|  
  
## TextDecorator  
  
|属性|说明|默认|  
|--------|--------|--------|  
|DefaultText|要显示的默认文本。|Label|  
|DisplayName|在生成的设计器中显示的修饰器的名称。|Label|  
|FontSize|在编辑器中修饰器中显示的文本的字体大小。|8|  
|FontStyle|在编辑器中修饰器中显示的文本的字体样式。|规则|  
|名称|修饰器的名称。|Label|  
|注释|与一个修饰器的非正式的说明。|\<none\>|  
|HorizontalOffset|级别的偏移量，相对于修饰器的默认位置，在英寸。  \(仅在形状。\)|0|  
|VerticalOffset|垂直偏移量，相对于修饰器的默认位置，在英寸。  \(仅在形状。\)|0|  
|OffsetFromLine|修饰器的偏移量行的，相对于其默认位置，在英寸。  \(仅在连接。\)|0|  
|OffsetFromShape|修饰器的偏移量形状的，相对于其默认位置，在英寸。  \(仅在连接。\)|0|  
|Position|修饰器的默认位置。|TargetBottom|  
  
## 请参阅  
 [Domain\-Specific Language Tools Glossary](http://msdn.microsoft.com/zh-cn/ca5e84cb-a315-465c-be24-76aa3df276aa)