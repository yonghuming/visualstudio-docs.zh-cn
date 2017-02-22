---
title: "InitializeCorrelation 活动设计器 | Microsoft Docs"
ms.custom: ""
ms.date: "11/23/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.ServiceModel.Activities.InitializeCorrelation.UI"
ms.assetid: 4c54f34c-ee84-42a6-abb0-ec260c1ccb76
caps.latest.revision: 6
caps.handback.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# InitializeCorrelation 活动设计器
**“InitializeCorrelation”**活动设计器用于创建和配置 <xref:System.ServiceModel.Activities.InitializeCorrelation> 活动，该活动用于在发送或接收消息之前在这些消息之间建立相关。  
  
## InitializeCorrelation 活动  
 <xref:System.ServiceModel.Activities.InitializeCorrelation> 活动用于在不发送或接收消息的情况下初始化相关。通常，相关是在发送或接收消息时初始化的。如果必须在发送或接收消息前建立相关，请使用 <xref:System.ServiceModel.Activities.InitializeCorrelation> 来初始化该相关。  
  
### 使用 InitializeCorrelation 活动设计器  
 **“InitializeCorrelation”**活动设计器可在**“工具箱”**的**“消息传递”**类别中找到，“工具箱”可通过单击 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 上的**“工具箱”**选项卡（或者，从**“视图”**菜单中选择**“工具栏”**或按 Ctrl\+Alt\+X）来访问。  
  
 可以将**“InitializeCorrelation”**活动设计器从**“工具箱”**拖放到 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 图面上。这将创建具有 InitializeCorrelation 的默认 <xref:System.Activities.Activity.DisplayName%2A> 的 <xref:System.ServiceModel.Activities.InitializeCorrelation> 活动。可以在**“InitializeCorrelation”**活动设计器的标头中或在**“属性”**窗口的**“DisplayName”**框中编辑 <xref:System.Activities.Activity.DisplayName%2A>。  
  
 可以在**“InitializeCorrelation”**活动设计器图面上的**“属性”**窗口的**“相关”**字段中指定 <xref:System.ServiceModel.Activities.CorrelationHandle>。  
  
 单击**“属性”**窗口中**“CorrelationData”**字段旁的椭圆形按钮或**“InitializeCorrelation”**活动设计器图面上的“查看…”提示文本将显示**“初始化相关”**对话框，在该对话框中可指定相关句柄和用于初始化该相关的键值对。[!INCLUDE[crabout](../test/includes/crabout_md.md)] 使用此对话框的更多信息，请参见 [“类型集合编辑器”对话框](../workflow-designer/type-collection-editor-dialog-box.md) 主题。  
  
### InitializeCorrelation 属性  
 下表列出 <xref:System.ServiceModel.Activities.InitializeCorrelation> 属性并说明如何在设计器中使用它们。这些属性可以在**“属性”**窗口或 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 图面中进行编辑。  
  
|属性名|必需|用法|  
|---------|--------|--------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.ServiceModel.Activities.InitializeCorrelation> 活动的友好名称。默认值为 InitializeCorrelation。<br /><br /> 虽然对友好 <xref:System.Activities.Activity.DisplayName%2A> 使用非默认值不是绝对必需的，但最好使用非默认值。|  
|<xref:System.ServiceModel.Activities.InitializeCorrelation.Correlation%2A>|False|用于关联相关中的工作流活动的 <xref:System.ServiceModel.Activities.CorrelationHandle>。|  
|<xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>|False|将消息与工作流实例相关联的相关数据的字典。<br /><br /> 使用 **“初始化相关”** 对话框来配置 <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>。[!INCLUDE[crabout](../test/includes/crabout_md.md)] 使用此对话框，请参见 [“类型集合编辑器”对话框](../workflow-designer/type-collection-editor-dialog-box.md) 主题。|  
  
## 请参阅  
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)   
 [Receive](../workflow-designer/receive-activity-designer.md)   
 [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)   
 [Send](../workflow-designer/send-activity-designer.md)   
 [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)   
 [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)