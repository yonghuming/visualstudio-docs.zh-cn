---
title: "关于异常的疑难解答：System.Data.NoNullAllowedException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "NoNullAllowedException 类"
ms.assetid: 1ab87572-007f-4b84-bb13-c3626e7f89cd
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 关于异常的疑难解答：System.Data.NoNullAllowedException
尝试向 <xref:System.Data.NoNullAllowedException> 设置为 <xref:System.Data.DataColumn.AllowDBNull%2A> 的列中插入 null 值时，将引发 `false` 异常。  
  
## 相关提示  
 **先检查以确定值是否为 DBNull，然后再将它添加到列中。**  
 如果 <xref:System.Data.DataColumn.AllowDBNull%2A> 设置为 `false`，将不能插入 null 值。 有关更多信息，请参见<xref:System.DBNull>。  
  
 **将 AllowDBNull 设置为 True。**  
 将此属性设置为 `true` 将允许插入 null 值。 有关详细信息，请参阅<xref:System.Data.DataColumn.AllowDBNull%2A>。  
  
## 备注  
 如果使用导航按钮在数据窗体上的数据库表的记录之间移动，则可能会引发此异常，并显示附加信息：“列‘Column’不允许空值。” 此行为的发生是由于在“数据窗体向导”中未选择数据库表的主键或“非 NULL”列。 如果创建数据窗体时在“数据窗体向导”中未选择数据库的主键或“非 NULL”列，则不会禁用**“添加 \- 创建一条新记录”**选项。 若要解决此问题，请在添加数据窗体时通过使用“数据窗体向导”选择所选表中的以下列：主列和不允许 NULL 的列。  
  
## 请参阅  
 <xref:System.Data.NoNullAllowedException>   
 <xref:System.Data.DataRowCollection.Add%2A>   
 <xref:System.Data.DataRow.EndEdit%2A>   
 <xref:System.Data.DataRow.ItemArray%2A>   
 <xref:System.Data.DataTable.LoadDataRow%2A>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)