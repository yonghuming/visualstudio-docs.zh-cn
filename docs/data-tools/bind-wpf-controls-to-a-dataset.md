---
title: "演练：将 WPF 控件绑定到数据集 | Microsoft Docs"
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
ms.assetid: 177420b9-568b-4dad-9d16-1b0e98a24d71
caps.latest.revision: 32
caps.handback.revision: 30
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 演练：将 WPF 控件绑定到数据集
在本演练中，你将创建一个包含数据绑定控件的 WPF 应用程序。  这些控件将绑定到在数据集中封装的产品记录。  你还将添加用于浏览产品和保存对产品记录所做的更改的按钮。  
  
 本演练阐释了以下任务：  
  
-   创建一个 WPF 应用程序和一个利用 AdventureWorksLT 示例数据库中的数据生成的数据集。  
  
-   通过将一个数据表从**“数据源”**窗口拖到 WPF 设计器的一个窗口中，创建一组数据绑定控件。  
  
-   创建用于向前\/向后导航产品记录的按钮。  
  
-   创建一个用于将用户对产品记录所做的更改保存到数据表和基础数据源的按钮。  
  
     [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## 系统必备  
 你需要以下组件来完成本演练：  
  
-   [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]  
  
-   对附加了 AdventureWorksLT 示例数据库的 SQL Server 或 SQL Server Express 的正在运行的实例的访问权限。  你可以从 [CodePlex 网站](http://go.microsoft.com/fwlink/?linkid=87843)下载 AdventureWorksLT 数据库。  
  
 事先了解以下概念也很有用，但对于完成本演练并不是必需的：  
  
-   数据集和 TableAdapter。  有关详细信息，请参阅[在 Visual Studio 中使用数据集](../data-tools/dataset-tools-in-visual-studio.md)和[TableAdapter 概述](../data-tools/tableadapter-overview.md)。  
  
-   使用 WPF 设计器。  有关详细信息，请参阅[WPF and Silverlight Designer 概述](http://msdn.microsoft.com/zh-cn/570b7a5c-0c86-4326-a371-c9b63378fc62)。  
  
-   WPF 数据绑定。  有关详细信息，请参阅[数据绑定概述](../Topic/Data%20Binding%20Overview.md)。  
  
## 创建项目  
 创建一个新的 WPF 项目。  该项目将显示产品记录。  
  
#### 创建项目  
  
1.  启动 Visual Studio。  
  
2.  在**“文件”**菜单上，指向**“新建”**，然后单击**“项目”**。  
  
3.  展开**“Visual Basic”**或**“Visual C\#”**，然后选择**“Windows”**。  
  
4.  选择**“WPF 应用程序”**项目模板。  
  
5.  在**“名称”**框中，键入 `AdventureWorksProductsEditor`，然后单击**“确定”**。  
  
     Visual Studio 将创建 `AdventureWorksProductsEditor` 项目。  
  
## 为应用程序创建数据集  
 你必须先为应用程序定义数据模型并将此模型添加到**“数据源”**窗口中，然后才能创建数据绑定控件。  在本演练中，你将创建要用作数据模型的数据集。  
  
#### 创建数据集  
  
1.  在**“数据”**菜单上，单击**“显示数据源”**。  
  
     将打开**“数据源”**窗口。  
  
2.  在**“数据源”**窗口中，单击**“添加新数据源”**。  
  
     **“数据源配置向导”**打开。  
  
3.  在**“选择数据源类型”**页上，选择**“数据库”**，然后单击**“下一步”**。  
  
4.  在**“选择数据库模型”**页上，选择**“数据集”**，然后单击**“下一步”**。  
  
5.  在**“选择你的数据连接”**页面上，选择以下选项之一：  
  
    -   如果下拉列表中包含到 AdventureWorksLT 示例数据库的数据连接，请选择该连接，然后单击**“下一步”**。  
  
         \- 或 \-  
  
    -   单击**“新建连接”**，然后创建到 AdventureWorksLT 数据库的连接。  
  
6.  在**“将连接字符串保存到应用程序配置文件中”**页面上，选中**“是，将连接另存为”**复选框，然后单击**“下一步”**。  
  
7.  在**“选择数据库对象”**页面上，展开**“表”**，然后选择**“Product \(SalesLT\)”**表。  
  
8.  单击**“完成”**。  
  
     Visual Studio 会将新的 AdventureWorksLTDataSet.xsd 文件添加到项目中，并将相应的**“AdventureWorksLTDataSet”**项添加到**“数据源”**窗口中。  AdventureWorksLTDataSet.xsd 文件定义了一个名为 `AdventureWorksLTDataSet` 的类型化数据集和一个名为 `ProductTableAdapter` 的 TableAdapter。  在本演练后面的部分中，你将使用 `ProductTableAdapter` 向数据集填充数据，并将更改保存回数据库中。  
  
9. 生成项目。  
  
## 编辑 TableAdapter 的默认填充方法  
 若要向数据集填充数据，请使用 `ProductTableAdapter` 的 `Fill` 方法。  默认情况下，`Fill` 方法将向 `AdventureWorksLTDataSet` 中的 `ProductDataTable` 填充 Product 表包含的所有数据行。  你可以修改此方法以仅返回行的子集。  对于本演练而言，将修改 `Fill` 方法以仅返回具有照片的产品行。  
  
#### 加载具有照片的产品行  
  
1.  在**“解决方案资源管理器”**中，双击 AdventureWorksLTDataSet.xsd 文件。  
  
     这将打开数据集设计器。  
  
2.  在此设计器中，右键单击**“Fill,GetData\(\)”**查询，然后选择**“配置”**。  
  
     将打开**“TableAdapter 配置向导”**。  
  
3.  在**“输入 SQL 语句”**页面上，在文本框中的 `SELECT` 语句后添加以下 WHERE 子句。  
  
    ```  
    WHERE ThumbnailPhotoFileName <> 'no_image_available_small.gif'  
    ```  
  
4.  单击**“完成”**。  
  
## 定义用户界面  
 通过在 WPF 设计器中修改 XAML，将多个按钮添加到该窗口中。  在本演练后面的部分中，你将添加可让用户通过使用这些按钮来滚动和保存对产品记录所做的更改的代码。  
  
#### 定义窗口的用户界面  
  
1.  在**“解决方案资源管理器”**中，双击 MainWindow.xaml。  
  
     将在 WPF 设计器中打开相应的窗口。  
  
2.  在设计器的 [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] 视图中，在 `<Grid>` 标记之间添加以下代码：  
  
    ```  
    <Grid.RowDefinitions>  
        <RowDefinition Height="75" />  
        <RowDefinition Height="625" />  
    </Grid.RowDefinitions>  
    <Button HorizontalAlignment="Left" Margin="22,20,0,24" Name="backButton" Width="75"><</Button>  
    <Button HorizontalAlignment="Left" Margin="116,20,0,24" Name="nextButton" Width="75">></Button>  
    <Button HorizontalAlignment="Right" Margin="0,21,46,24" Name="saveButton" Width="110">Save changes</Button>  
    ```  
  
3.  生成项目。  
  
## 创建数据绑定控件  
 通过将 `Product` 表从**“数据源”**窗口拖到 WPF 设计器中，创建显示客户记录的控件。  
  
#### 创建数据绑定控件  
  
1.  在**“数据源”**窗口中，单击**“Product”**节点的下拉菜单，然后选择**“详细信息”**。  
  
2.  展开**“Product”**节点。  
  
3.  在本示例中，由于一些字段不会显示，因此单击以下节点旁边的下拉菜单，然后选择**“无”**：  
  
    -   ProductCategoryID  
  
    -   ProductModelID  
  
    -   ThumbnailPhotoFileName  
  
    -   rowguid  
  
    -   ModifiedDate  
  
4.  单击**“ThumbNailPhoto”**节点旁边的下拉菜单，然后选择**“图像”**。  
  
    > [!NOTE]
    >  默认情况下，已将**“数据源”**窗口中表示图片的项的默认控件设置为**“无”**。  这是因为，图片是作为字节数组存储在数据库中的，并且从简单的字节数组到大型应用程序的可执行文件都可以包含在字节数组中。  
  
5.  从**“数据源”**窗口中，将**“Product”**节点拖到位于包含按钮的行的下方的网格行。  
  
     Visual Studio 会生成 XAML，它定义了一组绑定到**“Products”**表中的数据的控件。  它还会生成用于加载数据的代码。  有关生成的 XAML 和代码的详细信息，请参阅[在 Visual Studio 中将 WPF 控件绑定到数据](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)。  
  
6.  在设计器中，单击**“产品 ID”**标签旁边的文本框。  
  
7.  在**“属性”**窗口中，选中**“IsReadOnly”**属性旁边的复选框。  
  
## 导航产品记录  
 添加可让用户通过**“\<”**和**“\>”**按钮来滚动产品记录的代码。  
  
#### 使用户能够导航产品记录  
  
1.  在设计器中，双击窗口图面上的**“\<”**按钮。  
  
     Visual Studio 将打开代码隐藏文件，并为 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> 事件创建新的 `backButton_Click` 事件处理程序。  
  
2.  修改 `Window_Loaded` 事件处理程序，使 `ProductViewSource`、`AdventureWorksLTDataSet` 和 `AdventureWorksLTDataSetProductTableAdapter` 在位于该方法的外部，并使它们在整个窗体中是可访问的。  仅向窗体全局声明这些项，并在 `Window_Loaded` 事件处理程序内为这些项赋值，如下所示：  
  
     [!CODE [Data_WPFDATASET#1](../CodeSnippet/VS_Snippets_ProTools/data_wpfdataset#1)]  
  
3.  将以下代码添加到 `backButton_Click` 事件处理程序中：  
  
     [!CODE [Data_WPFDATASET#2](../CodeSnippet/VS_Snippets_ProTools/data_wpfdataset#2)]  
  
4.  返回到设计器，然后双击**“\>”**按钮。  
  
5.  将以下代码添加到 `nextButton_Click` 事件处理程序中：  
  
     [!CODE [Data_WPFDATASET#3](../CodeSnippet/VS_Snippets_ProTools/data_wpfdataset#3)]  
  
## 保存对产品记录所做的更改  
 添加可让用户通过使用**“保存更改”**按钮来保存对产品所做更改的代码。  
  
#### 添加保存对产品记录所做更改的功能  
  
1.  在设计器中，双击**“保存更改”**按钮。  
  
     Visual Studio 将打开代码隐藏文件，并为 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> 事件创建新的 `saveButton_Click` 事件处理程序。  
  
2.  将以下代码添加到 `saveButton_Click` 事件处理程序中：  
  
     [!CODE [Data_WPFDATASET#4](../CodeSnippet/VS_Snippets_ProTools/data_wpfdataset#4)]  
  
    > [!NOTE]
    >  此示例使用 `TableAdapter` 的 `Save` 方法来保存更改。  这对于本演练很合适，因为本演练中只会更改一个数据表。  如果你需要保存对多个数据表所做的更改，则还可以使用 Visual Studio 利用你的数据集生成的 `TableAdapterManager` 的 `UpdateAll` 方法。  有关详细信息，请参阅[TableAdapterManager 概述](../Topic/TableAdapterManager%20Overview.md)。  
  
## 测试应用程序  
 生成并运行应用程序。  验证你是否可以查看和更新产品记录。  
  
#### 测试应用程序  
  
1.  按 F5。  
  
     这将生成并运行应用程序。  验证以下内容：  
  
    -   文本框显示具有图片的第一条产品记录的数据。  此产品的产品 ID 为 713，名称为**“Long\-Sleeve Logo Jersey, S”**。  
  
    -   可以单击**“\>”**或**“\<”**按钮来导航其他产品记录。  
  
2.  在某条产品记录中，更改**“尺寸”**值，然后单击**“保存更改”**。  
  
3.  关闭应用程序，然后在 Visual Studio 中按**“F5”**重新启动应用程序。  
  
4.  导航到已更改的产品记录，然后验证是否已保存更改。  
  
5.  关闭该应用程序。  
  
## 后续步骤  
 完成本演练后，你可以执行以下相关任务：  
  
-   了解如何使用 Visual Studio 中的**“数据源”**窗口将 WPF 控件绑定到其他类型的数据源。  有关详细信息，请参阅[演练：将 WPF 控件绑定到 WCF 数据服务](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)。  
  
-   了解如何使用 Visual Studio 中的**“数据源”**窗口显示 WPF 控件中的相关数据（即具有父子关系的数据）。  有关详细信息，请参阅[演练：在 WPF 应用程序中显示相关数据](../data-tools/walkthrough-displaying-related-data-in-a-wpf-application.md)。  
  
## 请参阅  
 [在 Visual Studio 中将 WPF 控件绑定到数据](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)   
 [如何：在 Visual Studio 中将 WPF 控件绑定到数据](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md)   
 [在 Visual Studio 中使用数据集](../data-tools/dataset-tools-in-visual-studio.md)   
 [WPF and Silverlight Designer 概述](http://msdn.microsoft.com/zh-cn/570b7a5c-0c86-4326-a371-c9b63378fc62)   
 [数据绑定概述](../Topic/Data%20Binding%20Overview.md)