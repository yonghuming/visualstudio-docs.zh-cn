---
title: "TransactedReceiveScope 活动设计器 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: System.ServiceModel.Activities.TransactedReceiveScope.UI
ms.assetid: 7ca93aad-4e83-4d81-90f4-998ee114d9b6
caps.latest.revision: "4"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: 77f7b4e0131eb5afc4585a68097c8d419145096b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="transactedreceivescope-activity-designer"></a>TransactedReceiveScope 活动设计器
**TransactedReceiveScope**设计器用于创建和配置<xref:System.ServiceModel.Activities.TransactedReceiveScope>活动。  
  
## <a name="the-transactedreceivescope-activity"></a>TransactedReceiveScope 活动  
 <xref:System.ServiceModel.Activities.TransactedReceiveScope> 活动使您能够将事务流动到工作流或调度程序创建的服务器事务中。  
  
### <a name="using-the-transactedreceivescope-activity-designer"></a>使用 TransactedReceiveScope 活动设计器  
 **TransactedReceiveScope**在找不到活动设计器**消息**类别**工具箱**，通过单击访问的哪一**工具箱**选项卡上[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)](或者，选择**工具栏**从**视图**菜单上或 CTRL + ALT + X。)  
  
 **TransactedReceiveScope**活动设计器可以拖动从**工具箱**拖放到[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]图面任何位置通常放置活动的。 这将创建<xref:System.ServiceModel.Activities.TransactedReceiveScope>默认值的活动**DisplayName** TransactedReceiveScope。 <xref:System.Activities.Activity.DisplayName%2A>可以在的标头中编辑**TransactedReceiveScope**活动设计器中或在**DisplayName**属性网格的框。  
  
 **TransactedReceiveScope**设计器包含**请求**和**正文**框。 它们用于配置 <xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A> 属性，该属性指定一个 <xref:System.ServiceModel.Activities.Receive> 活动和一个指定某些其他 <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> 的 <xref:System.Activities.Activity> 属性。 <xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A> 创建一个事务。 然后使该事务成为 <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> 范围的环境事务以便此范围中的任何活动可在该事务内执行。  
  
### <a name="the-transactedreceivescope-properties"></a>TransactedReceiveScope 属性  
 下表列出 <xref:System.ServiceModel.Activities.TransactedReceiveScope> 属性并说明如何在设计器中使用它们。 这些 <xref:System.Activities.Activity.DisplayName%2A> 属性可在属性网格中或 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 图面上进行编辑，但其他属性必须在设计图面上进行编辑。  
  
|属性名|必需|用法|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.ServiceModel.Activities.TransactedReceiveScope> 活动的可选友好名称。 默认值为 TransactedReceiveScope。<br /><br /> 虽然 <xref:System.Activities.Activity.DisplayName%2A> 名称不是绝对必需的，但最好使用显示名称。|  
|<xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A>|True|删除<xref:System.ServiceModel.Activities.Receive>活动放置**请求**活动设计器图面上的块。|  
|<xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A>|False|删除<xref:System.Activities.Activity>到**正文**活动设计器图面上的块。|  
  
## <a name="see-also"></a>另请参阅  
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)   
 [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)   
 [接收](../workflow-designer/receive-activity-designer.md)   
 [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)   
 [发送](../workflow-designer/send-activity-designer.md)   
 [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)