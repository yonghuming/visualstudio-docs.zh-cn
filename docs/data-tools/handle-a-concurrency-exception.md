---
title: "演练：处理并发异常 | Microsoft Docs"
ms.custom: ""
ms.date: "09/21/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "并发控制, 异常"
  - "并发控制, 演练"
  - "数据并发, 演练"
  - "数据集 [Visual Basic], 错误"
  - "异常处理, 并发问题"
  - "更新数据集, 错误"
ms.assetid: 73ee9759-0a90-48a9-bf7b-9d6fc17bff93
caps.latest.revision: 23
caps.handback.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 演练：处理并发异常
当两个用户同时尝试更改数据库中的相同数据时会引发并发异常 \(<xref:System.Data.DBConcurrencyException>\)。  在本演练中，将创建一个 Windows 应用程序来阐释如何捕获 <xref:System.Data.DBConcurrencyException>、定位引起错误的行并给出一个处理错误的策略。  
  
 本演练将指导您进行以下过程：  
  
1.  创建新的**“Windows 应用程序”**项目。  
  
2.  根据 Northwind `Customers` 表创建新的数据集。  
  
3.  创建具有 <xref:System.Windows.Forms.DataGridView> 的窗体来显示数据。  
  
4.  用 Northwind 数据库中的 `Customers` 表的数据填充数据集。  
  
