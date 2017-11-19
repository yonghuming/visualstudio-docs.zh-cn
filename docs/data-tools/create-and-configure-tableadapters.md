---
title: "创建和配置 Tableadapter |Microsoft 文档"
ms.custom: 
ms.date: 09/01/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- table adapters, creating
- creating TableAdapters
- data [Visual Studio], creating data components
- data [Visual Studio], TableAdapters
- data [Visual Studio], creating table adapters
ms.assetid: 08630d69-0d6c-4e8f-b42d-2922f45f8415
caps.latest.revision: "28"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 11086ba17f3f2fb7af99d76b3efadece4a23c426
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2017
---
# <a name="create-and-configure-tableadapters"></a>创建和配置 Tableadapter
Tableadapter 提供你的应用程序和数据库之间的通信。 它们连接到数据库、 运行的查询或存储的过程，并返回新的数据的表或填充现有<xref:System.Data.DataTable>与返回的数据。 Tableadapter 还可以从回数据库应用程序发送更新的数据。  
  
当你执行以下操作之一时，会为您创建 Tableadapter:  
  
-   运行[数据源配置向导](../data-tools/media/data-source-configuration-wizard.png)，然后选择**数据库**或**Web 服务**数据源类型。  
  
-   将数据库对象从**服务器资源管理器**到**数据集设计器**。  
  
你还可以创建新的 TableAdapter，并将其与数据源配置通过将 TableAdapter 从工具箱拖到空区域**数据集设计器**面。  
  
Tableadapter 的简介，请参阅[填充数据集使用 Tableadapter](../data-tools/fill-datasets-by-using-tableadapters.md)。  
  
