---
title: "将数据集和 Tableadapter 分离到不同的项目 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- TableAdapters, n-tier applications
- n-tier applications, separating Datasets and TableAdapters
ms.assetid: f66a3940-6227-46af-a930-9177f425f4fd
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 4ae00a8b3a51b088100d4a27893dd100d5d7ba71
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2017
---
# <a name="separate-datasets-and-tableadapters-into-different-projects"></a>单独的数据集和 tableadapter 分离到不同的项目
类型化数据集已得到增强，以便[Tableadapter](create-and-configure-tableadapters.md)和数据集类可以生成到单独的项目。 这使你可以快速分离各应用程序层及生成 n 层数据应用程序。  
  
下面的过程介绍使用的过程**数据集设计器**以独立于包含生成的 TableAdapter 代码的项目的项目中生成数据集代码。  
  
## <a name="separate-datasets-and-tableadapters"></a>单独的数据集和 Tableadapter  
在将数据集代码分离 TableAdapter 代码中，包含的数据集代码的项目必须位于当前解决方案中。 如果此项目不在当前解决方案中，它将不可用在**数据集项目**列入**属性**窗口。  
  
[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### <a name="to-separate-the-dataset-into-a-different-project"></a>若要将数据集分离到不同的项目  
  
1.  打开包含数据集 （.xsd 文件） 的解决方案。  
  
    > [!NOTE]
    >  如果解决方案不包含想要将数据集代码分离到其中的项目，创建项目，或将现有项目添加到解决方案。  
  
2.  双击一个类型化数据集文件 （.xsd 文件） 中**解决方案资源管理器**以打开中的数据集**数据集设计器**。  
  
3.  选择的空白区域**数据集设计器**。  
  
4.  在**属性**窗口中，找到**数据集项目**节点。  
  
5.  在**数据集项目**列表中，选择你要在其中生成数据集代码项目的名称。  
  
     选择你要在其中生成数据集代码中，的项目后**数据集文件**默认文件名称中填充属性。 如有必要，可以更改此名称。 此外，如果你想要特定目录中生成数据集代码，你可以设置**项目文件夹**到的文件夹名称的属性。  
  
    > [!NOTE]
    >  当你将数据集和 Tableadapter (通过设置**数据集项目**属性)，将不会自动移动项目中的现有数据集分部类。 到数据集项目，必须手动移动现有数据集分部类。  
  
6.  保存的数据集。  
  
     数据集代码生成到中的选定项目**数据集项目**属性，与**TableAdapter**代码生成到当前项目。  
  
默认情况下，分隔的数据集和 TableAdapter 代码后结果将是离散的类文件中的每个项目。 原始项目具有一个文件，其名为 DatasetName.Designer.vb （或 DatasetName.Designer.cs） 包含 TableAdapter 代码。 中指定的项目**数据集项目**属性包含一个名为 DatasetName.DataSet.Designer.vb （或 DatasetName.DataSet.Designer.cs） 包含的数据集代码。  
  
> [!NOTE]
>  若要查看生成的类文件中，选择数据集或 TableAdapter 项目。 然后，在**解决方案资源管理器**，选择**显示所有文件**。  
  
## <a name="see-also"></a>请参阅
[N 层数据应用程序概述](../data-tools/n-tier-data-applications-overview.md)   
[演练： 创建 N 层数据应用程序](../data-tools/walkthrough-creating-an-n-tier-data-application.md)   
[分层更新](../data-tools/hierarchical-update.md)   
[在 Visual Studio 中访问数据](../data-tools/accessing-data-in-visual-studio.md)   
[ADO.NET](/dotnet/framework/data/adonet/index)