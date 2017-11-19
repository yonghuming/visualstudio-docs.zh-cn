---
title: "在 n 层应用程序中的 Tableadapter 添加代码 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- TableAdapters, n-tier applications
- n-tier applications, extending TableAdapters
ms.assetid: dafac00e-df9d-4d4a-95a6-e34b4d099425
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 396e1132015c2eb37f06095f135dae878bfeb574
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2017
---
# <a name="add-code-to-tableadapters-in-n-tier-applications"></a>在 n 层应用程序中的 Tableadapter 添加代码
你可以通过为 TableAdapter 创建分部类文件并将代码添加到它扩展 TableAdapter 的功能 (而不是将代码添加到*DatasetName*。DataSet.Designer 文件）。 分部类可以使划分到多个物理文件的特定类的代码。 有关详细信息，请参阅[部分](/dotnet/visual-basic/language-reference/modifiers/partial)或[分部 （类型）](/dotnet/csharp/language-reference/keywords/partial-type)。  
  
每次对数据集中 TableAdapter 进行更改，则生成定义 TableAdapter 的代码。 修改的 TableAdapter 配置任何向导运行期间进行更改时，也会生成此代码。 若要防止在 TableAdapter 的重新生成过程正在删除你的代码，请将代码添加到 TableAdapter 的分部类文件。  
  
默认情况下，分隔的数据集和 TableAdapter 代码后结果将是离散的类文件中的每个项目。 原始的项目将包含名为的文件*DatasetName*。Designer.vb (或*DatasetName*。Designer.cs)，其中包含 TableAdapter 代码。 中指定的项目**数据集项目**属性具有名为的文件*DatasetName*。DataSet.Designer.vb (或*DatasetName*。DataSet.Designer.cs)，其中包含数据集代码。  
  
> [!NOTE]
>  当你将数据集和 Tableadapter (通过设置**数据集项目**属性)，将不会自动移动项目中的现有数据集分部类。 到数据集项目，必须手动移动现有数据集分部类。  
  
> [!NOTE]
>  数据集提供了用于生成功能<xref:System.Data.DataTable.ColumnChanging>和<xref:System.Data.DataTable.RowChanging>事件处理程序时需要验证。 有关详细信息，请参阅[向 n 层数据集添加验证](../data-tools/add-validation-to-an-n-tier-dataset.md)。  
  
[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## <a name="to-add-user-code-to-a-tableadapter-in-an-n-tier-application"></a>若要将用户代码添加到在 n 层应用程序 TableAdapter  
  
1.  找到包含.xsd 文件的项目。
  
2.  双击**.xsd**文件以打开**数据集设计器**。  
  
3.  右键单击你想要将代码添加到，然后选择 TableAdapter**查看代码**。  
  
     分部类创建，并在代码编辑器中打开。  
  
4.  添加代码的分部类声明。  
  
5.  下面的示例演示如何将代码添加到`CustomersTableAdapter`中`NorthwindDataSet`:  
  
    ```vb  
    Partial Public Class CustomersTableAdapter  
        ' Add code here to add functionality   
        ' to the CustomersTableAdapter.  
    End Class  
    ```  
  
    ```csharp  
    public partial class CustomersTableAdapter  
    {  
        // Add code here to add functionality  
        // to the CustomersTableAdapter.  
    }  
    ```  
  
## <a name="see-also"></a>请参阅
[N 层数据应用程序概述](../data-tools/n-tier-data-applications-overview.md)   
[将代码添加到在 n 层应用程序中的数据集](../data-tools/add-code-to-datasets-in-n-tier-applications.md)   
[创建和配置 Tableadapter](create-and-configure-tableadapters.md)   
[分层更新概述](hierarchical-update.md)   
