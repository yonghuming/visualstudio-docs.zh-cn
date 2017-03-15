---
title: "如何：创建参数化 TableAdapter 查询 | Microsoft Docs"
ms.custom: ""
ms.date: "09/21/2016"
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
  - "数据 [Visual Studio], 搜索数据"
  - "数据 [Visual Studio], TableAdapter"
  - "查询 [Visual Studio], 创建"
  - "查询 [Visual Studio], TableAdapter"
  - "TableAdapter, 参数化查询"
  - "TableAdapter, 搜索数据"
ms.assetid: 104d1d19-b5a9-4071-b81e-1b3af08e9c7b
caps.latest.revision: 20
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：创建参数化 TableAdapter 查询
参数化查询将返回满足查询内的 WHERE 子句条件的数据。  例如，通过在返回客户列表的 SQL 语句的末尾添加 `WHERE City = @City`，可以参数化客户列表，使之只显示某个城市的客户。  
  
 你可以在[数据集设计器](../data-tools/creating-and-editing-typed-datasets.md)中创建参数化的 TableAdapter 查询，或在 Windows 应用程序中创建数据绑定窗体时使用**“数据”**菜单上的**“参数化数据源”**命令创建该类查询。  **“参数化数据源”**命令还将在窗体上创建控件，以供输入参数值和执行查询。  有关详细信息，请参阅[“搜索标准生成器”对话框](../Topic/Search%20Criteria%20Builder%20Dialog%20Box.md)。  
  
> [!NOTE]
>  构造参数化查询时，请使用特定于你正在对其编写代码的数据库的参数表示法。  例如，Access 和 OleDb 数据源使用问号“?”表示参数，所以 WHERE 子句将类似于：`WHERE City = ?`。  
  
> [!NOTE]
>  显示的对话框和菜单命令可能会与“帮助”中的描述不同，具体取决于你现用的设置或版本。  若要更改设置，请在**“工具”**菜单上选择**“导入和导出设置”**。  有关详细信息，请参阅[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-cn/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
## 创建参数化 TableAdapter 查询  
  
#### 在“数据集设计器”中创建参数化查询  
  
-   将 WHERE 子句和所需参数添加到 SQL 语句中，以创建新的 TableAdapter。  有关详细信息，请参阅[如何：创建 TableAdapter](../data-tools/create-and-configure-tableadapters.md)。  
  
     \- 或 \-  
  
-   将 WHERE 子句和所需参数添加到 SQL 语句中，以向现有 TableAdapter 中添加查询。  有关详细信息，请参阅[如何：创建 TableAdapter 查询](../data-tools/how-to-create-tableadapter-queries.md)。  
  
#### 在设计数据绑定窗体时创建参数化查询  
  
1.  在窗体中选择已绑定到数据集的控件。  有关详细信息，请参阅[在 Visual Studio 中将 Windows 窗体控件绑定到数据](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)。  
  
2.  在**“数据”**菜单上，单击**“添加查询”**。  
  
3.  将 WHERE 语句和所需参数添加到 SQL 语句中，以完成**“查询标准生成器”**对话框。  有关详细信息，请参阅[“搜索标准生成器”对话框](../Topic/Search%20Criteria%20Builder%20Dialog%20Box.md)。  
  
## 请参阅  
 [TableAdapter](../Topic/TableAdapters.md)   
 [连接到 Visual Studio 中的数据](../data-tools/connecting-to-data-in-visual-studio.md)   
 [准备应用程序以接收数据](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [将数据获取到应用程序](../data-tools/fetching-data-into-your-application.md)   
 [在 Visual Studio 中将控件绑定到数据](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [在应用程序中编辑数据](../data-tools/editing-data-in-your-application.md)   
 [验证数据](../Topic/Validating%20Data.md)   
 [保存数据](../data-tools/saving-data.md)   
 [数据演练](../Topic/Data%20Walkthroughs.md)