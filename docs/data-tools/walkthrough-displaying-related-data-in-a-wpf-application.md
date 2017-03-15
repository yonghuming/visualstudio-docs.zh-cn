---
title: "演练：在 WPF 应用程序中显示相关数据 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "WPF 数据绑定 [Visual Studio], 演练"
  - "WPF 设计器, 数据绑定"
  - "WPF, Visual Studio 中的数据绑定"
ms.assetid: 5c48f188-e9c4-40a6-97d9-67cdb2f90127
caps.latest.revision: 25
caps.handback.revision: 25
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# 演练：在 WPF 应用程序中显示相关数据
在本演练中，您将创建一个 WPF 应用程序，该应用程序显示具有父\/子关系的数据表中的数据。  这些数据封装在实体数据模型的各个实体中。  父实体包含一组订单的摘要信息。  此实体的每个属性均绑定到应用程序中的不同控件。  子实体包含每份订单的详细信息。  这组数据绑定到 <xref:System.Windows.Controls.DataGrid> 控件。  
  
 本演练阐释了以下任务：  
  
-   创建一个 WPF 应用程序和一个利用 AdventureWorksLT 示例数据库中的数据生成的实体数据模型。  
  
-   创建一组数据绑定控件，这些控件显示一组订单的摘要信息。  通过将父实体从**“数据源”**窗口拖动到**“WPF 设计器”**来创建这些控件。  
  
