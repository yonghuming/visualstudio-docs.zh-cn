---
title: "DataRelation 用于创建数据集之间的关系 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vbData.Microsoft.VSDesigner.DataSource.DesignRelation
- vbdata.Microsoft.VSDesigner.DataSource.DesignRelation
helpviewer_keywords:
- relationships, about relationships
- datasets [Visual Basic], relationships
- relationships, datasets
ms.assetid: cfe274f0-71fe-40f6-994e-7c7f6273c9ba
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: bfc537118f6c1769ec98893099daa0c61d1b5b1d
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2017
---
# <a name="create-relationships-between-datasets"></a>创建数据集之间的关系
包含相关的数据的数据集表，表使用<xref:System.Data.DataRelation>对象来表示表之间的父/子关系，并从另一个返回相关的记录。 通过使用添加到数据集的相关的表**数据源配置向导**，或**数据集设计器**、 创建和配置<xref:System.Data.DataRelation>为你的对象。  
  
<xref:System.Data.DataRelation>对象执行两个函数：  
  
-   它可以提供与你正在使用的记录相关的记录。 如果你正在处理父记录提供子记录 (<xref:System.Data.DataRow.GetChildRows%2A>)，而是如果你正在使用子记录的父记录 (<xref:System.Data.DataRow.GetParentRow%2A>)。  
  
-   它可强制引用完整性，例如当删除父记录中删除相关的子记录的约束。  
  
务必了解真正的联接和的函数之间的差异<xref:System.Data.DataRelation>对象。 在真正的联接，记录是来自父表和子表，并将放入单个的平面记录集。 当你使用<xref:System.Data.DataRelation>对象，创建任何新的记录集。 相反，DataRelation 跟踪表之间的关系，并且将父和子记录保持同步。  
  
## <a name="datarelation-objects-and-constraints"></a>DataRelation 对象和约束  
A<xref:System.Data.DataRelation>对象还用于创建和实施以下约束：  
  
-   唯一约束，这可确保表中的列包含没有重复项。  
  
-   外键约束，用于维护数据集中的父和子表之间的引用完整性。  
  
在指定的约束<xref:System.Data.DataRelation>对象实现通过自动创建相应的对象或设置属性。 如果你通过使用创建外键约束<xref:System.Data.DataRelation>对象、 的实例<xref:System.Data.ForeignKeyConstraint>类添加到<xref:System.Data.DataRelation>对象的<xref:System.Data.DataRelation.ChildKeyConstraint%2A>属性。  
  
唯一约束实现通过只需设置<xref:System.Data.DataColumn.Unique%2A>到数据列属性`true`或通过将实例添加<xref:System.Data.UniqueConstraint>类到<xref:System.Data.DataRelation>对象的<xref:System.Data.DataRelation.ParentKeyConstraint%2A>属性。 有关挂起数据集中的约束的信息，请参阅[填充数据集时关闭约束](../data-tools/turn-off-constraints-while-filling-a-dataset.md)。  
  
### <a name="referential-integrity-rules"></a>引用完整性规则  
作为外键约束的一部分，你可以指定在三个点应用的引用完整性规则：  
  
-   何时更新父记录  
  
-   当删除父记录  
  
-   接受或拒绝更改时  
  
中指定的规则，你可以<xref:System.Data.Rule>枚举并列出下表中。  
  
|外键约束规则|操作|  
|----------------------------------|------------|  
|<xref:System.Data.Rule.Cascade>|中子表中的相关记录还进行对父记录所做的更改 （update 或 delete）。|  
|<xref:System.Data.Rule.SetNull>|子记录不会删除，但这些子记录中的外键设置为<xref:System.DBNull>。 使用此设置时，子记录可以保留为"孤立项"-这就是，它们具有的父记录没有关系。 **注意：**使用此规则可能导致子表中的无效数据。|  
|<xref:System.Data.Rule.SetDefault>|中的相关的子记录的外键设置为其默认值 (由列的建立<xref:System.Data.DataColumn.DefaultValue%2A>属性)。|  
|<xref:System.Data.Rule.None>|对相关的子记录不进行任何更改。 使用此设置时，子记录可以包含对无效的父记录的引用。|  
  
