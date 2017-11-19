---
title: "创建一个数据库文件并在 Visual Studio 中使用表设计器 |Microsoft 文档"
ms.custom: 
ms.date: 11/03/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- database tables, creating
- database files, creating
- table designer
ms.assetid: 99c2b06f-47aa-414e-8057-a3453712fd23
caps.latest.revision: "49"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 47fad923b0e31d650d18426bf5f9a7da7bca3e38
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2017
---
# <a name="create-a-database-and-add-tables-in-visual-studio"></a>创建数据库并在 Visual Studio 中添加表
可以使用 Visual Studio 创建和更新 SQL Server Express LocalDB 中的本地数据库文件。 你还可以通过执行 TRANSACT-SQL 语句中的创建数据库**SQL Server 对象资源管理器**Visual Studio 中的工具窗口。 在本主题中，我们将创建的.mdf 文件，并使用表设计器中添加表和键。
  
## <a name="prerequisites"></a>先决条件  
若要完成本演练，你必须可选**数据存储和处理**安装在 Visual Studio 中的工作负荷。 若要安装它，打开**Visual Studio Installer**选择**工作负荷**选项卡。下**Web 和云**，选择**数据存储和处理**。 选择**修改**按钮以添加到 Visual Studio 的工作负荷。
  
## <a name="create-a-project-and-a-local-database-file"></a>创建一个项目及本地数据库文件  
  
### <a name="to-create-a-project-and-a-database-file"></a>创建项目和数据库文件  
1.  创建名为 Windows 窗体项目`SampleDatabaseWalkthrough`。  
  
2.  在菜单栏上，选择**项目**，**添加新项**。  
  
3.  在项模板列表中，向下滚动并选择**基于服务的数据库**。  
  
     ![项目模板对话框](../data-tools/media/raddata-vsitemtemplates.png "raddata VSItemTemplates")  
  
4.  将数据库命名**SampleDatabase**，然后选择**添加**按钮。

### <a name="to-add-a-data-source"></a>添加数据源  
5.  如果**数据源**窗口未打开，请打开它选择**Shift + Alt + D**键或在菜单栏中，选择**视图**，**其他窗口**，**数据源**。
  
6.  在**数据源**窗口中，选择**添加新数据源**链接。

    **数据源配置向导**打开。

7. 上**选择数据源类型**页上，选择**数据库**，然后选择**下一步**。

8. 上**选择数据库模型**页上，选择**下一步**以接受默认值 （数据集）。

9. 上**选择你的数据连接**页上，选择**SampleDatabase.mdf**在下拉列表中，文件，然后选择**下一步**。

10. 上**将连接字符串保存到应用程序配置文件**页上，选择**下一步**。

11. 一个**选择数据库对象**页上，你将看到一条消息，指出数据库不包含任何对象。 选择**完成**。

### <a name="to-view-properties-of-the-data-connection"></a>若要查看的数据连接属性
你可以通过打开数据连接属性窗口来查看 SampleDatabase.mdf 文件的连接字符串：
  
-   在 Visual Studio 中，选择**视图**， **SQL Server 对象资源管理器**如果该窗口尚未打开。 打开属性窗口通过展开**数据连接**节点，打开 SampleDatabase.mdf，快捷菜单，然后选中**属性**。  
  
-   或者，你可以选择**视图**，**服务器资源管理器**，如果该窗口尚未打开。 打开属性窗口通过展开**数据连接**节点。 Sampledatabase.mdf，打开快捷菜单，然后选择**属性**。  
  
## <a name="create-tables-and-keys-by-using-table-designer"></a>使用表设计器中创建表和键
在此部分中，你将创建两个表，每个表和几行示例数据中的主键。 你还将创建外键以指定一个表中的记录如何对应于另一个表中的记录。  
  
### <a name="to-create-the-customers-table"></a>创建 Customers 表  
1.  在**服务器资源管理器**或**SQL Server 对象资源管理器**，展开**数据连接**节点，然后展开**SampleDatabase.mdf**节点。  
  
2.  打开的快捷菜单**表**，然后选择**添加新表**。  
  
     **表设计器**将打开并显示一个具有一个默认行，这表示你要创建的表中的单个列的网格。 通过向网格中添加行，即可在表中添加列。  
  
