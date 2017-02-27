---
title: "如何：创建声明性规则条件（旧版） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "条件语句, 声明性规则条件"
  - "声明性规则条件"
  - "“规则条件编辑器”对话框"
ms.assetid: 804b6129-c433-408f-a424-46987967730c
caps.latest.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# 如何：创建声明性规则条件（旧版）
本主题介绍如何使用面向 [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] 或 [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] 的旧 [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] 来声明规则条件。  
  
 条件语句的计算结果为 **True** 或 **False**。声明性规则条件是一个条件语句，该语句是使用[“规则条件编辑器”对话框（旧版）](../workflow-designer/rule-condition-editor-dialog-box-legacy.md)创建的，并以 XML 形式与工作流存储在一起。声明性规则条件可以包括一些谓词，这些谓词比较工作流状态和组合多个谓词的布尔代数。  
  
 声明性规则条件用在以下 Windows Workflow Foundation 现成可用的活动中：  
  
-   [ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017)  
  
-   [IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65034)  
  
-   [ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65039)  
  
-   [WhileActivity](http://go.microsoft.com/fwlink?LinkID=65049)  
  
-   [SequentialWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65040)  
  
-   [StateMachineWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65045)  
  
### 使用规则条件编辑器创建声明性规则条件  
  
1.  在活动的**“属性”**窗口中，单击 **Condition** 属性或 **UntilCondition** 属性，具体情况视活动而定。  
  
2.  为该属性从列表中选择**“声明性规则条件”**。  
  
3.  展开 **Condition** 或 **UntilCondition** 属性。  
  
4.  单击 **ConditionName** 属性。  
  
5.  单击 **ConditionName** 的省略号**“\[…\]”**，打开**“选择条件”**对话框。  
  
6.  单击**“新建条件”**打开**“规则条件编辑器”**对话框。  
  
7.  在**“条件”**文本框中为条件键入表达式。  
  
     有关如何创建条件表达式的信息，请参见[“规则条件编辑器”对话框（旧版）](../workflow-designer/rule-condition-editor-dialog-box-legacy.md)。  
  
8.  条件表达式创建完成后，单击**“确定”**关闭对话框并用分配的名称创建规则条件。  
  
     **“选择条件”**对话框将打开。  
  
     有关如何使用**“选择条件”**对话框的信息，请参见[“选择条件”对话框（旧版）](../workflow-designer/select-condition-dialog-box-legacy.md)。  
  
## 请参阅  
 [旧版工作流活动](../workflow-designer/legacy-workflow-activities.md)   
 [使用 ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65066)   
 [使用 IfElseBranchActivity 活动](http://go.microsoft.com/fwlink?LinkID=65075)   
 [使用 Replicator 活动](http://go.microsoft.com/fwlink?LinkID=65080)   
 [使用 While 活动](http://go.microsoft.com/fwlink?LinkID=65091)   
 [“规则条件编辑器”对话框（旧版）](../workflow-designer/rule-condition-editor-dialog-box-legacy.md)   
 [“选择条件”对话框（旧版）](../workflow-designer/select-condition-dialog-box-legacy.md)   
 [在工作流中使用条件](http://go.microsoft.com/fwlink?LinkID=65009)