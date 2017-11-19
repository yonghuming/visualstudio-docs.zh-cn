---
title: "处理并发异常 |Microsoft 文档"
ms.custom: 
ms.date: 09/11/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- concurrency control, exceptions
- datasets [Visual Basic], errors
- exception handling, concurrency issues
- data concurrency, walkthroughs
- updating datasets, errors
- concurrency control, walkthroughs
ms.assetid: 73ee9759-0a90-48a9-bf7b-9d6fc17bff93
caps.latest.revision: "23"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 9162274d234c22e8bbe299389d2b41f57a69d714
ms.sourcegitcommit: ec1c7e7e3349d2f3a4dc027e7cfca840c029367d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/07/2017
---
# <a name="handle-a-concurrency-exception"></a>处理并发异常
并发异常 (<xref:System.Data.DBConcurrencyException>) 当两个用户尝试在同一时间更改数据库中的相同数据时引发。 在本演练中，你创建的 Windows 应用程序演示如何捕获<xref:System.Data.DBConcurrencyException>，找到，导致该错误的行并了解如何进行处理的策略。  
  
 本演练将指导你完成以下过程：  
  
1.  创建新的 **Windows 窗体应用程序**项目。  
  
2.  创建新的数据集基于 Northwind`Customers`表。  
  
3.  创建的窗体具有<xref:System.Windows.Forms.DataGridView>以显示数据。  
  
4.  使用数据填充数据集`Customers`Northwind 数据库中的表。  
  
5.  使用**显示表数据**功能**服务器资源管理器**访问`Customers`表的数据和更改记录。  
  
6.  为不同的值更改同一记录，更新数据集，并尝试将更改写入数据库，这会导致引发并发错误。  
  
7.  捕获到的错误，则显示的记录，以便确定是否继续并更新数据库，或者取消更新用户的不同版本。  
  
## <a name="prerequisites"></a>先决条件  
本演练使用 SQL Server Express LocalDB 和 Northwind 示例数据库。  
  
