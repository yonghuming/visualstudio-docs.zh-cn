---
title: "如何：扩展 TableAdapter 的功能 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
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
  - "数据 [Visual Studio], 扩展 TableAdapter"
  - "数据 [Visual Studio], TableAdapter"
  - "TableAdapter, 添加功能"
ms.assetid: 418249c8-c7f3-47ef-a94c-744cb6fe6aaf
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：扩展 TableAdapter 的功能
您可以通过将代码添加到 TableAdapter 的分部类文件，扩展 TableAdapter 的功能。  
  
 如果对 TableAdapter（在**“数据集设计器”**中）进行任何更改，或在运行任何修改 TableAdapter 配置的向导期间进行更改，都会重新生成定义 TableAdapter 的代码。  要避免在重新生成 TableAdapter 期间删除代码，请将代码添加至 TableAdapter 的分部类文件中。  
  
 （分部类允许将特定类的代码划分到多物理文件中。  有关更多信息，请参见 [分部](/dotnet/visual-basic/language-reference/modifiers/partial) 或 [分部（类型）](/dotnet/csharp/language-reference/keywords/partial-type)。）  
  
## 定位代码中的 TableAdapter  
 TableAdapter 是使用**“数据集设计器”**设计的，但生成的 TableAdapter 类并不是作为 <xref:System.Data.DataSet> 的嵌套类生成的。  根据与 TableAdapter 相关的数据集的名称，TableAdapter 位于某个命名空间中。  例如，如果应用程序包含一个名为 `HRDataSet` 的数据集，则 TableAdapter 将位于 `HRDataSetTableAdapters` 命名空间中。  （命名约定遵循以下模式：*DatasetName* \+ `TableAdapters`）。  
  
 下面的示例假设一个在具有 `NorthwindDataSet` 的项目中名为 `CustomersTableAdapter` 的 TableAdapter。  
  
#### 创建 TableAdapter 的分部类  
  
1.  通过从**“项目”**菜单中选择**“添加类”**，将一个新类添加到项目中。  
  
2.  将该类命名为 `CustomersTableAdapterExtended`。  
  
3.  单击**“添加”**。  
  
4.  用项目的正确命名空间和分部类名代替此代码。  例如：  
  
     [!CODE [VbRaddataTableAdapters#2](../CodeSnippet/VS_Snippets_VBCSharp/VbRaddataTableAdapters#2)]  
  
## 请参阅  
 [TableAdapter 概述](../data-tools/tableadapter-overview.md)   
 [如何：创建 TableAdapter](../data-tools/create-and-configure-tableadapters.md)   
 [如何：创建 TableAdapter 查询](../data-tools/how-to-create-tableadapter-queries.md)   
 [如何：扩展数据集的功能](../Topic/How%20to:%20Extend%20the%20Functionality%20of%20a%20Dataset.md)   
 [数据演练](../Topic/Data%20Walkthroughs.md)   
 [在 Visual Studio 中将 Windows 窗体控件绑定到数据](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Visual Studio 的数据应用程序概述](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [连接到 Visual Studio 中的数据](../data-tools/connecting-to-data-in-visual-studio.md)   
 [准备应用程序以接收数据](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [将数据获取到应用程序](../data-tools/fetching-data-into-your-application.md)   
 [在 Visual Studio 中将控件绑定到数据](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [在应用程序中编辑数据](../data-tools/editing-data-in-your-application.md)   
 [验证数据](../Topic/Validating%20Data.md)   
 [保存数据](../data-tools/saving-data.md)