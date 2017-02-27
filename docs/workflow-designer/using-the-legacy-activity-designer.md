---
title: "使用旧版活动设计器 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "活动, 添加子活动"
  - "活动, 配置"
  - "活动, 创建自定义"
  - "活动设计器"
  - "子活动, 添加"
  - "自定义活动"
ms.assetid: 2fea8a05-6e58-423d-94bf-a822b15ffb80
caps.latest.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# 使用旧版活动设计器
本主题介绍如何使用旧 [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] 中的活动设计器。在面向 [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] 或 [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] 时，请使用旧设计器。  
  
 通过使用活动设计器，可以创建自己的自定义活动。  
  
## 创建一个自定义活动  
 遵循以下步骤使用 Activity 设计器创建一个自定义活动：  
  
1.  在**“项目”**菜单上单击**“添加 Activity”**。  
  
2.  选择**“Activity”**或**“Activity \(具有单独的代码\)”**模板。  
  
    1.  使用**“Activity”**模板创建一个活动定义和用户代码在同一代码文件中的活动。  
  
    2.  使用**“Activity \(具有单独的代码\)”**模板创建一个活动定义（以工作流标记形式表示）和用户代码在不同代码文件中的活动。  
  
3.  键入活动名称或保留默认名称，然后单击**“添加”**。  
  
 此外，您还可以通过创建**Workflow Activity Library**类型的新项目来创建一组自定义的活动。有关此项目类型的更多信息，请参见[如何：创建工作流活动库（旧版）](../Topic/How%20to:%20Create%20a%20Workflow%20Activity%20Library%20\(Legacy\).md)。  
  
## 配置活动  
 当 Activity 设计器处于活动状态时，可以使用属性浏览器来配置下表中列出的属性。  
  
|属性|注释|  
|--------|--------|  
|**Name**|活动的名称。|  
|**Base Class**|从中派生活动的基类。默认的基类为 [SequenceActivity](http://go.microsoft.com/fwlink?LinkID=65020)。在**“属性”**窗口中，单击**“基类”**省略号**“\[…\]”**以在[“浏览并选择 .NET 类型”对话框（旧版）](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box-legacy.md)中选择另一个基类。|  
|**Description**|用户定义的活动说明。|  
|**Enabled**|默认情况下设置为 **True** 以启用活动执行和验证。设置为 **False** 可以禁用活动执行和验证。有关活动执行和验证的信息，请参见[开发工作流活动](http://go.microsoft.com/fwlink?LinkID=65024)（可能为英文网页）。|  
  
## 添加子活动  
 可以将子活动从工具箱拖到正在设计的活动。然后可以使用属性浏览器配置每个子活动。  
  
## 请参阅  
 [开发工作流活动](http://go.microsoft.com/fwlink?LinkID=65024)   
 [创建自定义活动](http://go.microsoft.com/fwlink?LinkID=65021)   
 [旧版工作流活动](../workflow-designer/legacy-workflow-activities.md)   
 [自定义活动示例](http://go.microsoft.com/fwlink?LinkID=65022)   
 [如何：创建工作流活动库（旧版）](../Topic/How%20to:%20Create%20a%20Workflow%20Activity%20Library%20\(Legacy\).md)   
 [使用旧版工作流设计器](../workflow-designer/using-the-legacy-workflow-designer.md)