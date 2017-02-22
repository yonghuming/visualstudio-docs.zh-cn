---
title: "图像形状的属性 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.dsltools.dsldesigner.selectimagedialog"
  - "vs.dsltools.dsldesigner.imageshape"
helpviewer_keywords: 
  - "域特定语言, 图像形状"
ms.assetid: 9ce00ccd-07f2-4640-ac96-2a60481d0d72
caps.latest.revision: 25
caps.handback.revision: 25
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# 图像形状的属性
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可以使用图形形状指定字段类如何显示在一个已生成的设计器。  通过设置类的 `Image` 属性定义图像形状到预定义的图像文件。  以下格式支持:  
  
-   .gif  
  
-   .jpg  
  
-   .jpeg  
  
-   .bmp  
  
-   .wmf  
  
-   .emf  
  
-   .png  
  
 默认情况下，设计器资源文件，如图像文件，位于 **DSL** 项目的 **资源**文件夹。  
  
 有关更多信息，请参见 [如何定义域特定语言](../modeling/how-to-define-a-domain-specific-language.md)。  有关如何使用这些属性的更多信息，请参见 [自定义和扩展域特定语言](../modeling/customizing-and-extending-a-domain-specific-language.md)。  
  
 图像形状具有下表中列出的属性。  
  
|属性|说明|默认|  
|--------|--------|--------|  
|填充颜色|形状的填充颜色。|白色|  
|渐变填充模式|形状加载渐变模式。|Horizontal|  
|具有默认连接点|如果 `True`，形状将使用顶部，底部，左侧和右侧在编辑器中生成的设计器连接点。|False|  
|轮廓颜色|形状的轮廓颜色。|Black|  
|大纲显示虚线样式|大纲显示虚线样式形状 \(纯、短划线、句点、 DashDot、 DashDotDot 或自定义\)。|实心填充|  
|轮廓粗细|形状的轮廓粗细。|0.03125|  
|文本颜色|为文本修饰器使用与形状的颜色。|Black|  
|访问修饰符|几何形状的访问修饰符 \(公共或内部\)。|Public|  
|自定义特性|用于将特性添加到从形状生成的源代码类别。|\<none\>|  
|生成派生的二进制文件|如果 `True`，基类和分部类 \(支持自定义通过重写\) 将生成。  有关更多信息，请参见 [重写和扩展生成的类](../modeling/overriding-and-extending-the-generated-classes.md)。|False|  
|具有自定义构造函数|如果 `True`，自定义构造函数在源代码中提供。  有关更多信息，请参见 [重写和扩展生成的类](../modeling/overriding-and-extending-the-generated-classes.md)。|False|  
|继承修饰符|描述用于从图像形状源代码类的继承 \(`none`、 `abstract` 或 `sealed`\) 创建。|无|  
|基本图形形状|形状基类。|（无）|  
|名称|形状的名称。|当前名称|  
|命名空间|参与和形状的命名空间。|当前命名空间|  
|工具提示类型|工具提示中定义的位置 \(修复，变量或无\)。  如果修复， `Fixed Tooltip Text` 属性的值然后使用作为工具提示;如果变量，工具提示在自定义代码并定义。|无|  
|注释|与此形状的非正式的说明。|\<none\>|  
|初始高度|初始高度形状，在英寸。|1|  
|初始宽度|形状的初始宽度，在英寸。|1.5|  
|为属性显示的填充颜色<br /><br /> 显示的渐变填充模式<br /><br /> 为属性显示的轮廓颜色<br /><br /> 为属性显示的大纲显示虚线样式<br /><br /> 为属性显示的轮廓粗细<br /><br /> 公开文本颜色|如果 `True`，用户可以设置形状提出的属性。  若要设置此属性，请右击形状定义然后单击 **将显示**。|False|  
|说明|用于文档生成的设计器。|\<none\>|  
|显示名称|此形状的生成的设计器中显示的名称。|\<none\>|  
|内置的工具提示文本|为内置的工具提示使用的文本。|\<none\>|  
|帮助关键字|在索引 F1 帮助涉及此元素的关键字。|\<none\>|  
|Image|为形状使用的图像文件的路径。|\<none\>|  
  
## 请参阅  
 [Domain\-Specific Language Tools Glossary](http://msdn.microsoft.com/zh-cn/ca5e84cb-a315-465c-be24-76aa3df276aa)