---
title: "分层更新 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "数据 [Visual Basic], 分层更新"
  - "数据集 [Visual Basic], 分层更新"
  - "分层更新"
  - "已修改数据的保存"
  - "相关表, 保存"
  - "保存数据, 更改的数据"
  - "保存数据, 分层更新"
  - "保存已更新数据"
  - "已更新数据的保存"
ms.assetid: 68bae3f6-ec9b-45ee-a33a-69395029f54c
caps.latest.revision: 26
caps.handback.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 分层更新
“分层更新”是指在维护引用完整性规则的同时，将已更新数据（来自具有两个或多个相关表的数据集）存回到数据库中的过程。  “引用完整性”是指数据库中的约束所提供的一致性规则，这些约束可对插入、更新和删除相关记录的行为进行控制。  例如，引用完整性可强制要求在为客户创建订单之前先创建该客户的记录。  
  
 保存相关数据表中修改过的数据比保存单个表中的数据稍为复杂。  这是因为必须以特定的顺序执行每个相关表的 Update、Insert 和 Delete 命令，以避免违反引用完整性约束。  例如，假设有一个订单录入应用程序，您可以使用该程序管理新的和现有的客户和订单。  如果您需要删除一个现有客户，则在删除该客户记录之前，必须先删除该客户的所有订单。  如果要添加新的客户（带订单），必须首先插入新的客户记录，然后再插入该客户的订单，这是表中外键约束的要求。  正如这些示例所示，您需要提取数据的特定子集，并以正确的顺序发送更新（Insert、Update 和 Delete）以维护引用完整性。  
  
 分层更新功能使用 `TableAdapterManager` 来管理类型化数据集中的 `TableAdapter`。  `TableAdapterManager` 组件是 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 生成的组件，因此它不是 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 的组成部分。  有关 `TableAdapterManager` 类的详细信息，请参见 [TableAdapterManager 概述](../Topic/TableAdapterManager%20Overview.md)中的“TableAdapterManager 参考”一节。  
  
 如果应用程序使用类型化数据集并且允许用户修改相关数据表（存在一对多关系的数据表，例如 Customers 和 Orders）中的数据，则可能需要使用分层更新。  
  
## 本节内容  
 [分层更新概述](../Topic/Hierarchical%20Update%20Overview.md)  
 解释什么是分层更新，并提供有关如何实现分层更新的详细信息。  
  
 [TableAdapterManager 概述](../Topic/TableAdapterManager%20Overview.md)  
 解释什么是 `TableAdapterManager`，并提供数据集设计器所生成的 `TableAdapterManager` 代码的说明。  
  
 [如何：启用和禁用分层更新](../Topic/How%20to:%20Enable%20and%20Disable%20Hierarchical%20Update.md)  
 介绍如何设置类型化数据集的 `Hierarchical Update` 属性，以生成保存相关表的代码。  
  
 [如何：配置数据集中的外键约束](../Topic/How%20to:%20Configure%20Foreign-Key%20Constraints%20in%20a%20Dataset.md)  
 介绍如何配置数据集中的约束。  
  
 [如何：在保存数据前提交数据绑定控件中正在进行的编辑](../data-tools/commit-in-process-edits-on-data-bound-controls-before-saving-data.md)  
 介绍如何停止窗体上数据绑定控件内的所有进行中的编辑，以准备保存数据源。  
  
 [如何：设置分层更新的执行顺序](../Topic/How%20to:%20Set%20the%20Order%20When%20Performing%20a%20Hierarchical%20Update.md)  
 介绍如何设置 `TableAdapterManager` 的 `UpdateOrder` 属性，以控制执行 Insert、Update 和 Delete 的顺序。  
  
 [如何：在现有 Visual Studio 项目中实现分层更新](../Topic/How%20to:%20Implement%20Hierarchical%20Update%20in%20Existing%20Visual%20Studio%20Projects.md)  
 介绍如何升级具有相关数据表的应用程序，以使用 `TableAdapterManager` 保存数据。  
  
 [演练：保存相关数据表中的数据（分层更新）](../Topic/Walkthrough:%20Saving%20Data%20from%20Related%20Data%20Tables%20\(Hierarchical%20Update\).md)  
 提供分步说明，介绍如何创建具有相关数据表的应用程序以及如何使用 `TableAdapterManager` 保存数据。  
  
## 参考  
 <xref:System.Data.DataSet>  
  
 <xref:System.Data.DataTable>  
  
## 相关章节  
 [在 N 层应用程序中使用数据集](../data-tools/work-with-datasets-in-n-tier-applications.md)  
  
 [保存数据](../data-tools/saving-data.md)  
  
 [创建和编辑类型化数据集](../data-tools/creating-and-editing-typed-datasets.md)  
  
 [TableAdapter](../Topic/TableAdapters.md)  
  
 [DataSet、DataTable 和 DataView](../Topic/DataSets,%20DataTables,%20and%20DataViews.md)  
  
 [DataTable](../Topic/DataTables.md)  
  
 [在 Visual Studio 中访问数据](../data-tools/accessing-data-in-visual-studio.md)