---
title: "Visual Studio 中的数据集工具 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.data.DataSet
helpviewer_keywords:
- untyped datasets
- datasets [Visual Basic], extended properties
- typed datasets
- current record in dataset
- XML [Visual Basic], datasets
- DataSet class, about datasets
- unique constraints (datasets)
- data relationships
- parent records in datasets
- extended properties, in typed datasets
- datasets [Visual Basic]
- schemas [Visual Basic], datasets
- datasets [Visual Basic], msprop
- master-detail tables, datasets
- databases [Visual Basic], updating
- msprop
- foreign keys, datasets
- DataSet class
- datasets [Visual Basic], filling
- case sensitivity, datasets
- constraints [Visual Basic], datasets
- child records
- related tables, datasets
- updating datasets, about dataset updates
- data caching, datasets
- DataRelation object, datasets
- untyped datasets, compared to typed datasets
- cache [Visual Studio], datasets
- datasets [Visual Basic], relationships
- related tables
- XML schemas, about XML schemas and datasets
- relationships, datasets
- typed datasets, compared to untyped datasets
- datasets [Visual Basic], populating
- datasets [Visual Basic], namespace
- data adapters, populating datasets
ms.assetid: ee57f4f6-9fe1-4e0a-be9a-955c486ff427
caps.latest.revision: "49"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 6a7e5741b11263ef3c3730ddaa69e566cd7c2e24
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="dataset-tools-in-visual-studio"></a>Visual Studio 中的数据集工具
> [!NOTE]
>  数据集和相关的类是从年初使应用程序能够使用内存中数据的同时从数据库断开连接的应用程序的旧.NET 技术。 它们是特别有用的应用程序使用户能够修改数据并将更改应用回数据库。 虽然数据集已证明是非常成功的技术，我们建议新的.NET 应用程序使用实体框架。 实体框架提供更自然的方式来使用表格数据作为对象模型，它具有一个更简单的编程接口。  
  
 数据集对象是一个内存中对象，它实质上是最小化的数据库。 它包含 DataTable、 DataColumn 和 DataRow 对象可以在其中存储并修改一个或多个数据库中的数据，而无需维护的开放连接。 数据集维护对其数据进行的更改的信息，因此可以跟踪更新和应用程序变得重新连接时发送回数据库。  
  
 数据集和相关的类中的.NET Framework 类库的 System.Data 命名空间中定义。 你可以创建和修改在代码中动态的数据集。 有关如何执行该操作的详细信息，请参阅 ADO.NET。 此部分中的文档演示如何通过使用 Visual Studio 设计器处理数据集。 要了解的一件事： 都通过设计器的数据集使用 TableAdapter 对象进行交互与数据库，而以编程方式进行的数据集使用 DataAdapter 对象。 有关以编程方式创建数据集的信息，请参阅[Dataadapter 和 Datareader](/dotnet/framework/data/adonet/dataadapters-and-datareaders)。  
  
 如果你的应用程序需要仅从数据库读取数据并不执行更新、 将添加时，或删除，你通常可以通过使用 DataReader 对象的数据检索到的泛型列表对象或另一个集合对象中获取更好的性能。 如果显示的数据，你可以数据的用户界面将与绑定集合。  
  
## <a name="dataset-workflow"></a>数据集工作流  
 Visual Studio 提供了大量的工具来简化数据集的处理。 基本的端到端工作流是：  
  
-   使用**数据源**窗口从一个或多个数据源创建新的数据集。 使用**数据集设计器**配置数据集并设置其属性。 例如，你需要指定哪些表从数据源，若要包含，和每个表中的哪些列。 请仔细选择，以节省的数据集将需要的内存量。 有关详细信息，请参阅[创建和配置数据集](../data-tools/create-and-configure-datasets-in-visual-studio.md)。  
  
-   指定表之间的关系，以便正确处理外键。 有关详细信息，请参阅[填充数据集使用 Tableadapter](../data-tools/fill-datasets-by-using-tableadapters.md)。  
  
-   使用**TableAdapter 配置向导**以指定的查询或存储的过程，将填充数据集，以及若要实现哪些数据库操作 （update、 delete 和等等）。 有关详细信息，请参阅以下主题：  
  
    -   [使用 Tableadapter 填充数据集](../data-tools/fill-datasets-by-using-tableadapters.md)  
  
    -   [编辑数据集中的数据](../data-tools/edit-data-in-datasets.md)  
  
    -   [验证数据集中的数据](../data-tools/validate-data-in-datasets.md)  
  
    -   [将数据保存回数据库](../data-tools/save-data-back-to-the-database.md)  
  
-   查询和数据集中搜索的数据。 有关详细信息，请参阅[查询数据集](../data-tools/query-datasets.md)。 [!INCLUDE[linq_dataset](../data-tools/includes/linq_dataset_md.md)]使[LINQ （语言集成查询）](http://msdn.microsoft.com/Library/a73c4aec-5d15-4e98-b962-1274021ea93d)中的数据<xref:System.Data.DataSet>对象。 有关详细信息，请参阅 [LINQ to DataSet](/dotnet/framework/data/adonet/linq-to-dataset)。  
  
-   使用**数据源**窗口以将用户界面控件绑定到数据集或其各个列，并指定哪些列是用户可编辑。 有关详细信息，请参阅[将控件绑定到 Visual Studio 中的数据](../data-tools/bind-controls-to-data-in-visual-studio.md)。  
  
## <a name="datasets-and-n-tier-architecture"></a>数据集和 N 层体系结构  
 关于 N 层应用程序中的数据集的信息，请参阅[处理 n 层应用程序中的数据集](../data-tools/work-with-datasets-in-n-tier-applications.md)。  
  
## <a name="datasets-and-xml"></a>数据集和 XML  
 有关从 XML 进行来回转换数据集的信息，请参阅[读取 XML 数据读入数据集](../data-tools/read-xml-data-into-a-dataset.md)和[将数据集另存为 XML](../data-tools/save-a-dataset-as-xml.md)。  
  
## <a name="see-also"></a>另请参阅  
 [适用于 NET 的 Visual Studio Data Tools](../data-tools/visual-studio-data-tools-for-dotnet.md)