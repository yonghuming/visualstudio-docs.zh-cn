---
title: "CorrelationScope 活动设计器 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.ServiceModel.Activities.CorrelationScope.UI"
ms.assetid: 75f20664-9042-464d-8e2b-148d365a2286
caps.latest.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# CorrelationScope 活动设计器
**“CorrelationScope”**活动设计器用于创建和配置 <xref:System.ServiceModel.Activities.CorrelationScope> 活动，该活动使用 <xref:System.ServiceModel.Activities.CorrelationHandle> 对象提供子消息传递活动的隐式管理。  
  
## CorrelationScope 活动  
 <xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A> 属性指定用于管理子消息传递活动的 <xref:System.ServiceModel.Activities.CorrelationHandle>。将 <xref:System.ServiceModel.Activities.CorrelationScope.Body%2A> 中包含的 <xref:System.ServiceModel.Activities.Send> 和 <xref:System.ServiceModel.Activities.Receive> 活动配置为使用包含 <xref:System.ServiceModel.Activities.CorrelationScope> 活动的 <xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A> 属性以执行相关。  
  
### 使用 CorrelationScope 活动设计器  
 **“CorrelationScope”**活动设计器可在**“工具箱”**的**“消息传递”**类别中找到，“工具箱”可通过单击 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 左侧的**“工具箱”**选项卡（或者，从**“视图”**菜单中选择**“工具栏”**或按 Ctrl\+Alt\+X）来访问。  
  
 可以将**“CorrelationScope”**活动设计器从**“工具箱”**拖放到 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 图面上。这将创建具有 CorrelationScope 的默认**“DisplayName”**的 <xref:System.ServiceModel.Activities.CorrelationScope> 活动。可以在**“CorrelationScope”**活动设计器的标头中或在**“属性”**窗口的**“DisplayName”**框中编辑 <xref:System.Activities.Activity.DisplayName%2A>。  
  
 若要指定子消息传递活动所使用的 <xref:System.ServiceModel.Activities.CorrelationHandle>，请单击**“属性”**窗口中**“CorrelatesWith”**字段旁的椭圆形按钮以显示**“表达式编辑器”**对话框。还可以在活动设计器图面上设置此属性。  
  
 通过将活动设计器放置在**“CorrelationScope”**设计器的**“Body”**框中可指定范围在相关之内的活动。  
  
### CorrelationScope 属性  
 下表列出 <xref:System.ServiceModel.Activities.CorrelationScope> 属性并说明如何在设计器中使用它们。这些属性可以在**“属性”**窗口中编辑，也可以在 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 设计器图面上编辑，通常在这两者中都可以进行编辑。  
  
|属性名|必需|用法|  
|---------|--------|--------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.ServiceModel.Activities.InitializeCorrelation> 活动的可选友好名称。|  
|<xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A>|False|指定用于管理子消息传递活动的 <xref:System.ServiceModel.Activities.CorrelationHandle>。如果未设置此属性，则 <xref:System.ServiceModel.Activities.CorrelationScope> 会自动创建一个隐式 <xref:System.ServiceModel.Activities.CorrelationHandle>。|  
|<xref:System.ServiceModel.Activities.CorrelationScope.Body%2A>|False|指定处于相关范围之内的活动。|  
  
## 请参阅  
 [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)   
 [Receive](../workflow-designer/receive-activity-designer.md)   
 [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)   
 [Send](../workflow-designer/send-activity-designer.md)   
 [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)   
 [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)