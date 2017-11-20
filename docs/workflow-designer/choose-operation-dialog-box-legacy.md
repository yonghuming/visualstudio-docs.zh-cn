---
title: "选择操作对话框 （旧版） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: System.Workflow.Activities.Design.OperationPickerDialog.UI
ms.assetid: bc3ec902-7797-494e-af48-e70c97eb6779
caps.latest.revision: "10"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: 320233edede13e2f33bdcb206b056bf1d0b94b8e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="choose-operation-dialog-box-legacy"></a>“选择操作”对话框（旧版）
本主题介绍如何使用**选择操作**对话框中，在旧[!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)]。 在需要面向 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 或 [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] 时，请使用旧 [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)]。  
  
 **选择操作**对话框用于选择要将与相关联的操作<xref:System.Workflow.Activities.ReceiveActivity>活动或<xref:System.Workflow.Activities.SendActivity>活动。 有关使用这些活动使用此对话框中的详细信息，请参阅[如何： 实现 WCF 协定操作 （旧版）](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md)和[如何： 调用 WCF 协定操作 （旧版）](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md)。  
  
 下表描述的用户界面 (UI) 元素**选择操作**对话框。  
  
|UI 元素|描述|  
|----------------|-----------------|  
|**添加协定**|为您创建一个新协定。 您可以在此协定上定义新操作。 （仅与 <xref:System.Workflow.Activities.ReceiveActivity> 一起使用。）|  
|**添加操作**|在中创建的新协定添加新操作**选择操作**对话框。 **注意：**只能向通过创建的协定添加新操作**选择操作**对话框。 <br /><br /> （仅与 <xref:System.Workflow.Activities.ReceiveActivity> 一起使用。）|  
|**导入...**|导入以前定义的协定，并允许您从该协定中选择一种操作。|  
|**操作名称**|当前选定操作的名称。 此文本框是可用于编辑仅当你创建了操作通过**选择操作**对话框。|  
|**参数**|此选项卡包含当前选定操作的参数定义。 **注意：**可以更改参数定义，仅当你创建了操作通过**选择操作**对话框。|  
|**属性**|此选项卡包含在客户端和服务之间所发送消息的 <xref:System.Net.Security.ProtectionLevel> 设置。 **注意：**仅当你创建了操作通过启用此选项卡**选择操作**对话框。|  
|**权限**|此选项卡包含允许调用此操作的用户的 <xref:System.Workflow.Activities.OperationInfoBase.PrincipalPermissionName%2A> 和 <xref:System.Workflow.Activities.OperationInfoBase.PrincipalPermissionRole%2A> 属性。 例如，如果仅允许从管理员组的用户通过调用此操作，然后你将编写"管理员"**角色**文本框。<br /><br /> 为通过创建这两个操作启用此选项卡**ChooseOperation**对话框，并通过导入的操作**导入**按钮。|  
  
> [!NOTE]
>  **选择操作**对话框中显示唯一协定或由其他使用的操作<xref:System.Workflow.Activities.SendActivity>工作流中的活动。 同样，**选择操作**对话框<xref:System.Workflow.Activities.ReceiveActivity>活动显示唯一协定或由其他使用的操作**ReceiveActivity**工作流中的活动。  
  
## <a name="see-also"></a>另请参阅  
 [如何： 实现 WCF 协定操作 （旧版）](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md)   
 [如何： 调用 WCF 协定操作 （旧版）](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md)   
 [Windows Workflow Foundation 的旧版设计器 UI 帮助](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)