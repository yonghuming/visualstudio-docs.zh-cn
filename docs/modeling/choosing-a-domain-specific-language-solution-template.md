---
title: "选择的域特定语言解决方案模板 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Domain-Specific Language Tools, solution templates
ms.assetid: 9c05955f-1548-4df6-b09b-4b348823c237
caps.latest.revision: "24"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: 2a1ad374c709b9575ff8e3d46bb3d2178a1c3f95
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="choosing-a-domain-specific-language-solution-template"></a>选择域特定语言解决方案模板
若要创建域特定语言解决方案时，选择一个域特定语言设计器向导中可用的解决方案模板。 通过选择与你想要创建的语言最严格相似的模板，你可以尽量减少你必须对开始解决方案进行的修改。  
  
 下面的解决方案模板是在域特定语言设计器向导中可用。  
  
|模板|功能|描述|  
|--------------|--------------|-----------------|  
|类关系图|-隔离舱形状<br />类继承<br />关系继承<br />形状继承<br />-关系属性|如果你的域特定语言包括实体和关系具有属性，请使用此解决方案模板。 此模板创建类似于 UML 类关系图的域特定语言。 主要实体是类和接口，与关联、 泛化和实现关系。 类或接口显示为一个包含属性的列表框。|  
|组件图|-端口|如果你的域特定语言包括组件，即，软件系统的部件，请使用此解决方案模板。 此模板创建类似于 UML 组件图的域特定语言。 主要实体是组件和端口，这将显示为小形状上组件的外部。|  
|任务流关系图|-图像和几何形状<br />-   *泳道*|如果你的域特定语言包括工作流、 状态或序列，请使用此解决方案模板。 此模板创建类似于 UML 活动图的域特定语言。 主要的实体是一项活动，并且主要关系是活动之间的转换。 该模板包含起始状态，最终状态等同步栏的几个其他元素。|  
|最小的语言|的一个类和形状<br />-一个关系和连接器|如果你的域特定语言不类似于其他模板，请使用此解决方案模板。 此模板创建具有两个类和一种关系，在中表示的域特定语言**工具箱**作为**框**和**行**。 类和关系每个具有示例字符串属性。|  
|最小 WinForm 设计器|-A 小的模型。<br />-A Windows 窗体中显示的模型。|如果你想要生成应用程序在其中 DSL 绑定到 Windows 窗体，而不是图形设计器，请使用此模板。<br /><br /> 充当语言的用户界面的表单已在 Dsl\UI 的文件夹中。<br /><br /> 在打开窗体设计器之前，应生成项目。<br /><br /> 有关详细信息，请参阅[创建 Windows Forms-Based 域特定语言](../modeling/creating-a-windows-forms-based-domain-specific-language.md)。|  
|最小的 WPF 设计器|-A 小模型<br />-显示模型 a Windows Presentation Foundation 用户界面|如果你想要生成应用程序在其中 DSL 绑定到 WPF 用户界面，而不是图形设计器，请使用此模板。<br /><br /> 用户界面的设计器处于 Dsl\UI 的文件夹。<br /><br /> 在打开设计器之前，应生成项目。<br /><br /> 有关详细信息，请参阅[创建 WPF-Based 域特定语言](../modeling/creating-a-wpf-based-domain-specific-language.md)。|  
|DSL 库|-A 最小库|如果你想要生成可导入其他 DSL 定义的部分 DSL 定义，请使用此模板。|  
  
## <a name="see-also"></a>另请参阅  
 [域特定语言工具的概述](../modeling/overview-of-domain-specific-language-tools.md)
