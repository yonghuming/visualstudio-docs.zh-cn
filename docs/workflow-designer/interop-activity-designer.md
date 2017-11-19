---
title: "Interop 活动设计器 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: System.Activities.Statements.Interop.UI
ms.assetid: 800a3403-ba86-41c4-8de1-c4fee9703eb1
caps.latest.revision: "6"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3adc99e0a09d2d82049dcbe816f14b24ab48a55d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="interop-activity-designer"></a>Interop 活动设计器
**互操作**活动设计器用于创建和配置<xref:System.Activities.Statements.Interop>活动。  
  
## <a name="the-interop-activity"></a>Interop 活动  
 <xref:System.Activities.Statements.Interop> 活动管理从工作流中的 <xref:System.Workflow.ComponentModel.Activity?displayProperty=fullName> 派生的活动类型的执行。  
  
### <a name="using-the-interop-activity-designer"></a>使用 Interop 活动设计器  
 **互操作**在找不到活动设计器**迁移**类别**工具箱**，通过单击访问的哪一**工具箱**选项卡 (或者，选择**工具箱**从**视图**菜单或 CTRL + ALT + X。)  
  
 [迁移](../workflow-designer/migration-activity-designers.md)包含的类别<xref:System.Activities.Statements.Interop>活动只中出现**工具箱**如果你的项目面向完整[!INCLUDE[netfx40_long](../workflow-designer/includes/netfx40_long_md.md)]。  
  
 对于 C# 项目，则可以重新面向该项目以使用完整[!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)]通过右键单击中的项目**解决方案资源管理器**并选择**属性**。 上**应用程序**选项卡上，选择**NET Framework 4**选项**目标框架**。 选择**是**按钮**目标框架更改**显示请求您确认此更改的对话框。  
  
 对于 VB 项目，则可以重新面向该项目以使用完整[!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)]通过项目中，右键单击**解决方案资源管理器**并选择**属性**。 上**编译**选项卡上，单击**高级编译选项**按钮。 选择**.Net Framework 4**从**目标框架列表**，然后单击**确定**。 单击**是**按钮**目标框架更改**显示请求您确认此更改的对话框。  
  
 **互操作**活动设计器可以拖动从**工具箱**拖放到[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]图面任何位置通常放置活动的如内<xref:System.Activities.Statements.Sequence>。 这将创建<xref:System.Activities.Statements.Interop>默认值的活动**DisplayName**的互操作。 <xref:System.Activities.Activity.DisplayName%2A>可以在的标头中编辑**互操作**活动设计器中或在**DisplayName**属性网格的框。  
  
 单击**单击此项可浏览...**中文**ActivityType**框中上,**互操作**活动设计器或在属性网格中，以打开**浏览并选择.Net 类型**对话框。 仅显示工作流 3.0 或工作流 3.5 活动的类型（即仅显示从 <xref:System.Workflow.ComponentModel.Activity> 派生的类型）。 [!INCLUDE[crabout](../test/includes/crabout_md.md)]使用此框指定类型，请参阅[浏览并选择.NET 类型对话框](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box.md)主题。  
  
### <a name="the-interop-properties"></a>Interop 属性  
 下表列出 <xref:System.Activities.Statements.Interop> 属性并说明如何在设计器中使用它们。 这些属性可以在属性网格中或 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 图面上进行编辑。  
  
|属性名|必需|用法|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.Interop> 活动的友好名称。 默认值为 Interop。 虽然显示名称不是绝对必需的，但最好使用显示名称。|  
|<xref:System.Activities.Statements.Interop.ActivityType%2A>|True|指定 <xref:System.Activities.Statements.Interop> 活动包含的活动类型。 指定的此类型必须派生自 <xref:System.Workflow.ComponentModel.Activity>。|  
  
## <a name="see-also"></a>另请参阅  
 [迁移](../workflow-designer/migration-activity-designers.md)