5.  填充数据集后，使用 Visual Studio 中的 [Visual Database Tools](http://msdn.microsoft.com/zh-cn/6b145922-2f00-47db-befc-bf351b4809a1) 直接访问 `Customers` 数据表并更改记录。  
  
6.  然后在该窗体中，将同一记录更改为不同的值，更新数据集，并尝试将更覆盖入数据库，这将导致引发并发错误。  
  
7.  捕获错误并显示不同版本的记录，以便用户可以确定是继续更新数据库还是取消更新。  
  
## 系统必备  
 若要完成本演练，您需要：  
  
-   能够访问 Northwind 示例数据库并具有执行更新的权限。  有关详细信息，请参阅[如何：安装示例数据库](../data-tools/how-to-install-sample-databases.md)。  
  
> [!NOTE]
>  显示的对话框和菜单命令可能会与“帮助”中的描述不同，具体取决于您现用的设置或版本。  若要更改设置，请在**“工具”**菜单上选择**“导入和导出设置”**。  有关详细信息，请参阅[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-cn/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
## 创建新项目  
 从创建新的 Windows 应用程序开始演练。  
  
#### 创建新的 Windows 应用程序项目  
  
1.  从**“文件”**菜单创建一个新的项目。  
  
2.  在**“项目类型”**窗格中选择一种编程语言。  
  
3.  在**“模板”**窗格中选择**“Windows 应用程序”**。  
  
4.  将项目命名为 `ConcurrencyWalkthrough`，然后单击**“确定”**。  
  
     Visual Studio 随即将该项目添加到**“解决方案资源管理器”**，并在设计器中显示一个新窗体。  
  
## 创建 Northwind 数据集  
 本节中将创建名为 `NorthwindDataSet` 的数据集。  
  
#### 创建 NorthwindDataSet  
  
1.  从**“数据”**菜单中选择**“添加新数据源”**。  
  
     [数据源配置向导](../data-tools/media/data-source-configuration-wizard.png)随即打开。  
  
2.  在**“选择数据源类型”**页面上选择**“数据库”**。  
  
3.  从可用连接列表中选择一个到 Northwind 示例数据库的连接，如果连接列表中的连接不可用则单击**“新建连接”**。  
  
    > [!NOTE]
    >  如果要连接到本地数据库文件，则当询问是否将文件添加到项目中时，选择**“否”**。  
  
4.  在**“将连接字符串保存到应用程序配置文件”**页面上单击**“下一步”**。  
  
5.  展开**“Tables”**节点并选择 `Customers` 表。  数据集的默认名称应为 `NorthwindDataSet`。  
  
6.  单击**“完成”**将数据集添加到项目中。  
  
## 创建数据绑定 DataGridView 控件  
 在本节中，将通过把**“Customers”**项从**“数据源”**窗口拖动到 Windows 窗体上来创建 <xref:System.Windows.Forms.DataGridView>。  
  
#### 创建绑定到 Customers 表的 DataGridView 控件  
  
1.  从**“数据”**菜单中选择**“显示数据源”**来打开**“数据源”**窗口。  
  
2.  从**“数据源”**窗口展开**“NorthwindDataSet”**节点并选择**“Customers”**表。  
  
3.  单击表节点上的下拉箭头并从下拉列表中选择**“DataGridView”**。  
  
4.  将表拖动到窗体上的空白区域中。  
  
     一个名为 `CustomersDataGridView` 的 <xref:System.Windows.Forms.DataGridView> 控件和一个名为 `CustomersBindingNavigator` 的 <xref:System.Windows.Forms.BindingNavigator> 被添加到绑定到 <xref:System.Windows.Forms.BindingSource>（它进而被绑定到 `NorthwindDataSet` 中的 `Customers` 表）的窗体中。  
  
## 检查点  
 现在可以测试窗体，以确定此时它的行为与预期相同。  
  
#### 测试窗体  
  
1.  按 F5 运行该应用程序  
  
     窗体出现，上面带有一个用 `Customers` 表中的数据填充的 <xref:System.Windows.Forms.DataGridView> 控件。  
  
2.  从**“调试”**菜单中选择**“停止调试”**。  
  
## 处理并发错误  
 处理错误的方式取决于应用程序所遵循的特定业务规则。  对于本演练，为了举例说明，在引发并发冲突后将使用下面的策略来处理并发错误：  
  
 应用程序将为用户显示记录的三个版本：  
  
-   数据库中的当前记录。  
  
-   加载到数据集中的原始记录。  
  
-   数据集中的建议更改。  
  
 然后用户就能够使用建议版本覆盖数据库，或是取消更新并用数据库中的新值刷新数据集。  
  
#### 启用并发错误的处理  
  
1.  创建自定义错误处理程序。  
  
2.  向用户显示选项。  
  
3.  处理用户的响应。  
  
4.  重新发送更新，或重新设置数据集中的数据。  
  
### 添加用于处理并发异常的代码  
 当尝试执行更新且引发了异常时，通常会希望利用异常所提供的信息。  
  
 在本节中，将添加代码，以尝试更新数据库，并处理可能引发的任何 <xref:System.Data.DBConcurrencyException> 以及任何其他异常。  
  
> [!NOTE]
>  本演练的后面部分将添加 `CreateMessage` 和 `ProcessDialogResults` 方法。  
  
##### 添加并发错误的错误处理程序  
  
1.  将以下代码添加到 `Form1_Load` 方法下：  
  
     [!code-cs[VbRaddataConcurrency#1](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_1.cs)]
     [!code-vb[VbRaddataConcurrency#1](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_1.vb)]  
  
2.  替换 `CustomersBindingNavigatorSaveItem_Click` 方法以调用 `UpdateDatabase` 方法，使其形式如下所示：  
  
     [!code-cs[VbRaddataConcurrency#2](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_2.cs)]
     [!code-vb[VbRaddataConcurrency#2](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_2.vb)]  
  
### 向用户显示选项  
 您刚编写的代码将调用 `CreateMessage` 过程来向用户显示错误信息。  对于本演练，您将使用一个消息框来向用户显示记录的不同版本，并让用户选择是用新更改覆盖记录还是取消编辑。  用户选择该消息框上的选项（单击按钮）后，响应将传递到 `ProcessDialogResult` 方法。  
  
##### 创建要向用户显示的消息  
  
-   在**“代码编辑器”**中添加下面的代码来创建该消息。  在 `UpdateDatabase` 方法下输入此代码。  
  
     [!code-cs[VbRaddataConcurrency#4](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_3.cs)]
     [!code-vb[VbRaddataConcurrency#4](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_3.vb)]  
  
### 处理用户的响应  
 您还需要用代码来处理用户对消息框的响应。  可以用建议的更改覆盖数据库中的当前记录，也可以放弃本地更改并用数据库中的当前记录刷新数据表。  如果用户选择"是", <xref:System.Data.DataTable.Merge%2A> 方法将被调用，同时 *preserveChanges* 参数设置为 `true`。  由于记录的初始版本现在与数据库中的记录匹配，所以更新尝试将会成功。  
  
##### 处理消息框中的用户输入  
  
-   在上一节所添加的代码下添加下面的代码。  
  
     [!code-cs[VbRaddataConcurrency#3](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_4.cs)]
     [!code-vb[VbRaddataConcurrency#3](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_4.vb)]  
  
## 测试  
 现在可以测试窗体，以确保其行为与预期相同。  要模拟并发冲突，需要在填充 NorthwindDataSet 之后更改数据库中的数据。  
  
#### 测试窗体  
  
1.  按 F5 运行该应用程序。  
  
2.  窗体出现后，使其保持运行并切换到 Visual Studio IDE。  
  
3.  从**“视图”**菜单中选择**“服务器资源管理器”**。  
  
4.  在**“服务器资源管理器”**中，展开您的应用程序正在使用的连接，然后展开**“Tables”**节点。  
  
5.  右击**“Customers”**表并选择**“显示表数据”**。  
  
6.  在第一条记录 \(`ALFKI`\) 中，将 `ContactName` 更改为 `Maria Anders2`。  
  
    > [!NOTE]
    >  导航至另一行以提交更改。  
  
7.  切换到 `ConcurrencyWalkthrough` 的运行窗体。  
  
8.  在窗体上的第一条记录 \(`ALFKI`\) 中，将 `ContactName` 更改为 `Maria Anders1`。  
  
9. 单击**“保存”**按钮。  
  
     引发并发错误，并出现消息框。  
  
10. 单击**“否”**会取消更新，并用数据库中的当前值更新数据集，而单击**“是”**则会将建议值写入数据库。  
  
## 请参阅  
 [数据演练](../Topic/Data%20Walkthroughs.md)   
 [在 Visual Studio 中将 Windows 窗体控件绑定到数据](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [连接到 Visual Studio 中的数据](../data-tools/connecting-to-data-in-visual-studio.md)   
 [准备应用程序以接收数据](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [将数据获取到应用程序](../data-tools/fetching-data-into-your-application.md)   
 [在 Visual Studio 中将控件绑定到数据](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [在应用程序中编辑数据](../data-tools/editing-data-in-your-application.md)   
 [验证数据](../Topic/Validating%20Data.md)   
 [保存数据](../data-tools/saving-data.md)