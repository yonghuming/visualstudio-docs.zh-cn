---
title: "CorrelationScope 活动设计器 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: System.ServiceModel.Activities.CorrelationScope.UI
ms.assetid: 75f20664-9042-464d-8e2b-148d365a2286
caps.latest.revision: "6"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3e6e745e470c5e5b5a279f460198729bd9429ccc
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="correlationscope-activity-designer"></a>CorrelationScope 活动设计器
**CorrelationScope**活动设计器用于创建和配置<xref:System.ServiceModel.Activities.CorrelationScope>活动提供子消息传递活动使用的隐式管理<xref:System.ServiceModel.Activities.CorrelationHandle>对象。  
  
## <a name="the-correlationscope-activity"></a>CorrelationScope 活动  
 <xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A> 属性指定用于管理子消息传递活动的 <xref:System.ServiceModel.Activities.CorrelationHandle>。 将 <xref:System.ServiceModel.Activities.Send> 中包含的 <xref:System.ServiceModel.Activities.Receive> 和 <xref:System.ServiceModel.Activities.CorrelationScope.Body%2A> 活动配置为使用包含 <xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A> 活动的 <xref:System.ServiceModel.Activities.CorrelationScope> 属性以执行相关。  
  
### <a name="using-the-correlationscope-activity-designer"></a>使用 CorrelationScope 活动设计器  
 **CorrelationScope**在找不到活动设计器**消息**类别**工具箱**，通过单击访问的哪一**工具箱**的左侧选项卡[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)](或者，选择**工具栏**从**视图**菜单上或 CTRL + ALT + X。)  
  
 **CorrelationScope**活动设计器可以拖动从**工具箱**拖放到[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]面。 这将创建<xref:System.ServiceModel.Activities.CorrelationScope>默认值的活动**DisplayName** CorrelationScope。 <xref:System.Activities.Activity.DisplayName%2A>可以在的标头中编辑**CorrelationScope**活动设计器中或在**DisplayName**框**属性**窗口。  
  
 若要指定<xref:System.ServiceModel.Activities.CorrelationHandle>使用子消息传递活动，单击旁的省略号按钮**CorrelatesWith**字段**属性**窗口以显示**表达式编辑器**对话框。 还可以在活动设计器图面上设置此属性。  
  
 范围在相关之内的活动指定的删除设计**正文**框中**CorrelationScope**设计器。  
  
### <a name="the-correlationscope-properties"></a>CorrelationScope 属性  
 下表列出 <xref:System.ServiceModel.Activities.CorrelationScope> 属性并说明如何在设计器中使用它们。 这些属性可以编辑在**属性**窗口或在[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]设计器图面上，并且通常在这两。  
  
|属性名|必需|用法|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.ServiceModel.Activities.InitializeCorrelation> 活动的可选友好名称。|  
|<xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A>|False|指定用于管理子消息传递活动的 <xref:System.ServiceModel.Activities.CorrelationHandle>。 如果未设置此属性，则 <xref:System.ServiceModel.Activities.CorrelationScope> 会自动创建一个隐式 <xref:System.ServiceModel.Activities.CorrelationHandle>。|  
|<xref:System.ServiceModel.Activities.CorrelationScope.Body%2A>|False|指定处于相关范围之内的活动。|  
  
## <a name="see-also"></a>另请参阅  
 [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)   
 [接收](../workflow-designer/receive-activity-designer.md)   
 [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)   
 [发送](../workflow-designer/send-activity-designer.md)   
 [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)   
 [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)