3.  在网格中，为下列各个条目添加行：  
  
    |列名称|数据类型|允许空|  
    |-----------------|---------------|-----------------|  
    |`CustomerID`|`nchar(5)`|False（清除）|  
    |`CompanyName`|`nvarchar(50)`|False（清除）|  
    |`ContactName`|`nvarchar (50)`|True（已选定）|  
    |`Phone`|`nvarchar (24)`|True（已选定）|  
  
4.  打开的快捷菜单`CustomerID`行，，然后选择**设置主键**。  
  
5.  打开默认行的快捷菜单，然后选择**删除**。  
  
6.  通过更新脚本窗格的第一行来命名 Customers 表，与以下示例相匹配：  
  
    ```  
    CREATE TABLE [dbo].[Customers]  
    ```  
  
    将显示如下所示的内容：  
  
    ![表设计器](../data-tools/media/raddata-table-designer.png "raddata 表设计器")  
  
7.  在左上角的**表设计器**，选择**更新**按钮。  
  
8.  在**预览数据库更新**对话框中，选择**更新数据库**按钮。  
  
    你所做的更改将保存到本地数据库文件中。  
  
### <a name="to-create-the-orders-table"></a>创建 Orders 表  
1.  添加另一个表，然后在下表中为每个条目添加行：  
  
    |列名称|数据类型|允许空|  
    |-----------------|---------------|-----------------|  
    |`OrderID`|`int`|False（清除）|  
    |`CustomerID`|`nchar(5)`|False（清除）|  
    |`OrderDate`|`datetime`|True（已选定）|  
    |`OrderQuantity`|`int`|True（已选定）|  
  
2.  设置**OrderID**为主键，以及然后删除默认行。  
  
3.  通过更新脚本窗格的第一行来命名 Orders 表，与以下示例相匹配：  
  
    ```sql  
    CREATE TABLE [dbo].[Orders]  
    ```  
  
4.  在左上角的**表设计器**，选择**更新**按钮。  
  
5.  在**预览数据库更新**对话框中，选择**更新数据库**按钮。  
  
    你所做的更改将保存到本地数据库文件中。  
  
### <a name="to-create-a-foreign-key"></a>创建外键  
1.  在网格右侧的上下文窗格中，打开快捷菜单**外键**，然后选择**添加新外键**，如下图所示。  
  
     ![表设计器中添加外键](../data-tools/media/foreignkey.png "ForeignKey")  
  
2.  在文本框中显示，替换**ToTable**与`Customers`。  
  
3.  在 T-SQL 的窗格中，更新以下示例相匹配的最后一行：  
  
    ```sql  
    CONSTRAINT [FK_Orders_Customers] FOREIGN KEY ([CustomerID]) REFERENCES [Customers]([CustomerID])  
    ```  
  
4.  在左上角的**表设计器**，选择**更新**按钮。  
  
5.  在**预览数据库更新**对话框中，选择**更新数据库**按钮。  
  
    你所做的更改将保存到本地数据库文件中。  
  
## <a name="populate-the-tables-with-data"></a>使用数据填充表  
  
### <a name="to-populate-the-tables-with-data"></a>将数据填入表中  
  
1.  在**服务器资源管理器**或**SQL Server 对象资源管理器**，展开示例数据库的节点。  
  
2.  打开的快捷菜单**表**节点中，选择**刷新**，然后展开**表**节点。  
  
3.  打开客户表的快捷菜单，然后选择**显示表数据**。  
  
4.  添加所需的某些客户的数据。  
  
    你可以指定任意五个字符作为客户 ID，但至少选择一个能记住的以便稍后在此过程中使用。  
  
5.  打开订单表的快捷菜单，然后选择**显示表数据**。  
  
6.  添加的某些订单的数据。  
  
    > [!IMPORTANT]
    > 请确保所有订单 Id 和订单数量都是整数，并且每个客户 ID 匹配的客户表的 CustomerID 列中指定一个值。  
  
7.  在菜单栏上，选择**文件**，**保存所有**。
  
## <a name="see-also"></a>请参阅
[在 Visual Studio 中访问数据](accessing-data-in-visual-studio.md)