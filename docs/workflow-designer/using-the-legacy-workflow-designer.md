---
title: "使用旧版工作流设计器 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: Visual Studio 2005 Extensions for Windows Workflow Foundation, about
ms.assetid: 7af53077-afd7-465f-9c1d-b387e9d4f216
caps.latest.revision: "10"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: eda078bdfc0eae8861ac4e70b0f1f73a399f994c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="using-the-legacy-workflow-designer"></a>使用旧版工作流设计器
[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 提供的旧 [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] 可用于面向 [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] 或 [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)]。  
  
 它可通过选择**.NET Framework 3.0**选项或**.NET Framework 3.5**的下拉列表的顶部列表中的选项**新项目**窗口。 中的默认选项[!INCLUDE[vs2010](../misc/includes/vs2010_md.md)]是**.NET Framework 4**用于创建[!INCLUDE[wf](../workflow-designer/includes/wf_md.md)]面向的应用程序[!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)]。  
  
 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]提供了一种以图形方式创建 [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] 应用程序的方法（使用熟悉的 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 用户界面）。 [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] 应用程序由名为活动的工作流过程步骤组成。 若要创建工作流，构成活动设计图面上的，通过拖动其相应的活动设计器从**工具箱**拖到设计图面。  
  
 下表列出了 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] for Windows Workflow Foundation 的主要功能。  
  
|功能|描述|  
|-------------|-----------------|  
|活动拖放|将活动从**工具箱**拖到设计图面来创建工作流。|  
|属性浏览器|标准**属性**中的窗口[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]用于配置活动的属性。|  
|缩放|双筒望远镜图标**缩放级别**图标位于设计图面右侧垂直滚动条的下方。 单击双筒望远镜图标并选择一个缩放百分比，以使工作流图形放大或缩小。你还可以使用**平移**图标放大镜光标选项来放大和缩小。|  
|平移|**平移**图标，一个包含指向四个方向的十字的箭头的圆圈位于双筒望远镜缩放图标的下方的设计图面右侧垂直滚动条的下方。 如果单击平铺图标，一个弹出菜单将提供以下光标选项：<br /><br /> -**放大**放大镜光标允许您通过单击设计图面放大。<br />-**缩小**放大镜光标允许您通过单击设计图面缩小。<br />-**导航工具**手形光标允许您"抓住"并变换工作流设计图面中的视图。<br />-**默认**箭头光标允许您从其他光标切换回默认箭头光标。|  
|自动滚动|如果工作流很大，您可能需要将活动放在超出设计图面区域可见显示部分的位置。 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 允许您将活动拖到设计图面边缘最接近您想要放置活动的位置的地方。 设计图面视图将在该方向上自动滚动。|  
|智能标记|未完全配置或未有效配置的活动都标有感叹号图标。 可以单击该图标，查看活动上存在的配置需要的下拉列表。 然后，可以使用**属性**窗口来适当配置活动。 当所有属性对于活动均有效时，感叹号图标将消失。|  
  
## <a name="in-this-section"></a>本节内容  
 [Visual Studio 工作流窗口（旧版）](../workflow-designer/visual-studio-workflow-windows-legacy.md)  
  
 [创建旧版工作流项目](../workflow-designer/creating-legacy-workflow-projects.md)  
  
 [顺序工作流视图（旧版）](../workflow-designer/sequential-workflow-views-legacy.md)  
  
 [旧版工作流活动](../workflow-designer/legacy-workflow-activities.md)  
  
 [在工作流中使用主题（旧版）](../workflow-designer/using-themes-in-workflows-legacy.md)  
  
 [使用旧版状态机工作流设计器](../workflow-designer/using-the-legacy-state-machine-workflow-designer.md)  
  
 [使用旧版活动设计器](../workflow-designer/using-the-legacy-activity-designer.md)  
  
 [Windows Workflow Foundation 的旧版设计器 UI 帮助](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)  
  
## <a name="see-also"></a>另请参阅  
 [开发工作流](http://go.microsoft.com/fwlink?LinkID=65010)