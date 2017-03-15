---
title: "“选择操作”对话框（旧版） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Workflow.Activities.Design.OperationPickerDialog.UI"
ms.assetid: bc3ec902-7797-494e-af48-e70c97eb6779
caps.latest.revision: 10
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 10
---
# “选择操作”对话框（旧版）
本主题介绍如何使用旧 [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] 中的**“选择操作”**对话框。在需要面向 [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] 或 [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] 时，请使用旧 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]。  
  
 **“选择操作”**对话框用于选择要与 <xref:System.Workflow.Activities.ReceiveActivity> 活动或 <xref:System.Workflow.Activities.SendActivity> 活动关联的操作。有关使用此对话框和这些活动的更多信息，请参见[如何：实现 WCF 协定操作（旧版）](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md) 和[如何：调用 WCF 协定操作（旧版）](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md)。  
  
 下表描述了**“选择操作”**对话框的用户界面 \(UI\) 元素。  
  
|UI 元素|说明|  
|-----------|--------|  
|**添加 协定**|为您创建一个新协定。您可以在此协定上定义新操作。（仅与 <xref:System.Workflow.Activities.ReceiveActivity> 一起使用。）|  
|**添加 操作**|为您在**“选择操作”**对话框中创建的新协定添加新操作。 **Note:**  您只能为通过**“选择操作”**对话框创建的协定添加新操作。 <br /><br /> （仅与 <xref:System.Workflow.Activities.ReceiveActivity> 一起使用。）|  
|**导入...**|导入以前定义的协定，并允许您从该协定中选择一种操作。|  
|**操作 名称**|当前选定操作的名称。仅当通过**“选择操作”**对话框创建了操作后，才能对此文本框进行编辑。|  
|**参数**|此选项卡包含当前选定操作的参数定义。 **Note:**  仅当通过**“选择操作”**对话框创建了操作后，才能对参数定义进行更改。|  
|**属性**|此选项卡包含在客户端和服务之间所发送消息的 <xref:System.Net.Security.ProtectionLevel> 设置。 **Note:**  仅当通过**“选择操作”**对话框创建了操作后，才能启用此选项卡。|  
|**权限**|此选项卡包含允许调用此操作的用户的 <xref:System.Workflow.Activities.OperationInfoBase.PrincipalPermissionName%2A> 和 <xref:System.Workflow.Activities.OperationInfoBase.PrincipalPermissionRole%2A> 属性。例如，如果只允许 Administrators 组的用户调用此操作，您需要在**“角色”**文本框中写入“Administrators”。<br /><br /> 无论是通过**“选择操作”**对话框创建的操作，还是通过**“导入”**按钮导入的操作，均可启用此选项卡。|  
  
> [!NOTE]
>  **“选择操作”**对话框仅显示工作流中其他 <xref:System.Workflow.Activities.SendActivity> 活动所使用的协定或操作。同样，<xref:System.Workflow.Activities.ReceiveActivity> 活动的**“选择操作”**对话框仅显示工作流中其他 **ReceiveActivity** 活动所使用的协定或操作。  
  
## 请参阅  
 [如何：实现 WCF 协定操作（旧版）](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md)   
 [如何：调用 WCF 协定操作（旧版）](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md)   
 [Windows Workflow Foundation 的旧版设计器 UI 帮助](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)