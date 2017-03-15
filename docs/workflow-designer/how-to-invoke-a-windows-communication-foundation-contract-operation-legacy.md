---
title: "如何：调用 Windows Communication Foundation 协定操作（旧版） | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: a9058345-708f-4fcf-8739-2a43e5285b7a
caps.latest.revision: 8
caps.handback.revision: 8
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# 如何：调用 Windows Communication Foundation 协定操作（旧版）
本主题介绍如何使用面向 [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] 或 [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] 的旧 [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] 来调用 [!INCLUDE[indigo1](../workflow-designer/includes/indigo1_md.md)] 协定操作。  
  
 在将**“SendActivity”**活动从工具箱拖到工作流设计图面后，必须导入现有协定，并确定从该**“SendActivity”**活动中调用哪个操作。您可以通过[“选择操作”对话框（旧版）](../workflow-designer/choose-operation-dialog-box-legacy.md)来选择协定及其操作。  
  
 另外，如果您一起使用配置文件和服务，则您需要指定一个 <xref:System.Workflow.Activities.ChannelToken>。<xref:System.Workflow.Activities.ChannelToken> 标识终结点配置，发送活动将使用此终结点配置来连接到工作流服务。  
  
### 从 SendActivity 活动调用 WCF 协定操作  
  
1.  在设计器中双击**“SendActivity”**活动，或在**“属性”**窗格中单击**“ServiceOperationInfo”**属性旁边的省略号。  
  
2.  **“选择操作”**对话框打开后，在该对话框的右上角单击**“导入”**。  
  
     随即打开[“浏览并选择 .NET 类型”对话框（旧版）](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box-legacy.md)。  
  
3.  搜索包含所需协定的程序集或项目。  
  
4.  选择该协定，然后单击**“确定”**。  
  
5.  在**“可用操作”**之下选择您要调用的操作，然后单击**“确定”**。  
  
### 指定通道令牌  
  
1.  在设计器中选择 <xref:System.Workflow.Activities.SendActivity> 活动。  
  
2.  在**“属性”**窗格中指定 <xref:System.Workflow.Activities.ChannelToken> 的名称。此名称唯一标识通道令牌。  
  
3.  展开通道令牌节点，并为要在 <xref:System.Workflow.Activities.ChannelToken.EndpointName%2A> 字段中使用的客户端终结点指定名称。配置文件中名称相同的终结点配置将用于配置通道。  
  
4.  如果配置文件中不存在终结点配置，请创建终结点配置。有关配置客户端的更多信息，请参见 [WCF 客户端概述](../Topic/WCF%20Client%20Overview.md)。  
  
## 请参阅  
 [“选择操作”对话框（旧版）](../workflow-designer/choose-operation-dialog-box-legacy.md)   
 [如何：实现 WCF 协定操作（旧版）](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md)   
 [旧版工作流活动](../workflow-designer/legacy-workflow-activities.md)