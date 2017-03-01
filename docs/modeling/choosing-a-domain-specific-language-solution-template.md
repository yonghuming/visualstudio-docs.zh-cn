---
title: "选择域特定语言解决方案模板 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language Tools, solution templates
ms.assetid: 9c05955f-1548-4df6-b09b-4b348823c237
caps.latest.revision: 24
author: alancameronwills
ms.author: awills
manager: douge
translationtype: Machine Translation
ms.sourcegitcommit: fd26c504273cae739ccbeef5e406891def732985
ms.openlocfilehash: 2a1ad374c709b9575ff8e3d46bb3d2178a1c3f95
ms.lasthandoff: 02/22/2017

---
# <a name="choosing-a-domain-specific-language-solution-template"></a>选择域特定语言解决方案模板
若要创建域特定语言解决方案，请选择域特定语言设计器向导中可用的解决方案模板之一。 通过选择最近似你想要创建的语言的模板，您可以尽量减少您必须对起始解决方案进行的修改。  
  
 下面的解决方案模板是在域特定语言设计器向导中可用。  
  
|模板|功能|说明|  
|--------------|--------------|-----------------|  
|类关系图|-隔离舱形状<br />类的继承<br />关系继承<br />形状继承<br />-关系属性|如果您的域特定语言包含的实体和关系具有属性，请使用此解决方案模板。 该模板创建类似于 UML 类图的特定于域的语言。 三大要素是类和接口，与关联、 泛化和实现关系。 类或接口显示为一个包含属性的列表框。|  
|组件图|-端口|如果您的域特定语言包括组件，即，软件系统的部分，请使用此解决方案模板。 该模板创建类似于 UML 组件图的特定于域的语言。 三大要素是组件及显示为小形状外侧的组件的端口。|  
|任务数据流关系图|-映像和几何形状<br />-   *泳道*|如果您的域特定语言包括工作流、 状态或序列，请使用此解决方案模板。 该模板创建类似于 UML 活动图的特定于域的语言。 主实体是一种活动，并且主关系是活动之间的转换。 该模板包含多个其他元素，如启动状态，最终状态，并同步栏。|  
|最小语言|的一个类和形状<br />-一个关系和连接符|如果您的域特定语言不同于其他模板，请使用此解决方案模板。 此模板创建具有两个类和一个关系，以表示域特定语言**工具箱**作为**框**和**行**。 类和关系有示例字符串属性。|  
|最小 WinForm 设计器|-A 小型模型。<br />的显示模型一个 Windows 窗体。|如果您想要生成的 DSL 绑定到 Windows 窗体，而不是一个图形设计器的应用程序，请使用此模板。<br /><br /> 窗体，它就像该语言的用户界面是 Dsl\UI 的文件夹中。<br /><br /> 在打开窗体设计器之前，应生成项目。<br /><br /> 有关详细信息，请参阅[创建 Windows Forms-Based 域特定语言](../modeling/creating-a-windows-forms-based-domain-specific-language.md)。|  
|最小 WPF 设计器|-A 小型模型<br />的显示模型一个 Windows Presentation Foundation 用户界面|如果您想要生成的 DSL 绑定到 WPF 用户界面，而不是一个图形设计器的应用程序，请使用此模板。<br /><br /> 用户界面的设计器处于文件夹 Dsl\UI。<br /><br /> 在打开用户界面设计器之前，应生成项目。<br /><br /> 有关详细信息，请参阅[创建 WPF-Based 域特定语言](../modeling/creating-a-wpf-based-domain-specific-language.md)。|  
|DSL 库|-A 最小的库|如果您想要生成可导入其他 DSL 定义的部分 DSL 定义，请使用此模板。|  
  
## <a name="see-also"></a>另请参阅  
 [域特定语言工具的概述](../modeling/overview-of-domain-specific-language-tools.md)

