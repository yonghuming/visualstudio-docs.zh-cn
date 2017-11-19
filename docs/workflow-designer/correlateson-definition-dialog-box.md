---
title: "CorrelatesOn 定义对话框 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: CorrelatesOnDefinition.UI
ms.assetid: 8b2b627a-f236-4479-aa09-525df65e3413
caps.latest.revision: "6"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: babe684c0fd4eeec1a00e4f44868bfc0a67e5f9d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="correlateson-definition-dialog-box"></a>“CorrelatesOn 定义”对话框
**CorrelatesOn**中使用对话框[!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)]编辑<xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A>属性<xref:System.ServiceModel.Activities.Receive>活动。 [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][接收](../workflow-designer/receive-activity-designer.md)主题。  
  
 <xref:System.ServiceModel.Activities.Receive> 活动之间的关联指定工作流中的不同服务操作如何相互连接。  
  
 下表描述的用户界面 (UI) 元素**CorrelatesOn**对话框。  
  
|UI 元素|描述|  
|----------------|-----------------|  
|**CorrelatesWith**|用于将消息路由到相应工作流实例的 <xref:System.ServiceModel.Activities.CorrelationHandle>。|  
|**XPath 查询**|包含用于从传入消息中提取相关数据的查询的键/值对。 它对应于 <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> 属性。 XPath 查询包含在 <xref:System.ServiceModel.MessageQuerySet> 对象中。|  
  
## <a name="to-launch-the-correlateson-dialog-box"></a>启动“CorrelatesOn”对话框  
 **接收**活动设计器可以拖动从**工具箱**拖放到[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]图面任何位置通常放置活动的。 这将创建具有 Receive 的默认 <xref:System.ServiceModel.Activities.Receive> 的 <xref:System.Activities.Activity.DisplayName%2A> 活动。 选择**接收**活动设计器，然后为 （集合） 文本旁的省略号按钮的单击**CorrelatesOn**属性在属性网格**CorrelatesOn 定义**对话框出现。  
  
## <a name="see-also"></a>另请参阅  
 <xref:System.ServiceModel.Activities.Receive>   
 [添加 CorrelationInitializers 对话框](../workflow-designer/add-correlationinitializers-dialog-box.md)   
 [添加相关对话框](http://msdn.microsoft.com/en-us/9e41a149-e8ab-41b1-8886-ea06a63041b6)   
 [“初始化相关”对话框](../workflow-designer/initialize-correlation-dialog-box.md)