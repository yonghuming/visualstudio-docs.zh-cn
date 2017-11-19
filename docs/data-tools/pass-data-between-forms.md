---
title: "窗体之间传递数据 |Microsoft 文档"
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
- walkthroughs [Windows Forms], data
- walkthroughs [Visual Studio], data
- data [Visual Studio], passing between forms
- forms, passing data between
- Windows Forms, walkthroughs
ms.assetid: 78bf038b-9296-4fbf-b0e8-d881d1aff0df
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: f401224657e64922fc9f6102a33eaf1cf824a556
ms.sourcegitcommit: ec1c7e7e3349d2f3a4dc027e7cfca840c029367d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/07/2017
---
# <a name="pass-data-between-forms"></a>窗体之间传递数据
本演练提供了有关将数据从一个窗体传递到另一个窗体的分步说明。 使用客户和订单表，从 Northwind，一种形式允许用户选择一个客户，并第二种形式显示所选的客户的订单。 本演练演示如何从第一个窗体接收数据的第二个窗体上创建的方法。  
  
> [!NOTE]
>  本演练仅演示在窗体之间传递数据的一种方法。 用于将数据传递到窗体中，包括创建另一个构造函数来接收数据，其他选项，或创建的公共属性，可以进行设置的数据的第一个表单。  
  
 本演练涉及以下任务：  
  
-   创建一个新**Windows 窗体应用程序**项目。  
  
-   创建和配置具有的数据集[数据源配置向导](../data-tools/media/data-source-configuration-wizard.png)。  
  
-   选择要拖动中的项时要创建窗体上的控件**数据源**窗口。 有关详细信息，请参阅[设置从数据源窗口拖动时创建的控件](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)。  
  
-   通过将某些项从创建数据绑定控件**数据源**拖到窗体的窗口。  
  
-   创建具有网格的第二个窗体来显示数据。  
  
-   创建一个 TableAdapter 查询来获取特定客户的订单。  
  
-   在窗体间传递数据。  
  
## <a name="prerequisites"></a>先决条件  
本演练使用 SQL Server Express LocalDB 和 Northwind 示例数据库。  
  
