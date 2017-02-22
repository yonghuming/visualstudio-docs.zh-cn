---
title: "顺序工作流视图（旧版） | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "顺序工作流视图"
  - "顺序工作流, 视图"
ms.assetid: 135f24b9-1b37-442b-9ef8-f0f2108a3212
caps.latest.revision: 7
caps.handback.revision: 7
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# 顺序工作流视图（旧版）
[!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)] 提供了一个旧 [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)]，可用于面向 [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] 或 [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)]。  
  
 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 提供了一种以图形方式创建方法 [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] 使用熟悉的应用程序 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 用户接口。[!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] 应用程序由名为活动的工作流过程步骤组成。若要创建工作流，请通过将相应活动设计器从**“工具箱”**拖到设计图面上，在设计图面上构成活动。  
  
 在创建顺序工作流（即 [SequentialWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65040)，可能为英文网页）时，会提供工作流的三个视图。可从**“工作流”**菜单和设计图面上的上下文菜单来访问这些视图。  
  
 下表列出了每个视图的名称和说明。  
  
|菜单\/选项卡选项|说明|  
|---------------|--------|  
|**查看顺序工作流**|右击设计图面并从上下文菜单中选择**“查看顺序工作流”**选项以显示**顺序工作流**视图，该视图显示顺序工作流的基于活动的图形化表示形式。或者从**“工作流”**菜单中选择**“查看顺序工作流”**。|  
|**查看取消处理程序**|右击设计图面并从上下文菜单中选择**“查看取消处理程序”**选项以显示**顺序工作流**视图，该视图显示与工作流关联的 [CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65050) 活动。或者从**“工作流”**菜单中选择**“查看取消处理程序”**。|  
|**查看错误处理程序**|右击设计图面并从上下文菜单中选择**“查看错误处理程序”**选项以显示**错误**视图，该视图显示与工作流关联的 [FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055) 活动。或者从**“工作流”**菜单中选择**“查看错误处理程序”**。|  
  
 有关类似视图的更多信息，请参见[活动视图（旧版）](../workflow-designer/activity-views-legacy.md)。  
  
## 请参阅  
 [活动视图（旧版）](../workflow-designer/activity-views-legacy.md)   
 [创建旧版工作流项目](../workflow-designer/creating-legacy-workflow-projects.md)   
 [工作流创作模式](http://go.microsoft.com/fwlink?LinkID=65014)