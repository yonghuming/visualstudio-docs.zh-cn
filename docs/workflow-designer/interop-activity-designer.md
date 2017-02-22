---
title: "Interop 活动设计器 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.Interop.UI"
ms.assetid: 800a3403-ba86-41c4-8de1-c4fee9703eb1
caps.latest.revision: 6
caps.handback.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Interop 活动设计器
**“Interop”**活动设计器用于创建和配置 <xref:System.Activities.Statements.Interop> 活动。  
  
## Interop 活动  
 <xref:System.Activities.Statements.Interop> 活动管理从工作流中的 <xref:System.Workflow.ComponentModel.Activity?displayProperty=fullName> 派生的活动类型的执行。  
  
### 使用 Interop 活动设计器  
 **“Interop”**活动设计器可在**“工具箱”**的**“迁移”**类别中找到，“工具箱”可通过单击**“工具箱”**选项卡（或者，从**“视图”**菜单中选择**“工具箱”**或按 Ctrl\+Alt\+X）来访问。  
  
 如果您的项目针对完整的 [!INCLUDE[netfx40_long](../workflow-designer/includes/netfx40_long_md.md)]，则**“工具箱”**中仅出现包含 <xref:System.Activities.Statements.Interop> 活动的 [迁移](../workflow-designer/migration-activity-designers.md)类别。  
  
 对于 C\# 项目，可通过在**“解决方案资源管理器”**中右击项目并选择**“属性”**，重新将项目定为使用完整的 [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)]。在**“应用程序”**选项卡上，选择**“目标框架”**中的**“.NET Framework 4”**选项。在显示请求您确认此更改的**“目标框架更改”**对话框中选择**“是”**按钮。  
  
 对于 VB 项目，可通过在**“解决方案资源管理器”**中右击项目并选择**“属性”**，重新将项目定为使用完整的 [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)]。在**“编译”**选项卡上，单击**“高级编译选项”**按钮。从**“目标框架列表”**中选择**“.Net Framework 4”**，然后单击**“确定”**。在显示请求您确认此更改的**“目标框架更改”**对话框中单击**“是”**按钮。  
  
 可以将**“Interop”**活动设计器从**“工具箱”**拖放到 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 图面上通常放置活动的任何位置，如 <xref:System.Activities.Statements.Sequence> 内。这将创建具有 Interop 的默认**“DisplayName”**的 <xref:System.Activities.Statements.Interop> 活动。可以在**“Interop”**活动设计器的标头中或在属性网格的**“DisplayName”**框中编辑 <xref:System.Activities.Activity.DisplayName%2A>。  
  
 在**“Interop”**活动设计器上或属性网格中，单击**“ActivityType”**框中的**“单击浏览…”**文本以打开**“浏览并选择 .NET 类型”**对话框。仅显示工作流 3.0 或工作流 3.5 活动的类型（即，仅从 <xref:System.Workflow.ComponentModel.Activity> 派生的类型）。[!INCLUDE[crabout](../test/includes/crabout_md.md)] 使用该对话框指定一个类型的更多信息，请参见 [“浏览并选择 .NET 类型”对话框](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box.md)主题。  
  
### Interop 属性  
 下表列出 <xref:System.Activities.Statements.Interop> 属性并说明如何在设计器中使用它们。这些属性可以在属性网格中或 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 图面上进行编辑。  
  
|属性名|必需|用法|  
|---------|--------|--------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.Interop> 活动的友好名称。默认值为 Interop。虽然显示名称不是绝对必需的，但最好使用显示名称。|  
|<xref:System.Activities.Statements.Interop.ActivityType%2A>|True|指定 <xref:System.Activities.Statements.Interop> 活动包含的活动类型。指定的此类型必须派生自 <xref:System.Workflow.ComponentModel.Activity>。|  
  
## 请参阅  
 [迁移](../workflow-designer/migration-activity-designers.md)