1.  如果你没有 SQL Server Express LocalDB，将其安装从[SQL Server 版本的下载页](https://www.microsoft.com/en-us/server-cloud/Products/sql-server-editions/sql-server-express.aspx)，或通过**Visual Studio Installer**。 在 Visual Studio 安装程序中，SQL Server Express LocalDB 可以安装的一部分**数据存储和处理**工作负荷，也可以作为单个组件。  
  
2.  按照这些步骤来安装 Northwind 示例数据库：  

    1. 在 Visual Studio 中，打开**SQL Server 对象资源管理器**窗口。 (SQL Server 对象资源管理器安装的一部分**数据存储和处理**在 Visual Studio 安装程序中的工作负荷。)展开**SQL Server**节点。 LocalDB 实例上右键单击并选择**新查询...**.  

       查询编辑器窗口将打开。  

    2. 复制[Northwind TRANSACT-SQL 脚本](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true)到剪贴板。 此 T-SQL 脚本从头创建 Northwind 数据库，并使用数据填充它。  

    3. 将 T-SQL 脚本粘贴到查询编辑器中，，然后选择**执行**按钮。  

       短时间内之后, 执行完查询和创建 Northwind 数据库。  
  
> [!NOTE]
>  显示的对话框和菜单命令可能会与不同帮助中的描述具体取决于你现用的设置或要使用的版本。 若要更改设置，请在 **“工具”** 菜单上选择 **“导入和导出设置”** 。 有关详细信息，请参阅[个性化设置 Visual Studio IDE](../ide/personalizing-the-visual-studio-ide.md)。  
  
## <a name="create-a-new-project"></a>创建新项目  
 通过创建新的 Windows 窗体应用程序开始你演练。  
  
#### <a name="to-create-a-new-windows-forms-application-project"></a>创建新的 Windows 窗体应用程序项目  
  
1. 在 Visual Studio 中，在**文件**菜单上，选择**新建**，**项目...**.  
  
2. 展开**Visual C#**或**Visual Basic**在左侧窗格中，然后选择**Windows 经典桌面**。  

3. 在中间窗格中，选择**Windows 窗体应用程序**项目类型。  

4. 将项目**ConcurrencyWalkthrough**，然后选择**确定**。 
  
     **ConcurrencyWalkthrough**创建项目并将其添加到**解决方案资源管理器**，并在设计器中打开一个新的表单。  
  
## <a name="create-the-northwind-dataset"></a>创建的罗斯文数据集  
 在本部分中，你将创建名为数据集`NorthwindDataSet`。  
  
#### <a name="to-create-the-northwinddataset"></a>若要创建 NorthwindDataSet  
  
1.  上**数据**菜单上，选择**添加新数据源**。  
  
     [数据源配置向导](../data-tools/media/data-source-configuration-wizard.png)打开。  
  
2.  上**选择数据源类型**屏幕上，选择**数据库**。  
  
3.  选择一个连接到 Northwind 示例数据库，从可用连接列表。 如果连接不可用的连接列表中，选择**新连接**  
  
    > [!NOTE]
    >  如果您要连接到本地数据库文件，选择**否**当系统询问您是否要将文件添加到你的项目。  
  
4.  上**将连接字符串保存到应用程序配置文件**屏幕上，选择**下一步**。  
  
5.  展开**表**节点，然后选择`Customers`表。 数据集的默认名称应为`NorthwindDataSet`。  
  
6.  选择**完成**将数据集添加到项目。  
  
## <a name="create-a-data-bound-datagridview-control"></a>创建数据绑定 DataGridView 控件  
 在本部分中，你创建<xref:System.Windows.Forms.DataGridView>通过拖动**客户**项从**数据源**拖到 Windows 窗体的窗口。  
  
#### <a name="to-create-a-datagridview-control-that-is-bound-to-the-customers-table"></a>创建绑定到客户表的 DataGridView 控件  
  
1.  上**数据**菜单上，选择**显示数据源**以打开**数据源窗口**。  
  
2.  在**数据源**窗口中，展开**NorthwindDataSet**节点，，然后选择**客户**表。  
  
3.  选择表节点上的向下箭头，然后选择**DataGridView**下拉列表中。  
  
4.  表拖到窗体的空白区域。  
  
     A<xref:System.Windows.Forms.DataGridView>控件名为`CustomersDataGridView`和<xref:System.Windows.Forms.BindingNavigator>名为`CustomersBindingNavigator`添加到窗体绑定到<xref:System.Windows.Forms.BindingSource>。这是在中，打开绑定到`Customers`表中`NorthwindDataSet`。  
  
## <a name="test-the-form"></a>测试窗体  
 你现在可以测试窗体，以确保其行为与预期到目前为止相同。  
  
#### <a name="to-test-the-form"></a>若要测试窗体  
  
1.  选择**F5**运行该应用程序  
  
     窗体将显示<xref:System.Windows.Forms.DataGridView>上的控件中的数据填充`Customers`表。  
  
2.  上**调试**菜单上，选择**停止调试**。  
  
## <a name="handle-concurrency-errors"></a>处理并发错误  
 处理错误的方式取决于用于管理你的应用程序的特定业务规则。 对于本演练，我们使用以下策略作为示例，有关如何处理并发错误。  
  
 应用程序向用户提供的记录的三个版本：  
  
-   数据库中的当前记录  
  
-   原始记录加载到数据集  
  
-   在数据集中建议的更改  
  
然后，用户就能够使用建议的版本中，覆盖数据库，或取消更新刷新来自数据库的新值的数据集。  
  
#### <a name="to-enable-the-handling-of-concurrency-errors"></a>若要启用并发错误的处理  
  
1.  创建自定义错误处理程序。  
  
2.  向用户显示的选择。  
  
3.  处理用户的响应。  
  
4.  重新发送更新，或重置数据集中的数据。  
  
### <a name="add-code-to-handle-the-concurrency-exception"></a>添加代码来处理并发异常  
 当你尝试执行的更新，并引发了异常时，你通常想要使用由引发的异常的信息执行某些操作。  
  
 在此部分中，你将添加尝试更新数据库的代码。 你还处理任何<xref:System.Data.DBConcurrencyException>可能引发的以及任何其他异常。  
  
> [!NOTE]
>  `CreateMessage`和`ProcessDialogResults`方法将添加在本演练后面。  
  
##### <a name="to-add-error-handling-for-the-concurrency-error"></a>若要添加的错误处理并发错误  
  
1.  添加下面的代码下面`Form1_Load`方法：  
  
     [!code-csharp[VbRaddataConcurrency#1](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_1.cs)]
     [!code-vb[VbRaddataConcurrency#1](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_1.vb)]  
  
2.  替换`CustomersBindingNavigatorSaveItem_Click`方法来调用`UpdateDatabase`方法，以便其类似以下所示：  
  
     [!code-csharp[VbRaddataConcurrency#2](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_2.cs)]
     [!code-vb[VbRaddataConcurrency#2](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_2.vb)]  
  
### <a name="display-choices-to-the-user"></a>向用户显示选项  
 你刚的代码编写调用`CreateMessage`过程来向用户显示错误信息。 对于本演练，你可以使用一个消息框以向用户显示该记录的不同版本。 这使用户能够选择是要使用所做的更改覆盖记录还是取消编辑。 一旦用户在消息框中选择的选项 （单击一个按钮），响应传递给`ProcessDialogResult`方法。  
  
##### <a name="to-create-the-message-to-display-to-the-user"></a>若要创建要向用户显示的消息  
  
-   通过添加以下代码创建消息**代码编辑器**。 输入下面的这个代码`UpdateDatabase`方法。  
  
     [!code-csharp[VbRaddataConcurrency#4](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_3.cs)]
     [!code-vb[VbRaddataConcurrency#4](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_3.vb)]  
  
### <a name="process-the-users-response"></a>处理用户的响应  
 你还需要用于处理用户的响应消息框的代码。 选项，可使用建议的更改，覆盖当前数据库中的记录或放弃本地更改并刷新与目前数据库中的记录的数据表。 如果用户选择是，<xref:System.Data.DataTable.Merge%2A>方法调用与*preserveChanges*参数设置为`true`。 这将导致更新尝试将会成功，因为该记录的原始版本现在匹配数据库中的记录。  
  
##### <a name="to-process-the-user-input-from-the-message-box"></a>从消息框中处理用户输入  
  
-   添加下面的代码已添加上一节中的代码。  
  
     [!code-csharp[VbRaddataConcurrency#3](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_4.cs)]
     [!code-vb[VbRaddataConcurrency#3](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_4.vb)]  
  
## <a name="test-the-form"></a>测试窗体  
 你现在可以测试窗体，以确保其行为与预期相同。 若要模拟并发冲突需要填写 NorthwindDataSet 之后更改数据库中的数据。  
  
#### <a name="to-test-the-form"></a>若要测试窗体  
  
1.  选择**F5**运行该应用程序。  
  
2.  窗体显示后，保持运行，并切换到 Visual Studio IDE。  
  
3.  上**视图**菜单上，选择**服务器资源管理器**。  
  
4.  在**服务器资源管理器**，展开连接你的应用程序是否使用，以及然后展开**表**节点。  
  
5.  右键单击**客户**表，，然后选择**显示表数据**。  
  
6.  在第一条记录 (`ALFKI`) 更改`ContactName`到`Maria Anders2`。  
  
    > [!NOTE]
    >  导航到不同的行，以提交更改。  
  
7.  切换到`ConcurrencyWalkthrough`的运行窗体。  
  
8.  在窗体上的第一个记录 (`ALFKI`)，更改`ContactName`到`Maria Anders1`。  
  
9. 选择**保存**按钮。  
  
     引发并发错误，并出现消息框。  
  
10. 选择**否**取消更新并使用当前数据库中的值更新数据集。 选择**是**建议的值写入数据库。  
  
## <a name="see-also"></a>另请参阅  
 [将数据保存回数据库](../data-tools/save-data-back-to-the-database.md)
