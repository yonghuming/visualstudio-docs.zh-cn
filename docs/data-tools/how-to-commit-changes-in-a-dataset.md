---
title: "如何：提交数据集中的更改 | Microsoft Docs"
ms.custom: ""
ms.date: "09/21/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DataSet.AcceptChanges"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "数据集 [Visual Basic], 提交更改"
ms.assetid: 51931353-4d22-4e35-a9ef-6f2b44e1f7d9
caps.latest.revision: 17
caps.handback.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# 如何：提交数据集中的更改
当您通过更新、插入和删除记录对数据集中的记录作出更改时，数据集将维护记录的初始版本和当前版本。  此外，每行的 <xref:System.Data.DataRow.RowState%2A> 属性将跟踪记录是否处于其初始状态，或者是否已对其执行更新、插入或删除操作。  当需要查找行的特定版本时，该信息将非常有用。  通常，您会获取所有已更改记录的一个子集，以发送给另一个进程。  有关更多信息，请参见 [如何：检索已更改的行](../Topic/How%20to:%20Retrieve%20Changed%20Rows.md)。  在处理完所有已更改的行之后，您可以通过调用 <xref:System.Data.DataSet>、<xref:System.Data.DataTable> 或 <xref:System.Data.DataRow> 的 `AcceptChanges` 方法提交更改。  `AcceptChanges` 方法在调用 [TableAdapter](../data-tools/tableadapter-overview.md) 或数据适配器的更新方法时自动调用。  在提交对数据库的更改后调用 `AcceptChanges`。  
  
 当对 <xref:System.Data.DataSet> 调用 <xref:System.Data.DataSet.AcceptChanges%2A> 时，任何仍处于编辑模式的 <xref:System.Data.DataRow> 对象都将成功结束其编辑。  每个 <xref:System.Data.DataRow> 的 <xref:System.Data.DataRow.RowState%2A> 属性也都更改；<xref:System.Data.DataRowState> 和 <xref:System.Data.DataRowState> 行变为 <xref:System.Data.DataRowState>，<xref:System.Data.DataRowState> 行被移除。  
  
 如果 <xref:System.Data.DataSet> 包含 <xref:System.Data.ForeignKeyConstraint> 对象，则调用 <xref:System.Data.DataSet.AcceptChanges%2A> 方法还将导致强制实施 <xref:System.Data.AcceptRejectRule>。  
  
### 提交数据集中的更改  
  
-   对 <xref:System.Data.DataSet>、<xref:System.Data.DataTable> 或 <xref:System.Data.DataRow> 调用 `AcceptChanges` 方法以提交这些对象中的更改。  
  
     下面的示例演示如何在更新数据源之后调用 `AcceptChanges` 方法来提交 `Customers` 表中的更改：  
  
     [!CODE [VbRaddataEditing#11](../CodeSnippet/VS_Snippets_VBCSharp/VbRaddataEditing#11)]  
  
## 请参阅  
 <xref:System.Data.DataSet.AcceptChanges%2A?displayProperty=fullName>   
 <xref:System.Data.DataTable.AcceptChanges%2A?displayProperty=fullName>   
 <xref:System.Data.DataRow.AcceptChanges%2A?displayProperty=fullName>   
 [保存数据](../data-tools/saving-data.md)   
 [如何：检索已更改的行](../Topic/How%20to:%20Retrieve%20Changed%20Rows.md)