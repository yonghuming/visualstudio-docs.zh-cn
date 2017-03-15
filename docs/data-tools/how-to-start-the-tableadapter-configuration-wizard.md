---
title: "如何：启动 TableAdapter 配置向导 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "TableAdapter 配置向导"
  - "TableAdapter, 配置向导"
ms.assetid: 301f2dcd-ed72-4229-80ef-3b59cb062d5d
caps.latest.revision: 11
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# 如何：启动 TableAdapter 配置向导
**“TableAdapter 配置向导”**在强类型数据集中创建和编辑 TableAdapter。  该向导根据输入到向导中的 SQL 语句或数据库中现有的存储过程来创建 TableAdapter。  该向导还可以根据输入到向导中的 SQL 语句在数据库中创建新的存储过程。  
  
### 启动 TableAdapter 配置向导创建新的 TableAdapter  
  
1.  在**“数据集设计器”**中打开你的数据集。  有关详细信息，请参阅[如何：在数据集设计器中打开数据集](../Topic/How%20to:%20Open%20a%20Dataset%20in%20the%20Dataset%20Designer.md)。  
  
    > [!NOTE]
    >  如果项目中没有数据集，请参阅[如何：创建类型化数据集](../data-tools/create-and-configure-datasets-in-visual-studio.md)。  
  
2.  如果要创建新的 TableAdapter，请将**“TableAdapter”**对象从**“工具箱”**的**“数据集”**选项卡拖到**“数据集设计器”**上。  
  
3.  在**“选择你的数据连接”**页面上，从当前可用连接的列表中选择数据连接，或选择**“新建连接”**创建一个新连接。  
  
### 启动 TableAdapter 配置向导编辑现有 TableAdapter  
  
1.  在**“数据集设计器”**中打开你的数据集。  有关详细信息，请参阅[如何：在数据集设计器中打开数据集](../Topic/How%20to:%20Open%20a%20Dataset%20in%20the%20Dataset%20Designer.md)。  
  
2.  在**“数据集设计器”**中，右键单击 TableAdapter，然后选择**“配置”**。  该向导将打开到**“生成 SQL 语句”**页面或**“将命令绑定到现有存储过程”**页面，具体取决于 TableAdapter 的最初配置方式。  
  
3.  完成该向导。  
  
## 请参阅  
 [数据演练](../Topic/Data%20Walkthroughs.md)   
 [在 Visual Studio 中将 Windows 窗体控件绑定到数据](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [TableAdapter 概述](../data-tools/tableadapter-overview.md)   
 [创建和编辑类型化数据集](../data-tools/creating-and-editing-typed-datasets.md)   
 [数据源概述](../data-tools/add-new-data-sources.md)   
 [如何：连接到数据库中的数据](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [验证数据](../Topic/Validating%20Data.md)   
 [如何：使用 Windows 窗体 BindingSource 组件对 ADO.NET 数据进行排序和筛选](../Topic/How%20to:%20Sort%20and%20Filter%20ADO.NET%20Data%20with%20the%20Windows%20Forms%20BindingSource%20Component.md)   
 [如何：使用 Windows 窗体 BindingSource 组件创建查找表](../Topic/How%20to:%20Create%20a%20Lookup%20Table%20with%20the%20Windows%20Forms%20BindingSource%20Component.md)   
 [演练：在 Windows 窗体上显示数据](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)