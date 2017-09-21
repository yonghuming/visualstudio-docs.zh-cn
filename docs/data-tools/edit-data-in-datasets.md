---
title: "编辑数据集中的数据 | Microsoft Docs"
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
  - "数据 [Visual Studio], 在数据集中编辑"
  - "数据集 [Visual Basic], 编辑数据"
ms.assetid: 50d5c580-fbf7-408f-be70-e63ac4f4d0eb
caps.latest.revision: 15
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 编辑数据集中的数据
编辑 <xref:System.Data.DataSet> 中的数据是在组成数据集的单个 <xref:System.Data.DataTable> 对象中操作实际数据的过程。  在数据表中编辑数据几乎与在任何数据库的表中编辑数据一样 — 该过程可包括插入、更新和删除表中的记录。  
  
 除了更改实际数据外，还可以查询 <xref:System.Data.DataTable> 以返回特定的数据行，如单个行、特定版本行（原始的和建议的）、仅更改过的行以及有错误的行。  
  
## 公共数据表任务  
 下表提供与数据集中编辑和查询数据关联的常规任务的链接：  
  
|任务|描述|  
|--------|--------|  
|将新记录插入到数据表中。|创建新的 <xref:System.Data.DataRow> 并将其添加到表的行集合中。  有关详细信息，请参阅[如何：向数据表中添加行](../Topic/How%20to:%20Add%20Rows%20to%20a%20DataTable.md)。|  
|更新数据表中现有的记录。|将值直接分配到数据行的特定列。  有关详细信息，请参阅[如何：编辑数据表中的行](../Topic/How%20to:%20Edit%20Rows%20in%20a%20DataTable.md)。|  
|从数据表中删除现有记录|调用要从表中移除的数据行的 <xref:System.Data.DataRow.Delete%2A> 方法。  有关详细信息，请参阅[如何：删除数据表中的行](../Topic/How%20to:%20Delete%20Rows%20in%20a%20DataTable.md)。|  
|定位数据表中已更改的记录。|调用数据表的 <xref:System.Data.DataTable.GetChanges%2A> 方法。  有关详细信息，请参阅[如何：检索已更改的行](../Topic/How%20to:%20Retrieve%20Changed%20Rows.md)。|  
|访问数据表中不同版本的行。|通过在要查看的 <xref:System.Data.DataRowVersion> 中传递，访问数据行的单个列。  有关详细信息，请参阅[如何：获取 DataRow 的特定版本](../Topic/How%20to:%20Get%20Specific%20Versions%20of%20a%20DataRow.md)。|  
|定位数据表中有错误的行。|检查数据表的 <xref:System.Data.DataTable.HasErrors%2A> 属性。  有关详细信息，请参阅[如何：定位出错的行](../Topic/How%20to:%20Locate%20Rows%20that%20Have%20Errors.md)。|  
  
## 请参阅  
 [DataTable](../Topic/DataTables.md)   
 [准备应用程序以接收数据](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [将数据获取到应用程序](../data-tools/fetching-data-into-your-application.md)   
 [在应用程序中编辑数据](../data-tools/editing-data-in-your-application.md)   
 [DataTable](../Topic/DataTables.md)   
 [数据演练](../Topic/Data%20Walkthroughs.md)   
 [在 Visual Studio 中将 Windows 窗体控件绑定到数据](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Visual Studio 的数据应用程序概述](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [连接到 Visual Studio 中的数据](../data-tools/connecting-to-data-in-visual-studio.md)   
 [在 Visual Studio 中将控件绑定到数据](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [验证数据](../Topic/Validating%20Data.md)   
 [保存数据](../data-tools/saving-data.md)