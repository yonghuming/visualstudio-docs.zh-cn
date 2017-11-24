---
title: "创建和配置 Visual Studio 中的数据集 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- typed datasets, creating
- datasets, creating
- datasets, configuring
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: f48371e17830b2cf31ff81708a72ba9d95f9a7c5
ms.sourcegitcommit: eb954434c34b4df6fd2264266381b23ce9e6204a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2017
---
# <a name="create-and-configure-datasets-in-visual-studio"></a>创建和配置 Visual Studio 中的数据集

A*数据集*是一组在内存中存储数据库中的数据和支持更改跟踪来启用的对象的创建、 读取、 更新和删除 (CRUD) 操作对这些数据而无需必须始终连接到数据库。 数据集为简单设计*对数据的窗体*业务应用程序。 新应用程序，请考虑使用实体框架来存储和内存中的数据创建模型。 若要使用数据集，你应具有数据库概念基本知识。

创建类型化<xref:System.Data.DataSet>在设计时通过使用 Visual Studio 中的类**数据源配置向导**。 有关以编程方式创建数据集的信息，请参阅[创建数据集 (ADO.NET)](/dotnet/framework/data/adonet/dataset-datatable-dataview/creating-a-dataset)。

## <a name="create-a-new-dataset-by-using-the-data-source-configuration-wizard"></a>通过使用数据源配置向导创建新的数据集

1.  上**项目**菜单上，单击**添加新数据源**启动**数据源配置向导**。

2.  选择你将连接到的数据源的类型。

     ![数据源配置向导](../data-tools/media/data-source-configuration-wizard.png "数据源配置向导")

3.  对于数据库，选择将你的数据集的数据源的数据库。

     ![数据源选择的连接](../data-tools/media/data-source-choose-a-connection.png "数据源选择的连接")

4.  选择的表 （或单独的列），存储过程、 函数和从你想要在数据集中表示数据库的视图。

     ![选择数据库对象](../data-tools/media/raddata-chose-objects.png "raddata 选择对象")

5.  单击 **“完成”**。

6.  数据集显示为中的一个节点**解决方案资源管理器**:

     ![在解决方案资源管理器中的数据集](../data-tools/media/dataset-in-solution-explorer.png "解决方案资源管理器中的数据集")

     单击该节点，然后在显示该数据集**数据集设计器**。 请注意，在数据集中每个表有一个关联的 TableAdapter 对象，它表示在底部。 表适配器用于填充数据集并 （可选） 将命令发送到数据库。

     ![数据集设计器](../data-tools/media/dataset-designer.png "数据集设计器")

7.  连接表的关系行表示表的关系，在数据库中定义。 默认情况下，在数据库中的外键约束表示只，作为关系与更新和删除规则设置为 none。 通常情况下，这是你想得到。 不过，您可以单击要显示的行**关系**对话框中，你可以在其中更改分层更新的行为。 有关详细信息，请参阅[数据集中的关系](../data-tools/relationships-in-datasets.md)和[分层更新](../data-tools/hierarchical-update.md)。

     ![数据集关系对话框](../data-tools/media/raddata-relation-dialog.png "raddata 关系对话框")

8.  单击表、 表适配器或在表中的列名称以查看其属性在**属性**窗口。 你可以修改某些此处的值。 只需记住您正在修改数据集，不是源数据库。

     ![数据集列属性](../data-tools/media/dataset-column-properties.png "数据集列属性")

9. 你可以将新表或表适配器添加到数据集，或添加新的查询，对应于现有表适配器，或指定新的关系，通过将这些项从表之间**工具箱**选项卡。时，此选项卡会出现**数据集设计器**处于活动状态。

     ![数据集工具箱](../data-tools/media/raddata-dataset-toolbox.png "raddata 数据集工具箱")

10. 接下来，你可能想要指定如何填充数据集的数据。 为此，你使用**TableAdapter 配置向导**。 有关详细信息，请参阅[填充数据集使用 Tableadapter](../data-tools/fill-datasets-by-using-tableadapters.md)。

## <a name="add-a-database-table-or-other-object-to-an-existing-dataset"></a>将数据库表或其他对象添加到现有数据集

此过程演示如何从同一个数据库用于首次创建数据集添加一个表。

1.  单击中的数据集节点**解决方案资源管理器**将数据集设计器引入焦点。

2.  单击**数据源**Visual Studio 中，左边距中的选项卡上，或输入`Data Sources`中**快速启动**。

3.  右键单击数据集节点并选择**使用向导配置数据源**。

     ![数据源上下文菜单](../data-tools/media/data-source-context-menu.png "数据源上下文菜单")

4.  使用向导来指定哪些其他的表，或存储的过程或其他数据库对象，将添加到数据集。

## <a name="add-a-stand-alone-data-table-to-a-dataset"></a>将独立的数据表添加到数据集

1.  打开中的数据集**数据集设计器**。

2.  拖动<xref:System.Data.DataTable>类**数据集**选项卡**工具箱**到**数据集设计器**。

3.  添加列来定义您数据的表。 右键单击该表，然后选择**添加 > 列**。 使用**属性**窗口设置列和键的数据类型，如有必要。

4.  独立表需要实现`Fill`独立的表中的逻辑，以便你可以用数据填充它们。 有关填充独立数据表的信息，请参阅[填充数据集从 DataAdapter](/dotnet/framework/data/adonet/populating-a-dataset-from-a-dataadapter)。

## <a name="see-also"></a>请参阅

[Visual Studio 中的数据集工具](../data-tools/dataset-tools-in-visual-studio.md)