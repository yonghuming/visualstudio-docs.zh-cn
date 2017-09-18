---
title: "数据集中的关系 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbData.Microsoft.VSDesigner.DataSource.DesignRelation"
  - "vbdata.Microsoft.VSDesigner.DataSource.DesignRelation"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "数据集 [Visual Basic], 关系"
  - "关系, 关于关系"
  - "关系, 数据集"
ms.assetid: cfe274f0-71fe-40f6-994e-7c7f6273c9ba
caps.latest.revision: 15
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 数据集中的关系
数据集可像关系数据库一样包含关系表。  简化数据表之间关系的对象是 **DataRelation** 对象。  下列主题提供了有关 ADO.NET **DataRelation** 对象、如何创建它们以及如何使用它们处理相关表中的数据的信息。  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## 本节内容  
 [介绍 DataRelation 对象](../Topic/Introduction%20to%20DataRelation%20Objects.md)  
 提供有关数据集允许您指定表间关系以及利用这些关系的方法的概述。  
  
 [如何：使用数据集设计器创建 DataRelation](../Topic/How%20to:%20Create%20DataRelations%20with%20the%20Dataset%20Designer.md)  
 介绍如何使用**“数据集设计器”**向数据集中添加 <xref:System.Data.DataRelation> 对象。  
  
 [如何：访问相关数据表中的记录](../Topic/How%20to:%20Access%20Records%20in%20Related%20DataTables.md)  
 介绍如何通过编程方法返回具有一对多关系的表的类型化数据集中的相关记录。  
  
 [演练：创建数据表之间的关系](../Topic/Walkthrough:%20Creating%20a%20Relationship%20between%20Data%20Tables.md)  
 提供分步说明，介绍如何使用**“数据集设计器”**创建两个数据表并在它们之间添加关系。  
  
## 参考  
 <xref:System.Data.DataRelation>  
 表示两个 T:System.Data.DataTable 对象之间的父\/子关系。  
  
 <xref:System.Data.DataRow.GetChildRows%2A>  
 获取 T:System.Data.DataRow 的子行。  
  
 <xref:System.Data.DataRow.GetParentRow%2A>  
 获取 T:System.Data.DataRow 的父行。  
  
 <xref:System.Data.Rule>  
 指示强制执行 <xref:System.Data.ForeignKeyConstraint> 时发生的操作。  
  
 <xref:System.Data.DataColumn.Unique%2A>  
 获取或设置一个值，该值指示该列每一行中的值是否必须唯一。  
  
 <xref:System.Data.Constraint>  
 表示可在一个或多个 <xref:System.Data.DataColumn> 对象上强制执行的约束。  
  
## 相关章节  
 [添加 DataRelation](../Topic/Adding%20DataRelations.md)  
 描述如何创建 <xref:System.Data.DataSet> 中表之间的关系。  
  
 [导航 DataRelation](../Topic/Navigating%20DataRelations.md)  
 描述如何使用 <xref:System.Data.DataSet> 中表之间的关系来返回具有父子关系的子行或父行。  
  
 [嵌套 DataRelation](../Topic/Nesting%20DataRelations.md)  
 讨论嵌套 <xref:System.Data.DataRelation> 对象在以 XML 数据形式表示 <xref:System.Data.DataSet> 内容时的重要性，并描述如何创建这些对象。