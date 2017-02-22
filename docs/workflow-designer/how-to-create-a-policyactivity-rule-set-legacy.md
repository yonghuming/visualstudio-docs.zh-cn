---
title: "如何：创建 PolicyActivity 规则集（旧版） | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "PolicyActivity 活动, 创建规则集"
  - "PolicyActivity 活动, 选择规则集"
  - "“规则集编辑器”对话框"
  - "规则集, 针对 PolicyActivity 创建"
  - "“选择规则集”对话框"
ms.assetid: f272489d-3342-4511-8b59-6a0fd7a42d70
caps.latest.revision: 4
caps.handback.revision: 4
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# 如何：创建 PolicyActivity 规则集（旧版）
本主题介绍如何使用面向 [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] 或 [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] 的旧 [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] 来创建策略活动规则集。  
  
 在将**“策略”**活动项从**“工具箱”**拖动到工作流设计图面之后，需要为 [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019)（可能为英文网页）活动选择现有规则或创建新规则集。通过使用[“选择规则集”对话框（旧版）](../workflow-designer/select-rule-set-dialog-box-legacy.md)可以选择现有规则集；通过使用[“规则集编辑器”对话框（旧版）](../workflow-designer/rule-set-editor-dialog-box-legacy.md)可以创建规则集。  
  
> [!NOTE]
>  通过双击工作流设计图面上的 [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019)（可能为英文网页）活动，您可以直接打开[“规则集编辑器”对话框（旧版）](../workflow-designer/rule-set-editor-dialog-box-legacy.md)对话框。  
  
### 为 PolicyActivity 活动选择或创建规则集  
  
1.  右击 [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019)（可能为英文网页），然后单击**“属性”**打开**“属性”**窗口。  
  
2.  单击**“RuleSetReference”**属性。  
  
3.  执行下列操作之一：  
  
    -   单击**“RuleSetReference”**省略号**“\[…\]”**，然后在[“选择规则集”对话框（旧版）](../workflow-designer/select-rule-set-dialog-box-legacy.md)中选择现有规则集。然后转到步骤 10。  
  
         \- 或 \-  
  
    -   键入规则集的名称。单击**“RuleSetReference”**省略号**“\[…\]”**，然后在[“选择规则集”对话框（旧版）](../workflow-designer/select-rule-set-dialog-box-legacy.md)中选择**“编辑”**。  
  
         \- 或 \-  
  
    -   键入规则集的名称。展开**“RuleSetReference”**属性并在**“RuleSet 定义”**属性中选择省略号**“\[…\]”**。  
  
         这将打开[“规则集编辑器”对话框（旧版）](../workflow-designer/rule-set-editor-dialog-box-legacy.md)。  
  
4.  在[“规则集编辑器”对话框（旧版）](../workflow-designer/rule-set-editor-dialog-box-legacy.md)中单击**“添加规则”**以将新规则添加到规则集中。  
  
5.  输入**“名称”**、**“优先级”**和**“重新计算”**属性，或者保留默认值。  
  
6.  为**“条件”**输入文本。  
  
7.  为**“Then 操作”**和**“Else 操作”**输入文本。  
  
8.  再次单击**“添加规则”**以添加另一规则。  
  
9. 完成上述操作后，单击**“确定”**。  
  
## 请参阅  
 [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019)   
 [“选择规则集”对话框（旧版）](../workflow-designer/select-rule-set-dialog-box-legacy.md)   
 [“规则集编辑器”对话框（旧版）](../workflow-designer/rule-set-editor-dialog-box-legacy.md)   
 [使用策略活动](http://go.microsoft.com/fwlink?LinkID=65004)   
 [旧版工作流活动](../workflow-designer/legacy-workflow-activities.md)