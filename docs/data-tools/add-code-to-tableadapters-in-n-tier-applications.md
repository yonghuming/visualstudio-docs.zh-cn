---
title: "如何：向 N 层应用程序中的 TableAdapter 添加代码 | Microsoft Docs"
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
  - "n 层应用程序, 扩展 TableAdapter"
  - "TableAdapter, n 层应用程序"
ms.assetid: dafac00e-df9d-4d4a-95a6-e34b4d099425
caps.latest.revision: 19
caps.handback.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：向 N 层应用程序中的 TableAdapter 添加代码
通过创建分部类文件 `TableAdapter` 并向其中添加代码（而不是向 *数据集名称*.DataSet.Designer 文件中添加代码），可以扩展 `TableAdapter` 的功能。  （分部类可帮助将特定类的代码划分到多个物理文件中。  有关更多信息，请参见 [分部](/dotnet/visual-basic/language-reference/modifiers/partial) 或 [分部（类型）](/dotnet/csharp/language-reference/keywords/partial-type)。）  
  
 每次更改 `TableAdapter`（在[创建和编辑类型化数据集](../data-tools/creating-and-editing-typed-datasets.md)中）时，都会生成定义 `TableAdapter` 的代码。  此外，在运行修改 `TableAdapter` 的配置的任何向导期间，进行修改也会生成此代码。  若要防止在重新生成 `TableAdapter` 期间删除代码，请向 `TableAdapter` 的分部类文件中添加代码。  
  
 默认情况下，分离数据集和 `TableAdapter` 代码后，每个项目中将包含一个独立的类文件。  原始项目将包含一个名为 *数据集名称*.Designer.vb（或 *数据集名称*.Designer.cs）的文件，其中含有 `TableAdapter` 代码。  **“数据集项目”**属性中指定的项目将包含一个名为 *数据集名称*.DataSet.Designer.vb（或 *数据集名称*.DataSet.Designer.cs）的文件，其中含有数据集代码。  
  
> [!NOTE]
>  分离数据集与 `TableAdapter` 时（通过设置**“数据集项目”**属性），将不会自动移动项目中现有的数据集分部类。  您必须手动将它们移到数据集项目中。  
  
> [!NOTE]
>  [创建和编辑类型化数据集](../data-tools/creating-and-editing-typed-datasets.md)还可在应添加验证代码时生成 <xref:System.Data.DataTable.ColumnChanging> 和 <xref:System.Data.DataTable.RowChanging> 事件处理程序。  有关更多信息，请参见[如何：向 N 层数据集添加验证](../data-tools/add-validation-to-an-n-tier-dataset.md)。  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
### 向 n 层应用程序的 TableAdapter 添加用户代码  
  
1.  查找包含 .xsd 文件的项目（[创建和编辑类型化数据集](../data-tools/creating-and-editing-typed-datasets.md)）。  
  
2.  双击**“.xsd”**文件以打开[创建和编辑类型化数据集](../data-tools/creating-and-editing-typed-datasets.md)。  
  
3.  右击要向其添加代码的 `TableAdapter`，然后单击**“查看代码”**。  
  
     此时将创建一个分部类，并在代码编辑器中打开。  
  
4.  在分部类声明中添加代码。  
  
5.  下面的示例演示在 `NorthwindDataSet` 中向 `CustomersTableAdapter` 添加代码的位置：  
  
    ```vb#  
    Partial Public Class CustomersTableAdapter  
        ' Add code here to add functionality   
        ' to the CustomersTableAdapter.  
    End Class  
    ```  
  
    ```c#  
    public partial class CustomersTableAdapter  
    {  
        // Add code here to add functionality  
        // to the CustomersTableAdapter.  
    }  
    ```  
  
## 请参阅  
 [N 层数据应用程序概述](../data-tools/n-tier-data-applications-overview.md)   
 [如何：向 N 层应用程序的数据集添加代码](../data-tools/add-code-to-datasets-in-n-tier-applications.md)   
 [TableAdapter](../Topic/TableAdapters.md)   
 [TableAdapterManager 概述](../Topic/TableAdapterManager%20Overview.md)   
 [分层更新概述](../Topic/Hierarchical%20Update%20Overview.md)   
 [创建数据应用程序](../data-tools/creating-data-applications.md)