1.  如果你没有 SQL Server Express LocalDB，将其安装从[SQL Server 版本的下载页](https://www.microsoft.com/en-us/server-cloud/Products/sql-server-editions/sql-server-express.aspx)，或通过**Visual Studio Installer**。 在 Visual Studio 安装程序中，SQL Server Express LocalDB 可以安装的一部分**数据存储和处理**工作负荷，也可以作为单个组件。  
  
2.  按照这些步骤来安装 Northwind 示例数据库：  

    1. 在 Visual Studio 中，打开**SQL Server 对象资源管理器**窗口。 (SQL Server 对象资源管理器安装的一部分**数据存储和处理**在 Visual Studio 安装程序中的工作负荷。)展开**SQL Server**节点。 LocalDB 实例上右键单击并选择**新查询...**.  

       查询编辑器窗口将打开。  

    2. 复制[Northwind TRANSACT-SQL 脚本](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true)到剪贴板。 此 T-SQL 脚本从头创建 Northwind 数据库，并使用数据填充它。  

    3. 将 T-SQL 脚本粘贴到查询编辑器中，，然后选择**执行**按钮。  

       短时间内之后, 执行完查询和创建 Northwind 数据库。  
  
## <a name="create-the-windows-forms-application"></a>创建 Windows 窗体应用程序  
  
#### <a name="to-create-the-new-windows-project"></a>创建新的 Windows 项目  
  
1. 在 Visual Studio 中，在**文件**菜单上，选择**新建**，**项目...**.  
  
2. 展开**Visual C#**或**Visual Basic**在左侧窗格中，然后选择**Windows 经典桌面**。  

3. 在中间窗格中，选择**Windows 窗体应用程序**项目类型。  

4. 将项目**PassingDataBetweenForms**，然后选择**确定**。 
  
     **PassingDataBetweenForms**项目时创建，并添加到**解决方案资源管理器**。  
  
## <a name="create-the-data-source"></a>创建数据源  
  
#### <a name="to-create-the-data-source"></a>创建数据源  
  
1.  在 **“数据”** 菜单上，单击 **“显示数据源”**。  
  
2.  在**数据源**窗口中，选择**添加新数据源**启动**数据源配置**向导。  
  
3.  在 **“选择数据源类型”** 页上选择 **“数据库”** ，然后单击 **“下一步”**。  
  
4.  上**选择数据库模型**页上，确认**数据集**指定，并依次**下一步**。  
  
5.  上**选择你的数据连接**页上，执行下列操作之一：  
  
    -   如果下拉列表中包含到 Northwind 示例数据库的数据连接，请选择该连接。  
  
    -   选择**新连接**以启动**添加/修改连接**对话框。  
  
6.  如果你的数据库需要密码，并启用该选项以包括敏感数据，选择的选项，然后单击**下一步**。  
  
7.  上**将连接字符串保存到应用程序配置文件**页上，单击**下一步**。  
  
8.  上**选择数据库对象**页上，展开**表**节点。  
  
9. 选择**客户**和**订单**表，，然后单击**完成**。  
  
     **NorthwindDataSet**添加到你的项目，与**客户**和**订单**表将显示在**数据源**窗口。  
  
## <a name="create-the-first-form-form1"></a>创建第一个窗体 (Form1)  
 你可以创建数据绑定网格 (<xref:System.Windows.Forms.DataGridView>控件)，通过拖动**客户**节点从**数据源**拖到窗体的窗口。  
  
#### <a name="to-create-a-data-bound-grid-on-the-form"></a>在窗体上创建数据绑定网格  
  
-   将主**客户**节点从**数据源**窗口拖到**Form1**。  
  
     A<xref:System.Windows.Forms.DataGridView>和一个工具条 (<xref:System.Windows.Forms.BindingNavigator>) 上出现用于导航记录**Form1**。 A [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md)，CustomersTableAdapter， <xref:System.Windows.Forms.BindingSource>，和<xref:System.Windows.Forms.BindingNavigator>组件栏中出现。  
  
## <a name="create-the-second-form-form2"></a>创建第二个窗体 (Form2)  
  
#### <a name="to-create-a-second-form-to-pass-the-data-to"></a>创建要传入数据的第二个窗体  
  
1.  从“项目”菜单中，选择“添加 Windows 窗体”。  
  
2.  保留默认名称的**Form2**，然后单击**添加**。  
  
3.  将主**订单**节点从**数据源**窗口拖到**Form2**。  
  
     A<xref:System.Windows.Forms.DataGridView>和一个工具条 (<xref:System.Windows.Forms.BindingNavigator>) 上出现用于导航记录**Form2**。 A [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md)，CustomersTableAdapter， <xref:System.Windows.Forms.BindingSource>，和<xref:System.Windows.Forms.BindingNavigator>组件栏中出现。  
  
4.  删除**OrdersBindingNavigator**从组件栏。  
  
     **OrdersBindingNavigator**从消失**Form2**。  
  
## <a name="add-a-tableadapter-query-to-form2-to-load-orders-for-the-selected-customer-on-form1"></a>向 Form2 加载 Form1 上所选客户的订单添加 TableAdapter 查询  
  
#### <a name="to-create-a-tableadapter-query"></a>若要创建 TableAdapter 查询  
  
1.  双击**NorthwindDataSet.xsd**文件中**解决方案资源管理器**。  
  
2.  右键单击**OrdersTableAdapter**，然后选择**添加查询**。  
  
3.  保留默认选项**使用 SQL 语句**，然后单击**下一步**。  
  
4.  保留默认选项**返回行的选择**，然后单击**下一步**。  
  
5.  将 WHERE 子句添加到查询，返回`Orders`基于`CustomerID`。 查询应当类似于：  
  
    ```  
    SELECT OrderID, CustomerID, EmployeeID, OrderDate, RequiredDate, ShippedDate, ShipVia, Freight, ShipName, ShipAddress, ShipCity, ShipRegion, ShipPostalCode, ShipCountry  
    FROM Orders   
    WHERE CustomerID = @CustomerID  
    ```  
  
    > [!NOTE]
    >  验证数据库的参数语法是否正确。 例如，在 Microsoft Access 中，WHERE 子句应当如下：`WHERE CustomerID = ?`。  
  
6.  单击 **“下一步”**。  
  
7.  有关**填充 DataTableMethod 名称**，类型`FillByCustomerID`。  
  
8.  清除**返回 DataTable**选项，并依次**下一步**。  
  
9. 单击 **“完成”**。  
  
## <a name="create-a-method-on-form2-to-pass-data-to"></a>在要传入数据的 Form2 上创建方法  
  
#### <a name="to-create-a-method-to-pass-data-to"></a>创建要传入数据的方法  
  
1.  右键单击**Form2**，然后选择**查看代码**以打开**Form2**中**代码编辑器**。  
  
2.  以下代码添加到**Form2**后`Form2_Load`方法：  
  
     [!code-vb[VbRaddataDisplaying#1](../data-tools/codesnippet/VisualBasic/pass-data-between-forms_1.vb)]
     [!code-csharp[VbRaddataDisplaying#1](../data-tools/codesnippet/CSharp/pass-data-between-forms_1.cs)]  
  
## <a name="create-a-method-on-form1-to-pass-data-and-display-form2"></a>在 Form1 传递数据并显示 Form2 上创建方法  
  
#### <a name="to-create-a-method-to-pass-data-to-form2"></a>创建向 Form2 传递数据的方法  
  
1.  在**Form1**，客户数据网格中，右键单击，然后单击**属性**。  
  
2.  在**属性**窗口中，单击**事件**。  
  
3.  双击**celldoubleclick**事件。  
  
     将显示代码编辑器。  
  
4.  更新方法定义以匹配以下示例：  
  
     [!code-csharp[VbRaddataDisplaying#2](../data-tools/codesnippet/CSharp/pass-data-between-forms_2.cs)]
     [!code-vb[VbRaddataDisplaying#2](../data-tools/codesnippet/VisualBasic/pass-data-between-forms_2.vb)]  
  
## <a name="run-the-application"></a>运行应用程序  
  
#### <a name="to-run-the-application"></a>运行应用程序  
  
-   按 F5 运行该应用程序。  
  
-   双击中的客户记录**Form1**以打开**Form2**与该客户的订单。  
  
## <a name="next-steps"></a>后续步骤  
 根据应用程序的需求，在窗体间传递数据之后可能还需要执行一些步骤。 你可以通过以下操作来增强此演练的效果：  
  
-   编辑数据集，以添加或移除数据库对象。 有关详细信息，请参阅[创建和配置数据集](../data-tools/create-and-configure-datasets-in-visual-studio.md)。  
  
-   添加将数据保存回数据库的功能。 有关详细信息，请参阅[将数据保存回数据库](../data-tools/save-data-back-to-the-database.md)。  
  
## <a name="see-also"></a>另请参阅  
 [在 Visual Studio 中将 Windows 窗体控件绑定到数据](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)