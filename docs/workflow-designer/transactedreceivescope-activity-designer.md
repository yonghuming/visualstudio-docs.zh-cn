---
title: "TransactedReceiveScope 活动设计器 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.ServiceModel.Activities.TransactedReceiveScope.UI"
ms.assetid: 7ca93aad-4e83-4d81-90f4-998ee114d9b6
caps.latest.revision: 4
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# TransactedReceiveScope 活动设计器
**“TransactedReceiveScope”**设计器用于创建和配置 <xref:System.ServiceModel.Activities.TransactedReceiveScope> 活动。  
  
## TransactedReceiveScope 活动  
 <xref:System.ServiceModel.Activities.TransactedReceiveScope> 活动使您能够将事务流动到工作流或调度程序创建的服务器事务中。  
  
### 使用 TransactedReceiveScope 活动设计器  
 **“TransactedReceiveScope”**活动设计器可在**“工具箱”**的**“消息传递”**类别中找到，“工具箱”可通过单击 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 中的**“工具箱”**选项卡（或者，从**“视图”**菜单中选择**“工具栏”**或按 Ctrl\+Alt\+X）来访问。  
  
 可以将**“TransactedReceiveScope”**活动设计器从**“工具箱”**拖放到 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 图面上通常放置活动的任何位置。这将创建具有 TransactedReceiveScope 的默认**“DisplayName”**的 <xref:System.ServiceModel.Activities.TransactedReceiveScope> 活动。可以在**“TransactedReceiveScope”**活动设计器的标头中或在属性网格的**“DisplayName”**框中编辑 <xref:System.Activities.Activity.DisplayName%2A>。  
  
 **“TransactedReceiveScope”**设计器包含**“Request”**和**“Body”**框。它们用于配置 <xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A> 属性，该属性指定一个 <xref:System.ServiceModel.Activities.Receive> 活动和一个指定某些其他 <xref:System.Activities.Activity> 的 <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> 属性。<xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A> 创建一个事务。然后使该事务成为 <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> 范围的环境事务以便此范围中的任何活动可在该事务内执行。  
  
### TransactedReceiveScope 属性  
 下表列出 <xref:System.ServiceModel.Activities.TransactedReceiveScope> 属性并说明如何在设计器中使用它们。这些 <xref:System.Activities.Activity.DisplayName%2A> 属性可在属性网格中或 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 图面上进行编辑，但其他属性必须在设计图面上进行编辑。  
  
|属性名|必需|用法|  
|---------|--------|--------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.ServiceModel.Activities.TransactedReceiveScope> 活动的可选友好名称。默认值为 TransactedReceiveScope。<br /><br /> 虽然 <xref:System.Activities.Activity.DisplayName%2A> 名称不是绝对必需的，但最好使用显示名称。|  
|<xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A>|True|将 <xref:System.ServiceModel.Activities.Receive> 活动放置在活动设计器图面上的**“Request”**块中。|  
|<xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A>|False|将 <xref:System.Activities.Activity> 活动放置在活动设计器图面上的**“Body”**块中。|  
  
## 请参阅  
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)   
 [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)   
 [Receive](../workflow-designer/receive-activity-designer.md)   
 [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)   
 [Send](../workflow-designer/send-activity-designer.md)   
 [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)