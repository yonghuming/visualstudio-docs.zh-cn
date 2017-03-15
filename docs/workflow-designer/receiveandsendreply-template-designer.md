---
title: "ReceiveAndSendReply 模板设计器 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.ServiceModel.Activities.ReceiveAndSendReply.UI"
  - "System.ServiceModel.Activities.SendReply.UI"
ms.assetid: d1d9a058-df7e-48f5-a2e7-3caeeba7eaa6
caps.latest.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# ReceiveAndSendReply 模板设计器
**“ReceiveAndSendReply”**模板用于在 <xref:System.Activities.Statements.Sequence> 活动中创建一对预配置的 <xref:System.ServiceModel.Activities.Receive> 和 <xref:System.ServiceModel.Activities.SendReply> 活动，这对活动作为服务器上请求\/响应消息交换模式的一部分而关联。  
  
## ReceiveAndSendReply 模板  
 添加**“ReceiveAndSendReply”**模板除了在 <xref:System.Activities.Statements.Sequence> 活动中创建 <xref:System.ServiceModel.Activities.Receive> 和 <xref:System.ServiceModel.Activities.SendReply> 活动之外，还要完成三个任务：  
  
1.  配置 <xref:System.ServiceModel.Activities.Receive> 活动的 <xref:System.ServiceModel.Activities.Receive.OperationName%2A> 和 <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> 属性。  
  
2.  将 <xref:System.ServiceModel.Activities.Receive> 活动的 <xref:System.ServiceModel.Activities.SendReply.Request%2A> 属性绑定到 <xref:System.ServiceModel.Activities.Send> 活动。  
  
3.  创建一个 <xref:System.ServiceModel.Activities.CorrelationHandle> 作为父活动中的一个变量。  
  
### 使用 ReceiveAndSendReply 模板设计器  
 **“ReceiveAndSendReply”**活动设计器可在**“工具箱”**的**“消息传递”**类别中找到，“工具箱”可通过单击 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 中的**“工具箱”**选项卡（或者，从**“视图”**菜单中选择**“工具栏”**或按 Ctrl\+Alt\+X）来访问。  
  
 可以将**“ReceiveAndSendReply”**活动设计器从**“工具箱”**拖放到 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 图面上通常放置活动的任何位置。这将创建一个可以使用**“Send”**活动设计器配置的 <xref:System.ServiceModel.Activities.Receive> 活动以及一个可以使用“SendReplyToReceive”设计器配置的相关 <xref:System.ServiceModel.Activities.SendReply>。  
  
 [!INCLUDE[crabout](../test/includes/crabout_md.md)]使用**“Receive”**设计器配置 <xref:System.ServiceModel.Activities.Receive> 活动的更多信息，请参见 [Receive](../workflow-designer/receive-activity-designer.md)主题。  
  
 [!INCLUDE[crabout](../test/includes/crabout_md.md)]使用**“SendReplyToReceive”**设计器配置 <xref:System.ServiceModel.Activities.SendReply> 活动的更多信息，请参见下一节。  
  
### SendReply 的属性  
 下表列出 <xref:System.ServiceModel.Activities.SendReply> 属性并说明如何在设计器中使用它们。这些属性可以在属性网格中进行编辑，其中一些属性还可以在 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 设计器图面上进行编辑。  
  
|属性名|必需|用法|  
|---------|--------|--------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.ServiceModel.Activities.SendReply> 活动的可选友好名称。默认值为 SendReplyToReceive。<br /><br /> 虽然对友好 <xref:System.Activities.Activity.DisplayName%2A> 使用非默认值不是绝对必需的，但最好使用非默认值。|  
|<xref:System.ServiceModel.Activities.SendReply.Request%2A>|True|对与此 <xref:System.ServiceModel.Activities.SendReply> 活动配对的 <xref:System.ServiceModel.Activities.Receive> 活动的引用。此属性不得为 **null**。将 <xref:System.ServiceModel.Activities.Receive> 和 <xref:System.ServiceModel.Activities.SendReply> 活动配合使用，可对服务器上的请求\/响应消息模式进行建模。此属性指定配对的 <xref:System.ServiceModel.Activities.Send> 活动。在该设计器中无法编辑此属性，因为它自动绑定到从中创建了 <xref:System.ServiceModel.Activities.SendReply> 活动的 <xref:System.ServiceModel.Activities.Send> 活动。|  
|<xref:System.ServiceModel.Activities.SendReply.Content%2A>|False|指定要接收的消息或参数内容。它可为 <xref:System.ServiceModel.Activities.ReceiveMessageContent> 活动或 <xref:System.ServiceModel.Activities.ReceiveParametersContent> 活动。编辑此属性的方法是单击属性网格中**“内容”**字段旁的椭圆形按钮，或单击**“Receive”**活动设计器图面上**“内容”**标签旁的**“定义…”**按钮。两者都显示**“内容定义”**对话框。[!INCLUDE[crabout](../test/includes/crabout_md.md)] 本主题演示如何使用对话框，请参见 [“内容定义”对话框](../workflow-designer/content-definition-dialog-box.md) 主题。|  
|<xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A>|False|指定在工作流中对配置此 <xref:System.ServiceModel.Activities.Receive> 活动的多个 <xref:System.ServiceModel.Activities.CorrelationHandle> 对象进行初始化的 <xref:System.ServiceModel.Activities.CorrelationInitializer> 对象的集合。单击属性旁边的省略号 <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> 打开 **“添加相关初始值设定项”** 对话框。[!INCLUDE[crabout](../test/includes/crabout_md.md)] 使用对话框，请参见 [“添加相关初始值设定项”对话框](../workflow-designer/add-correlationinitializers-dialog-box.md) 主题。|  
|<xref:System.ServiceModel.Activities.SendReply.Action%2A>|False|指定消息的操作标头。如果未显式设置，则它的默认值为：<br /><br /> **https:\/\/tempuri.org\/{服务协定命名空间}\/{服务协定名称}\/{操作名称}**|  
|<xref:System.ServiceModel.Activities.SendReply.PersistBeforeSend%2A>|False|该值指定是否应在回复消息前保留工作流服务实例。默认值为 **false**。|  
  
## 请参阅  
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)   
 [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)   
 [Receive](../workflow-designer/receive-activity-designer.md)   
 [Send](../workflow-designer/send-activity-designer.md)   
 [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)   
 [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)