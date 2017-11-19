---
title: "将代码添加到在 n 层应用程序中的数据集 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords: n-tier applications, extending datasets
ms.assetid: d43c2ccd-4902-43d8-b1a8-d10ca5d3210c
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 26dd5500f50b185c31809d9882e03e56541a567a
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2017
---
# <a name="add-code-to-datasets-in-n-tier-applications"></a>将代码添加到在 n 层应用程序中的数据集
你可通过创建数据集分部类文件并将代码添加到其扩展数据集的功能 (而不是将代码添加到*DatasetName*。Dataset.Designer 文件）。 分部类可以使划分到多个物理文件的特定类的代码。 有关详细信息，请参阅[部分](/dotnet/visual-basic/language-reference/modifiers/partial)或[分部类和方法](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)。  
  
每次对 （在类型化数据集） 的数据集定义进行更改，则生成的代码定义数据集。 修改数据集配置任何向导运行过程中进行更改时，也会生成此代码。 若要防止在数据集重新生成过程正在删除你的代码，请将代码添加到数据集的分部类文件。  
  
默认情况下，分隔的数据集和 TableAdapter 代码后结果将是离散的类文件中的每个项目。 原始的项目将包含名为的文件*DatasetName*。Designer.vb (或*DatasetName*。Designer.cs)，其中包含 TableAdapter 代码。 中指定的项目**数据集项目**属性包含一个名为*DatasetName*。DataSet.Designer.vb (或*DatasetName*。DataSet.Designer.cs)。此文件包含的数据集代码。  
  
> [!NOTE]
>  当你将数据集和 Tableadapter (通过设置**数据集项目**属性)，将不会自动移动项目中的现有数据集分部类。 到数据集项目，必须手动移动现有数据集分部类。  
  
> [!NOTE]
>  类型化数据集时需要添加验证代码，提供用于生成功能<xref:System.Data.DataTable.ColumnChanging>和<xref:System.Data.DataTable.RowChanging>事件处理程序。 有关详细信息，请参阅[向 n 层数据集添加验证](../data-tools/add-validation-to-an-n-tier-dataset.md)。  
  
## <a name="to-add-code-to-datasets-in-n-tier-applications"></a>若要将代码添加到在 n 层应用程序中的数据集  
  
1.  找到包含.xsd 文件的项目。 
  
2.  选择**.xsd**文件以打开该数据集。  
  
3.  右键单击你想要添加代码 （表标题栏中名称），，然后选择的数据表**查看代码**。  
  
     分部类创建，并在代码编辑器中打开。  
  
4.  添加代码的分部类声明。  
  
     下面的示例演示如何将代码添加到 NorthwindDataSet 中 CustomersDataTable:  
  
    ```vb  
    Partial Public Class CustomersDataTable  
        ' Add code here to add functionality   
        ' to the CustomersDataTable.  
    End Class  
    ```    
    ```csharp  
    partial class CustomersDataTable  
    {  
        // Add code here to add functionality  
        // to the CustomersDataTable.  
    }  
    ```  
  
## <a name="see-also"></a>请参阅
[N 层数据应用程序概述](../data-tools/n-tier-data-applications-overview.md)   
[向 N 层应用程序中的 TableAdapter 添加代码](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md)  
[创建和配置 Tableadapter](create-and-configure-tableadapters.md)  
[分层更新概述](hierarchical-update.md)     
[Visual Studio 中的数据集工具](../data-tools/dataset-tools-in-visual-studio.md)