[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## <a name="use-the-tableadapter-configuration-wizard"></a>使用 TableAdapter 配置向导  
运行**TableAdapter 配置向导**若要创建或编辑 Tableadapter 及其关联的 Datatable。 你可以通过右键单击该中配置现有 TableAdapter**数据集设计器**。  
  
![raddata 表适配器配置向导](../data-tools/media/raddata-table-adapter-configuration-wizard.png "raddata 表适配器配置向导")  
  
如果从工具箱中将新的 TableAdapter 时**数据集设计器**是否处于专注，向导将启动并提示你指定的数据源 TableAdapter 应连接到。 在下一页上，向导会要求它应使用哪种类型的命令与 SQL 语句或存储的过程中的数据库进行通信。 （你看不到此如果你要配置已与数据源关联的 TableAdapter。）  
  
-   你可以选择在基础数据库中创建新的存储的过程，如果你有用于数据库的正确权限。 如果你没有这些权限，这不会作为一个选项。  
  
-   你还可以选择运行的现有存储的过程**选择**，**插入**，**更新**，和**删除**的命令TableAdapter。 分配给存储的过程**更新**命令，例如，运行时`TableAdapter.Update()`调用方法。  
  
将参数从选中的存储过程映射到数据表中相应的列。 例如，如果你的存储的过程接受一个名为参数`@CompanyName`它传递给`CompanyName`在表中，列集**源列**的`@CompanyName`参数`CompanyName`。  
  
> [!NOTE]
>  通过调用 TableAdapter 的方法将在向导的下一步是运行分配给 SELECT 命令的存储的过程。 默认方法是`Fill`，因此通常用于运行 SELECT 过程的代码是`TableAdapter.Fill(tableName)`。 如果更改默认名称从`Fill`，替换`Fill`同名你分配，并将"TableAdapter"替换为 TableAdapter 的实际名称 (例如， `CustomersTableAdapter`)。  
  
-   选择**创建方法来直接向数据库发送更新**选项等同于设置`GenerateDBDirectMethods`属性为 true。 如果原始的 SQL 语句未提供足够的信息或查询不是一个可更新查询，选项将不可用。 这种情况下可以发生，例如，在**加入**查询和返回单个 （标量） 值的查询。  
  
**高级选项**向导中，您可以：  
- 生成基于定义的 SELECT 语句的 INSERT、 UPDATE 和 DELETE 语句**生成 SQL 语句**页
- 使用开放式并发
- 指定是否在插入后刷新的数据表并运行更新语句  
  
## <a name="configure-a-tableadapters-fill-method"></a>配置 TableAdapter 的填充方法  
有时你可能想要更改 TableAdapter 的表的架构。 若要执行此操作，可修改 TableAdapter 的主`Fill`方法。 Tableadapter 创建是主要`Fill`定义关联的数据的表的架构的方法。 主`Fill`方法基于的查询或在最初配置 TableAdapter 时输入的存储的过程。 它是在数据集设计器中的数据表的第一个 （顶端） 方法。  
  
![使用多个查询的 TableAdapter](../data-tools/media/tableadapter.gif "TableAdapter")  
  
向 TableAdapter 做的任何更改的主`Fill`方法将反映在关联的数据的表的架构。 例如，从当中，该查询中删除列`Fill`方法还从关联的数据表中删除列。 此外，从 main 删除列`Fill`方法删除列从任何其他查询该 TableAdapter。  
  
TableAdapter 查询配置向导可用于创建和编辑其他查询的 TableAdapter。 这些其他的查询必须符合表架构中，除非它们返回一个标量值。  每个其他查询具有你指定的名称。  
 
下面的示例演示如何调用名为一个额外查询`FillByCity`:  
 
`CustomersTableAdapter.FillByCity(NorthwindDataSet.Customers, "Seattle")`  
  
#### <a name="to-start-the-tableadapter-query-configuration-wizard-with-a-new-query"></a>若要使用新查询启动 TableAdapter 查询配置向导  
  
1.  打开中的数据集**数据集设计器**。  
  
2.  如果要创建新查询，则拖动窗口**查询**对象**数据集**选项卡**工具箱**到<xref:System.Data.DataTable>，或选择**添加查询**从 TableAdapter 的快捷菜单。 您还可以拖动**查询**对象拖放到的空白区域**数据集设计器**，这将创建不关联的情况下 TableAdapter <xref:System.Data.DataTable>。 这些查询可以仅返回单个 （标量） 值或运行的插入、 更新或删除对数据库的命令。  
  
3.  上**选择你的数据连接**屏幕上，选择或创建的连接，该查询将使用。  
  
    > [!NOTE]
    >  当在设计器无法确定正确的连接，若要使用，或任何连接不不可用时，才会显示此屏幕。  
  
4.  上**选择命令类型**屏幕上，选择以下从数据库提取数据的方法：  
  
    -   **使用 SQL 语句**使您能够键入 SQL 语句以从您的数据库选择的数据。  
  
    -   **创建新的存储的过程**允许您让向导创建新存储过程 （在数据库中） 基于指定的 SELECT 语句。  
  
    -   **使用现有存储的过程**，你可以运行查询时运行现有的存储的过程。  
  
#### <a name="to-start-the-tableadapter-query-configuration-wizard-on-an-existing-query"></a>要启动 TableAdapter 查询配置向导在现有的查询  
  
-   如果你正在编辑现有 TableAdapter 查询，右键单击查询，并选择**配置**从快捷菜单。  
  
    > [!NOTE]
    >  右键单击 TableAdapter 的主查询重新配置 TableAdapter 和<xref:System.Data.DataTable>架构。 右键单击 TableAdapter 上的一个额外查询，但是，配置所选的查询。 **TableAdapter 配置向导**TableAdapter 查询配置向导重新配置所选的查询时将 TableAdapter 定义中，重新配置。  
  
#### <a name="to-add-a-global--query-to-a-tableadapter"></a>若要向 TableAdapter 添加全局查询  
  
-   *全局查询*是返回单个 （标量） 值或空值的 SQL 查询。 通常情况下，全局函数执行数据库操作，例如插入、 更新，删除。 它们还聚合信息，如表或特定的顺序中的所有项的总费用中的客户的计数。  
  
     通过拖动添加全局查询**查询**对象**数据集**选项卡**工具箱**到的空白区域**数据集设计器**.  
  
-   提供执行所需的任务，例如，查询`SELECT COUNT(*) AS CustomerCount FROM Customers`。  
  
    > [!NOTE]
    >  拖动**查询**对象直接拖动到**数据集设计器**创建返回标量 （单个） 值的方法。 虽然查询或你选择的存储的过程可能会返回多个单个值，它由向导创建的方法仅返回单个值。 例如，查询可能返回返回的数据的第一行的第一列。

## <a name="see-also"></a>请参阅
[使用 Tableadapter 填充数据集](../data-tools/fill-datasets-by-using-tableadapters.md)