---
title: "消息传递活动设计器 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 897e63cf-a42f-4edd-876f-c4ccfffaf6d6
caps.latest.revision: "7"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2aa2383326682dcedbb0888f5b55d34e3894327c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="messaging-activity-designers"></a>消息传递活动设计器
消息传递活动设计器用于在 [!INCLUDE[indigo1](../workflow-designer/includes/indigo1_md.md)] 应用程序中创建和配置从中发送和接收 [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] 消息的消息传递活动。 [!INCLUDE[netfx40_long](../workflow-designer/includes/netfx40_long_md.md)]引入了五个消息传递活动并且 [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] 提供了两个新的模板设计器，使您能在一个工作流中管理消息传递。 本节中所包含并在下表中列出的各主题介绍如何使用 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 活动和模板设计器。  
  
## <a name="in-this-section"></a>本节内容  
  
|消息活动|描述|  
|----------------------|-----------------|  
|[CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)|创建和配置 <xref:System.ServiceModel.Activities.CorrelationScope> 活动，该活动使用 <xref:System.ServiceModel.Activities.CorrelationHandle> 对象提供子消息传递活动的隐式管理。|  
|[InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)|创建和配置 <xref:System.ServiceModel.Activities.InitializeCorrelation> 活动，该活动用于在不发送或接收消息的情况下初始化相关。|  
|[接收](../workflow-designer/receive-activity-designer.md)|创建和配置 <xref:System.ServiceModel.Activities.Receive> 活动，该活动从某个服务接收消息。|  
|[ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)|在 <xref:System.ServiceModel.Activities.Send> 活动内创建预配置的一对 <xref:System.ServiceModel.Activities.ReceiveReply> 和 <xref:System.Activities.Statements.Sequence> 活动。|  
|[发送](../workflow-designer/send-activity-designer.md)|创建和配置 <xref:System.ServiceModel.Activities.Send> 活动，该活动向某个服务发送消息。|  
|[SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)|在 <xref:System.ServiceModel.Activities.Receive> 活动内创建预配置的一对 <xref:System.ServiceModel.Activities.SendReply> 和 <xref:System.Activities.Statements.Sequence> 活动。|  
|[TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)|创建和配置 <xref:System.ServiceModel.Activities.TransactedReceiveScope> 活动，该活动能将事务流入某个工作流中。|  
  
## <a name="reference"></a>参考  
 <xref:System.Activities.Activity>  
  
 <xref:System.ServiceModel.Activities.CorrelationScope>  
  
 <xref:System.ServiceModel.Activities.Receive>  
  
 <xref:System.ServiceModel.Activities.Send>  
  
 <xref:System.ServiceModel.Activities.ReceiveReply>  
  
 <xref:System.ServiceModel.Activities.SendReply>  
  
 <xref:System.ServiceModel.Activities.TransactedReceiveScope>  
  
## <a name="related-sections"></a>相关章节  
 有关其他类型活动设计器的信息，请参见下列主题。  
  
 [控制流](../workflow-designer/control-flow-activity-designers.md)  
  
 [使用活动设计器](../workflow-designer/using-the-activity-designers.md)  
  
 [流程图](../workflow-designer/flowchart-activity-designers.md)  
  
 [运行时](../workflow-designer/runtime-activity-designers.md)  
  
 [基元](../workflow-designer/primitives-activity-designers.md)  
  
 [事务](../workflow-designer/transaction-activity-designers.md)  
  
 [集合](../workflow-designer/collection-activity-designers.md)  
  
 [错误处理](../workflow-designer/error-handling-activity-designers.md)  
  
## <a name="external-resources"></a>外部资源  
 [使用活动设计器](../workflow-designer/using-the-activity-designers.md)