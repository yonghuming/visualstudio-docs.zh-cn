---
title: "演练：在数据集设计器中创建数据表 | Microsoft Docs"
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
  - "数据 [Visual Studio], 数据集设计器"
  - "数据集设计器, 创建数据表"
  - "DataTable 对象, 创建"
  - "表 [Visual Studio], 创建"
ms.assetid: abf0a2b5-e4e5-422e-97ef-55a0e35a82df
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# 演练：在数据集设计器中创建数据表
此演练解释如何使用**“数据集设计器”**创建 <xref:System.Data.DataTable>（没有 TableAdapter）。  有关创建包含 TableAdapter 的数据表的信息，请参见[如何：创建 TableAdapter](../data-tools/create-and-configure-tableadapters.md)。  
  
 本演练涉及以下任务：  
  
-   创建新的“Windows 应用程序”项目  
  
-   将新的数据集添加到应用程序中  
  
-   向数据集添加新的数据表  
  
-   向数据表添加列  
  
-   为表设置主键  
  
## 创建新的 Windows 应用程序  
  
#### 创建新的 Windows 应用程序项目  
  
1.  从**“文件”**菜单创建一个新的项目。  
  
2.  在**“项目类型”**窗格中选择一种编程语言。  
  
3.  在**“模板”**窗格中单击**“Windows 应用程序”**。  
  
4.  将项目命名为`“DataTableWalkthrough”`，然后单击**“确定”**。  
  
     Visual Studio 会将该项目添加到**“解决方案资源管理器”**并在设计器中显示**“Form1”**。  
  
## 将新的数据集添加到应用程序中  
  
#### 向项目添加新的数据集项  
  
1.  在**“项目”**菜单上，单击**“添加新项”**。  
  
     随即出现“添加新项”对话框。  
  
2.  在**“模板”**框中选择**“数据集”**。  
  
3.  单击**“添加”**。  
  
     Visual Studio 将向项目中添加一个名为**“Dataset1.xsd”**的文件，并在**“数据集设计器”**中将其打开。  
  
## 将新的数据表添加到数据集中  
  
#### 向数据集添加新的数据表  
  
1.  将一个**“DataTable”**从**“工具箱”**的**“数据集”**选项卡拖动到**“数据集设计器”**。  
  
     将一个名为**“DataTable1”**的表添加到了该数据集中。  
  
    > [!NOTE]
    >  若要创建包含 TableAdapter 的数据表，请参见[演练：创建带有多个查询的 TableAdapter](../data-tools/walkthrough-creating-a-tableadapter-with-multiple-queries.md)。  
  
2.  单击**“DataTable1”**的标题栏并将其重命名为`“Music”`。  
  
## 向数据表添加列  
  
#### 向数据表添加列  
  
1.  右击**“Music”**表。  指向**“添加”**，然后单击**“列”**。  
  
2.  将此列命名为`“SongID”`命名。  
  
3.  在**“属性”**窗口中，将 <xref:System.Data.DataColumn.DataType%2A> 属性设置为 <xref:System.Int16?displayProperty=fullName>。  
  
4.  重复此过程添加下面的列：  
  
     `SongTitle`：<xref:System.String?displayProperty=fullName>  
  
     `Artist`：<xref:System.String?displayProperty=fullName>  
  
     `Genre`：<xref:System.String?displayProperty=fullName>  
  
## 为表设置主键  
 所有的数据表都应有一个主键。  主键唯一地标识数据表中的记录。  
  
#### 设置数据表的主键  
  
-   右击**“SongID”**列，然后单击**“设置主键”**。  
  
     在**“SongID”**列的旁边将显示钥匙图标。  
  
## 保存项目  
  
#### 保存 DataTableWalkthrough 项目  
  
-   在**“文件”**菜单上，单击**“全部保存”**。  
  
## 后续步骤  
 既然已经创建了表，您可能希望执行下列操作之一：  
  
|若要|请参见|  
|--------|---------|  
|创建窗体以输入数据|[演练：在 Windows 窗体上显示数据](../data-tools/walkthrough-displaying-data-on-a-windows-form.md).|  
|向表中添加数据|[向数据表中添加数据](../Topic/Adding%20Data%20to%20a%20DataTable.md).|  
|查看表中的数据|[查看数据表中的数据](../Topic/Viewing%20Data%20in%20a%20DataTable.md).|  
|编辑数据|[DataTable 编辑](../Topic/DataTable%20Edits.md)|  
|删除表中的行|[DataRow 删除](../Topic/DataRow%20Deletion.md)|  
  
## 请参阅  
 [连接到 Visual Studio 中的数据](../data-tools/connecting-to-data-in-visual-studio.md)   
 [准备应用程序以接收数据](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [将数据获取到应用程序](../data-tools/fetching-data-into-your-application.md)   
 [在 Visual Studio 中将控件绑定到数据](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [在应用程序中编辑数据](../data-tools/editing-data-in-your-application.md)   
 [验证数据](../Topic/Validating%20Data.md)   
 [保存数据](../data-tools/saving-data.md)   
 [数据演练](../Topic/Data%20Walkthroughs.md)