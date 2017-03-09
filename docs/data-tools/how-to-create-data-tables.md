---
title: "如何：创建数据表 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Microsoft.VSDesigner.DataSource.DesignTable"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "数据 [Visual Studio], 创建数据表"
  - "数据集设计器, 创建数据表"
  - "表 [Visual Studio], 创建"
ms.assetid: 0e8bf4c4-3d05-4b20-9926-9d29914b26ed
caps.latest.revision: 19
caps.handback.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# 如何：创建数据表
数据可以存储在 <xref:System.Data.DataTable> 对象的内存中。（数据集由 <xref:System.Data.DataTable> 对象组成。）通常使用 [TableAdapter 配置向导](../Topic/TableAdapter%20Configuration%20Wizard.md) 或通过将数据库对象从**“服务器资源管理器”**拖动到**“数据集设计器”**用 TableAdapter 创建新数据表。  
  
 数据表是在 [数据源配置向导](../data-tools/media/data-source-configuration-wizard.png) 中创建新的 TableAdapter 时作为副产品创建的，但也可单独创建。  通过将 <xref:System.Data.DataTable> 对象从**“工具箱”**的**“数据集”**选项卡拖动到**“数据集设计器”**可以创建单独的数据表。  
  
> [!NOTE]
>  若要以编程方式创建数据表，请参见 [创建 DataTable](../Topic/Creating%20a%20DataTable.md)。  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## 随 TableAdapter 一起创建 DataTable  
 与 TableAdapter 一起创建的数据表中包括以数据填充表和将更改重新写入数据库的方法。  通过运行**“TableAdapter 配置向导”**或通过将数据库对象从**“服务器资源管理器”**拖动到**“数据集设计器”**可以创建 TableAdapter。  
  
#### 随 TableAdapter 一起创建新数据表  
  
1.  在**“数据集设计器”**中打开您的数据集。  有关信息，请参见 [如何：在数据集设计器中打开数据集](../Topic/How%20to:%20Open%20a%20Dataset%20in%20the%20Dataset%20Designer.md)。  
  
2.  将一个**“TableAdapter”**从**“工具箱”**的**“数据集”**选项卡拖动到**“数据集设计器”**。  
  
     **“TableAdapter 配置向导”**打开。  
  
3.  完成该向导。  有关更多信息，请参阅[TableAdapter 配置向导](../Topic/TableAdapter%20Configuration%20Wizard.md)。  
  
#### 在“服务器资源管理器”中随 TableAdapter 一起创建新数据表  
  
1.  在**“数据源设计器”**中打开您的数据集。  
  
2.  将数据库对象（例如表）从**“服务器资源管理器”**拖动到**“数据集设计器”**上。  
  
## 创建单独的 DataTable  
 为了填充数据，单独的表需要实现 `Fill` 逻辑。  有关填充单独的数据表的信息，请参见 [从 DataAdapter 填充 DataSet](../Topic/Populating%20a%20DataSet%20from%20a%20DataAdapter.md)。  
  
#### 创建新的单独数据表  
  
1.  在**“数据集设计器”**中打开您的数据集。  
  
2.  将一个 <xref:System.Data.DataTable> 从**“工具箱”**的**“数据集”**选项卡拖动到**“数据集设计器”**上。  
  
3.  添加列以定义数据表。  有关详细信息，请参阅[如何：向数据表添加列](../Topic/How%20to:%20Add%20Columns%20to%20a%20DataTable.md)。  
  
## 请参阅  
 <xref:System.Data.DataTable>   
 [数据演练](../Topic/Data%20Walkthroughs.md)   
 [演练：在 Windows 窗体上显示数据](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)   
 [TableAdapter 概述](../data-tools/tableadapter-overview.md)   
 [创建和编辑类型化数据集](../data-tools/creating-and-editing-typed-datasets.md)   
 [数据源概述](../data-tools/add-new-data-sources.md)   
 [“数据源”窗口](../Topic/Data%20Sources%20Window.md)   
 [如何：连接到数据库中的数据](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [验证数据](../Topic/Validating%20Data.md)