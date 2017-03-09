---
title: "保存数据 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DataRow.RowState"
  - "DataSet.GetChanges"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "数据 [Visual Studio], 保存"
  - "数据 [Visual Studio], 更新"
  - "数据库, 更新"
  - "DBDirect 方法"
  - "保存数据"
  - "TableAdapter DBDirect 方法"
  - "TableAdapter.Update 方法"
  - "更新数据"
  - "更新数据库"
ms.assetid: 21d2b115-62e4-4ac9-a873-dcbb535b8af8
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# 保存数据
保存数据就是将应用程序的数据模型中的已更改数据保存回原始数据存储区（通常是关系数据库，如 SQL Server）的过程。  
  
 通过数据模型更新数据源通常是一个包含两个步骤的过程。  第一步是使用新信息（新记录、已更改的记录或已删除的记录）更新数据模型。  第二步是将在数据模型中的更改保存回数据库。  
  
 下列主题将描述与保存数据相关的概念和任务。  
  
## 相关主题  
 [将数据保存在数据集中](../data-tools/save-data-back-to-the-database.md)  
 提供有关如何在数据集中进行更改以及数据集如何跟踪更改信息以将这些更改保存到数据库的概述。  
  
 [保存实体数据](../data-tools/saving-entity-data.md)  
 介绍如何在 [ADO.NET 实体框架](../Topic/ADO.NET%20Entity%20Framework.md)和 [WCF 数据服务 4.5](../Topic/WCF%20Data%20Services%204.5.md)应用程序中保存更改。