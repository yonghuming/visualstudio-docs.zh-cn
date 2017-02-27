---
title: "如何：实现 Windows Communication Foundation 协定操作（旧版） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: d6aeb20e-fac8-4a9d-bd26-ae78bef96b41
caps.latest.revision: 7
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# 如何：实现 Windows Communication Foundation 协定操作（旧版）
本主题介绍如何使用面向 [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] 或 [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] 的旧 [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] 来实现 [!INCLUDE[indigo1](../workflow-designer/includes/indigo1_md.md)] 协定操作。  
  
 在将**“ReceiveActivity”**活动从工具箱拖到工作流设计图面后，您可以创建新的 [!INCLUDE[indigo2](../workflow-designer/includes/indigo2_md.md)] 协定或导入现有协定，并实现操作。您可以通过[“选择操作”对话框（旧版）](../workflow-designer/choose-operation-dialog-box-legacy.md)来选择和\/或创建协定及其操作。  
  
### 实现 WCF 协定操作  
  
1.  在设计器中双击**“ReceiveActivity”**活动，或在**“属性”**窗格中单击**“ServiceOperationInfo”**属性旁边的省略号。  
  
2.  执行下列操作之一：  
  
    -   单击对话框右上角的**“添加协定”**。这将为您创建新的 [!INCLUDE[indigo2](../workflow-designer/includes/indigo2_md.md)] 协定和操作。  
  
         \- 或 \-  
  
    -   单击对话框右上角的**“导入”**。随即打开[“浏览并选择 .NET 类型”对话框（旧版）](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box-legacy.md)。搜索包含所需协定的程序集或项目。选择该协定，然后单击**“确定”**。  
  
     在创建或导入协定后，您可以为创建或导入的协定添加新操作。若要添加新操作，请选择该协定，然后单击对话框右上角的**“添加操作”**。完成添加操作后，请继续步骤 3。  
  
3.  选择要与**“ReceiveActivity”**活动关联的操作。您可以更改操作的名称、参数、属性和权限设置，从而对该操作的定义进行操作。  
  
     若要更改名称，请在**“操作名称”**文本框中输入新名称。  
  
     单击**“参数”**选项卡可访问该操作的参数。您可以更改参数的名称、类型或方向，也可以在操作中添加或删除参数。  
  
     单击**“属性”**选项卡可访问该操作的操作保护级别和受支持的消息交换功能。  
  
     单击**“权限”**选项卡可指定允许实现操作的组。  
  
4.  单击**“确定”**，则**“ReceiveActivity”**活动将显示正在实现的操作的操作名称。  
  
5.  将您希望用于实现该操作的工作流活动置于**“ReceiveActivity”**活动中。  
  
## 请参阅  
 [“选择操作”对话框（旧版）](../workflow-designer/choose-operation-dialog-box-legacy.md)   
 [如何：调用 WCF 协定操作（旧版）](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md)   
 [旧版工作流活动](../workflow-designer/legacy-workflow-activities.md)