-   创建一个 <xref:System.Windows.Controls.DataGrid> 控件，该控件显示每份选定订单的相关详细信息。  通过将子实体从**“数据源”**窗口拖动到**“WPF 设计器”**中的一个窗口来创建这些控件。  
  
     [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## 系统必备  
 您需要以下组件来完成本演练：  
  
-   [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
-   对附加了 AdventureWorksLT 示例数据库的 SQL Server 或 SQL Server Express 的正在运行的实例的访问权限。  您可以从 [CodePlex 网站](http://go.microsoft.com/fwlink/?linkid=87843)下载 AdventureWorksLT 数据库。  
  
 事先了解以下概念也很有用，但对于完成本演练并不是必需的：  
  
-   实体数据模型和 ADO.NET Entity Framework。  有关更多信息，请参见 [实体框架概述](../Topic/Entity%20Framework%20Overview.md)。  
  
-   使用 WPF 设计器。  有关更多信息，请参见 [WPF and Silverlight Designer 概述](http://msdn.microsoft.com/zh-cn/570b7a5c-0c86-4326-a371-c9b63378fc62)。  
  
-   WPF 数据绑定。  有关更多信息，请参见[数据绑定概述](../Topic/Data%20Binding%20Overview.md)。  
  
## 创建项目  
 创建新的 WPF 项目以显示订单记录。  
  
#### 创建新的 WPF 项目  
  
1.  启动 Visual Studio。  
  
2.  在**“文件”**菜单上指向**“新建”**，再单击**“项目”**。  
  
3.  展开**“Visual C\#”**或**“Visual Basic”**，然后选择**“Windows”**。  
  
4.  确保在对话框顶部的组合框中选择**“.NET Framework 4”**。  本演练中使用的 <xref:System.Windows.Controls.DataGrid> 控件仅在 .NET Framework 4 中可用。  
  
5.  选择**“WPF 应用程序”**项目模板。  
  
6.  在**“名称”**框中键入 `AdventureWorksOrdersViewer`。  
  
7.  单击**“确定”**。  
  
     Visual Studio 将创建 `AdventureWorksOrdersViewer` 项目。  
  
## 为应用程序创建实体数据模型  
 您必须先为应用程序定义数据模型并将此模型添加到**“数据源”**窗口中，然后才能创建数据绑定控件。  在本演练中，数据模型为实体数据模型。  
  
#### 创建实体数据模型  
  
1.  在**“数据”**菜单上，单击**“添加新数据源”**打开**“数据源配置向导”**。  
  
2.  在**“选择数据源类型”**页上，单击**“数据库”**，然后单击**“下一步”**。  
  
3.  在**“选择数据库模型”**页上，单击**“实体数据模型”**，然后单击**“下一步”**。  
  
4.  在**“选择模型内容”**页上，单击**“从数据库生成”**，然后单击**“下一步”**。  
  
5.  在**“选择您的数据连接”**页上，执行下列操作之一：  
  
    -   如果下拉列表中包含到 AdventureWorksLT 示例数据库的数据连接，请选择该连接。  
  
         \- 或 \-  
  
    -   单击**“新建连接”**并创建到 AdventureWorksLT 数据库的连接。  
  
     确保选择了**“将 App.Config 中的实体连接设置另存为”**选项，然后单击**“下一步”**。  
  
6.  在**“选择数据库对象”**页上，展开**“表”**，然后选择以下表：  
  
    -   **SalesOrderDetail**  
  
    -   **SalesOrderHeader**  
  
7.  单击**“完成”**。  
  
8.  生成项目。  
  
## 创建显示订单的数据绑定控件  
 通过将 `SalesOrderHeaders` 实体从**“数据源”**窗口中拖动到 WPF 设计器中，创建显示订单记录的控件。  
  
#### 创建显示订单记录的数据绑定控件  
  
1.  在**“解决方案资源管理器”**中，双击 MainWindow.xaml。  
  
     将在 WPF 设计器中打开相应的窗口。  
  
2.  编辑 XAML，将**“Height”**和**“Width”**属性设置为 800。  
  
3.  在**“数据源”**窗口中，单击**“SalesOrderHeaders”**节点的下拉菜单，并选择**“详细信息”**。  
  
4.  展开**“SalesOrderHeaders”**节点。  
  
5.  单击**“SalesOrderID”**旁边的下拉菜单，并选择**“ComboBox”**。  
  
6.  对于**“SalesOrderHeaders”**节点的以下每个子节点，单击节点旁边的下拉菜单并选择**“无”**：  
  
    -   **RevisionNumber**  
  
    -   **OnlineOrderFlag**  
  
    -   **ShipToAddressID**  
  
    -   **BillToAddressID**  
  
    -   **CreditCardApprovalCode**  
  
    -   **SubTotal**  
  
    -   **TaxAmt**  
  
    -   **Freight**  
  
    -   **rowguid**  
  
    -   **ModifiedDate**  
  
     此操作将阻止 Visual Studio 在下一步中为这些节点创建数据绑定控件。  对于本演练，假定最终用户不需要查看此数据。  
  
7.  从**“数据源”**窗口中，将**“SalesOrderHeaders”**节点拖动到**“WPF 设计器”**中的窗口。  
  
     Visual Studio 将生成 XAML 和代码，前者创建一组绑定到**“SalesOrderHeaders”**实体中数据的控件，后者加载数据。  有关生成的 XAML 和代码的更多信息，请参见[在 Visual Studio 中将 WPF 控件绑定到数据](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)。  
  
8.  在设计器中，单击**“Sales Order ID”（销售订单 ID）**标签旁边的组合框。  
  
9. 在**“属性”**窗口中，选中**“IsReadOnly”**属性旁边的复选框。  
  
## 创建显示订单详细信息的 DataGrid  
 通过将 `SalesOrderDetails` 实体从**“数据源”**窗口拖动到 WPF 设计器中，创建显示订单详细信息的 <xref:System.Windows.Controls.DataGrid> 控件。  
  
#### 创建显示订单详细信息的 DataGrid  
  
1.  在**“数据源”**窗口中，找到作为**“SalesOrderHeaders”**节点的子级的**“SalesOrderDetails”**节点。  
  
    > [!NOTE]
    >  还有一个与**“SalesOrderHeaders”**节点同级的**“SalesOrderDetails”**节点。  请确保已选择**“SalesOrderHeaders”**节点的子节点。  
  
2.  展开子**“SalesOrderDetails”**节点。  
  
3.  对于**“SalesOrderDetails”**节点的以下每个子节点，单击节点旁边的下拉菜单并选择**“无”**：  
  
    -   **SalesOrderID**  
  
    -   **SalesOrderDetailID**  
  
    -   **rowguid**  
  
    -   **ModifiedDate**  
  
     此操作会阻止 Visual Studio 将此数据包含在下一个步骤创建的 <xref:System.Windows.Controls.DataGrid> 控件中。  对于本演练，假定最终用户不需要查看此数据。  
  
4.  从**“数据源”**窗口中，将子**“SalesOrderDetails”**节点拖动到**“WPF 设计器”**中的窗口。  
  
     Visual Studio 将生成 XAML 以定义新的数据绑定 <xref:System.Windows.Controls.DataGrid> 控件，该控件将显示在设计器中。  Visual Studio 还会在代码隐藏文件中更新生成的 `GetSalesOrderHeadersQuery` 方法以包含**“SalesOrderDetails”**实体中的数据。  
  
## 测试应用程序  
 生成并运行应用程序，以验证应用程序是否显示订单记录。  
  
#### 测试应用程序  
  
1.  按 F5。  
  
     这将生成并运行应用程序。  确认以下事项：  
  
    -   **“Sales Order ID”（销售订单 ID）**组合框将显示**“71774”**。  这是实体中第一个订单 ID。  
  
    -   对于您在**“Sales Order ID”（销售订单 ID）**组合框中选择的每份订单，<xref:System.Windows.Controls.DataGrid> 中都会显示详细的订单信息。  
  
2.  关闭应用程序。  
  
## 后续步骤  
 完成本演练之后，请了解如何使用 Visual Studio 中的**“数据源”**窗口将 WPF 控件绑定到其他类型的数据源。  有关更多信息，请参见[演练：将 WPF 控件绑定到 WCF 数据服务](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)和[演练：将 WPF 控件绑定到数据集](../data-tools/bind-wpf-controls-to-a-dataset.md)。  
  
## 请参阅  
 [在 Visual Studio 中将 WPF 控件绑定到数据](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)   
 [如何：在 WPF 应用程序中显示相关数据](../data-tools/display-related-data-in-wpf-applications.md)