有关数据集表中的更新的详细信息，请参阅[将数据保存回数据库](../data-tools/save-data-back-to-the-database.md)。  
  
### <a name="constraint-only-relations"></a>仅限约束的关系  
当你创建<xref:System.Data.DataRelation>对象，你必须指定，该关系仅可用于强制执行约束的选项-即，它将不还用于访问相关的记录。 此选项可用于生成的数据集，这是效率稍有提高，并包含较少方法比具有相关记录功能。 但是，你将无法访问相关的记录。 例如，仅限约束的关系会导致删除仍然具有子记录的父记录，并且不能通过父访问子记录。  
  
## <a name="manually-creating-a-data-relation-in-the-dataset-designer"></a>手动创建数据集设计器中的数据关系  
当通过使用 Visual Studio 中的数据设计工具创建数据表时，当可以从你的数据源收集的信息的关系会自动创建。 如果你手动添加从数据表**数据集**选项卡**工具箱**，可能需要手动创建关系。 有关创建信息<xref:System.Data.DataRelation>对象以编程方式，请参阅[添加 Datarelation](/dotnet/framework/data/adonet/dataset-datatable-dataview/adding-datarelations)。  
  
数据表之间的关系显示为线在**数据集设计器**，并具有键和无穷标志符号的关系的一到多方面进行描述。 默认情况下，关系的名称不会不显示在设计图面上。  
  
[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### <a name="to-create-a-relationship-between-two-data-tables"></a>若要创建的两个数据表之间的关系  
  
1.  打开中的数据集**数据集设计器**。 有关详细信息，请参阅[演练： 创建数据集设计器中的数据集](walkthrough-creating-a-dataset-with-the-dataset-designer.md)。  
  
2.  拖动**关系**对象**数据集**工具箱拖放到关系中的子数据表。  
  
     **关系**对话框随即打开，填充**子表**包装盒拖表**关系**拖到对象。  
  
3.  选择从父表**父表**框。 父表包含一个对多关系的"一"方上的记录。  
  
4.  验证正确的子表是否显示在**子表**框。 子表包含一个对多关系"多"方上的记录。  
  
5.  键入的名称之间的关系**名称**框中，或保留默认名称基于所选表。 这是实际名称<xref:System.Data.DataRelation>在代码中的对象。  
  
6.  选择联接中的表的列**键列**和**外键列**列出。  
  
7.  选择是否创建某一关系、 约束，或两者。   
  
8.  选中或清除**嵌套关系**框。 选择此选项设置<xref:System.Data.DataRelation.Nested%2A>属性`true`，这将导致子行嵌套在父列中，当以 XML 数据形式编写或与同步这些行的关系<xref:System.Xml.XmlDataDocument>。 有关详细信息，请参阅[嵌套 Datarelation](/dotnet/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations)。  
  
9. 设置你正在对这些表中的记录进行更改时要执行的规则。 有关更多信息，请参见<xref:System.Data.Rule>。  
  
10. 单击**确定**来创建关系。 在两个表之间的设计器上显示一关系线。  
  
#### <a name="to-display-a-relation-name-in-the-dataset-designer"></a>若要在数据集设计器中显示的关系名称  
  
1.  打开中的数据集**数据集设计器**。 有关详细信息，请参阅[演练： 创建数据集设计器中的数据集](walkthrough-creating-a-dataset-with-the-dataset-designer.md)。  
  
2.  从**数据**菜单上，选择**显示关系标签**命令以显示关系名称。 清除该命令，以隐藏的关系名称。

## <a name="see-also"></a>请参阅
[在 Visual Studio 中创建和配置数据集](../data-tools/create-and-configure-datasets-in-visual-studio.md)