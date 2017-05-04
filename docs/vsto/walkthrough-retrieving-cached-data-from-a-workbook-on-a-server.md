---
title: "演练：从服务器上的工作簿中检索缓存的数据 | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "数据 [Visual Studio 中的 Office 开发], 在服务器上进行访问"
  - "数据集 [Visual Studio 中的 Office 开发], 在服务器上进行访问"
  - "文档 [Visual Studio 中的 Office 开发], 服务器端数据访问"
  - "服务器端数据访问 [Visual Studio 中的 Office 开发]"
  - "工作簿 [Visual Studio 中的 Office 开发], 检索数据"
ms.assetid: ef6d61e5-a498-4b38-8e2e-2e80706d854b
caps.latest.revision: 35
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 34
---
# 演练：从服务器上的工作簿中检索缓存的数据
  此演练演示如何通过使用 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> 类在不启动 Excel 的情况下从 Microsoft Office Excel 工作簿中缓存的数据集中检索数据。  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 本演练阐释了以下任务：  
  
-   定义一个数据集，其中包含 AdventureWorksLT 数据库中的数据。  
  
-   在 Excel 工作簿项目和控制台应用程序项目中创建此数据集的实例。  
  
-   创建一个绑定到工作簿中的此数据集的 <xref:Microsoft.Office.Tools.Excel.ListObject>，并在打开此工作簿时用数据填充此 <xref:Microsoft.Office.Tools.Excel.ListObject>。  
  
-   将工作簿中的此数据集添加到数据缓存中。  
  
-   在不启动 Excel 的情况下，将缓存的数据集中的数据读入控制台应用程序中的数据集。  
  
 尽管此演练假设您是在开发计算机上运行代码，但此演练演示的代码可以在未安装 Excel 的服务器上使用。  
  
> [!NOTE]  
>  以下说明中的某些 Visual Studio 用户界面元素在计算机上出现的名称或位置可能会不同。  您安装的 Visual Studio 版本以及使用的设置决定了这些元素。  有关更多信息，请参见[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-cn/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
## 系统必备  
 您需要以下组件来完成本演练：  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] 或 [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)]。  
  
-   访问附有 AdventureWorksLT 示例数据库的 Microsoft SQL Server 或 Microsoft SQL Server Express 的运行中实例。  您可以从 [CodePlex 网站](http://go.microsoft.com/fwlink/?linkid=87843)下载 AdventureWorksLT 数据库。  有关附加数据库的更多信息，请参见下列主题：  
  
    -   若要使用 SQL Server Management Studio 或 SQL Server Management Studio Express 来附加数据库，请参见[如何：附加数据库 \(SQL Server Management Studio\)](http://msdn.microsoft.com/zh-cn/b4efb0ae-cfe6-4d81-a4b4-6e4916885caa)。  
  
    -   若要使用命令行来附加数据库，请参见[如何：将数据库文件附加到 SQL Server Express](http://msdn.microsoft.com/zh-cn/0f8e42b5-7a8c-4c30-8c98-7d2bdc8dcc68)。  
  
## 创建定义数据集的类库项目  
 若要在 Excel 工作簿项目和控制台应用程序中使用同一数据集，您必须在这两个项目都引用的一个单独程序集中定义此数据集。  对于此演练，请在类库项目中定义数据集。  
  
#### 创建类库项目  
  
1.  启动 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。  
  
2.  在**“文件”**菜单上指向**“新建”**，再单击**“项目”**。  
  
3.  在“模板”窗格中，展开**“Visual C\#”**或**“Visual Basic”**，然后单击**“窗口”**。  
  
4.  在项目模板列表中，选择**“类库”**。  
  
5.  在**“名称”**框中键入 **AdventureWorksDataSet**。  
  
6.  单击**“浏览”**，导航至 %UserProfile%\\My Documents（对于 Windows XP 及更低版本）或 %UserProfile%\\Documents（对于 Windows Vista）文件夹，然后单击**“选择文件夹”**。  
  
7.  在**“新建项目”**对话框中，确保**“创建解决方案的目录”**复选框未选中。  
  
8.  单击**“确定”**。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 会将**“AdventureWorksDataSet”**项目添加到**“解决方案资源管理器”**中，并打开**“Class1.cs”**或**“Class1.vb”**代码文件。  
  
9. 在**“解决方案资源管理器”**中，右击**“Class1.cs”**或**“Class1.vb”**，然后单击**“删除”**。  此演练不需要此文件。  
  
## 在类库项目中定义数据集  
 定义一个类型化数据集，其中包含 SQL Server 2005 附带的 AdventureWorksLT 数据库中的数据。  在此演练后面的部分中，您将从一个 Excel 工作簿项目和一个控制台应用程序项目中引用此数据集。  
  
 此数据集是一个类型化数据集，表示 AdventureWorksLT 数据库的 Product 表中的数据。  有关类型化的数据集的更多信息，请参见 [在 Visual Studio 中使用数据集](../data-tools/dataset-tools-in-visual-studio.md)。  
  
#### 在类库项目中定义类型化数据集  
  
1.  在**“解决方案资源管理器”**中，单击**“AdventureWorksDataSet”**项目。  
  
2.  如果 **数据源** 窗口不可见，则显示那么，在菜单栏上，选择 **查看**，**其他窗口**，**数据源**。  
  
3.  选择 **添加新数据源** 开始 **数据源配置向导**。  
  
4.  单击**“数据库”**，然后单击**“下一步”**。  
  
5.  如果已与 AdventureWorksLT 数据库建立连接，请选择此连接，然后单击**“下一步”**。  
  
     否则，单击**“新建连接”**，然后使用**“添加连接”**对话框创建新连接。  有关更多信息，请参见[如何：连接到数据库中的数据](~/data-tools/how-to-connect-to-data-in-a-database.md)。  
  
6.  在**“                  ”**页中，单击**“   ”**。  
  
7.  在**“选择数据库对象”**页中，展开**“表”**，然后选择**“Product \(SalesLT\)”**。  
  
8.  单击“完成”。  
  
     AdventureWorksLTDataSet.xsd 文件即会添加到 **AdventureWorksDataSet** 项目中。  此文件定义以下各项：  
  
    -   一个名为 `AdventureWorksLTDataSet` 的类型化数据集。  此数据集表示 AdventureWorksLT 数据库中的 Product 表的内容。  
  
    -   一个名为 `ProductTableAdapter` 的 TableAdapter。  此 TableAdapter 可用来在 `AdventureWorksLTDataSet` 中读取和写入数据。  有关更多信息，请参见[TableAdapter 概述](/visual-studio/data-tools/tableadapter-overview)。  
  
     在本演练后面的部分中，您将使用这两个对象。  
  
9. 在**“解决方案资源管理器”**中右击**“AdventureWorksDataSet”**，再单击**“生成”**。  
  
     验证项目已生成且未发生错误。  
  
## 创建 Excel 工作簿项目  
 为数据的接口创建一个 Excel 工作簿项目。  在此演练后面的部分中，您将创建一个显示这些数据的 <xref:Microsoft.Office.Tools.Excel.ListObject>，并且您将向此工作簿中的数据缓存添加此数据集的实例。  
  
#### 创建 Excel 工作簿项目  
  
1.  在**“解决方案资源管理器”**中右击**“AdventureWorksDataSet”**解决方案，指向**“添加”**，再单击**“新建项目”**。  
  
2.  在模板窗格中，展开 **Visual C\#** 或  **Visual Basic**，然后展开 **Office\/SharePoint**。  
  
3.  在展开的 **Office\/SharePoint** 节点下，选择 **Office 外接程序** 节点。  
  
4.  在项目模板列表中，选择 **Excel 2010 工作簿** 或 **Excel 2013 工作簿** 项目。  
  
5.  在**“名称”**框中键入 **AdventureWorksReport**。  请勿修改位置。  
  
6.  单击**“确定”**。  
  
     会打开**“Visual Studio Tools for Office 项目向导”**。  
  
7.  确保已选择**“创建新文档”**，然后单击**“确定”**。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 将在设计器中打开 **AdventureWorksReport** 工作簿，并将**“AdventureWorksReport”**项目添加到**“解决方案资源管理器”**。  
  
## 在 Excel 工作簿项目中将此数据集添加到数据源  
 必须先在 Excel 工作簿项目中将此数据集添加到数据源，然后才能在 Excel 工作簿中显示此数据集。  
  
#### 在 Excel 工作簿项目中将此数据集添加到数据源  
  
1.  在**“解决方案资源管理器”**中，双击**“AdventureWorksReport”**项目下的**“Sheet1.cs”**或**“Sheet1.vb”**。  
  
     工作簿即会在设计器中打开。  
  
2.  在**“数据”**菜单上，单击**“添加新数据源”**。  
  
     **“数据源配置向导”**打开。  
  
3.  单击**“对象”**，然后单击**“下一步”**。  
  
4.  在**“选择希望绑定到的对象”**页中，单击**“添加引用”**。  
  
5.  在**“项目”**选项卡上，单击**“AdventureWorksDataSet”**，再单击**“确定”**。  
  
6.  在**“AdventureWorksDataSet”**程序集的**“AdventureWorksDataSet”**命名空间下，单击**“AdventureWorksLTDataSet”**，然后单击**“完成”**。  
  
     **“数据源”**窗口即会打开，并且**“AdventureWorksLTDataSet”**会添加到数据源列表中。  
  
## 创建绑定到此数据集的实例的 ListObject  
 若要在工作簿中显示此数据集，请创建一个绑定到此数据集的实例的 <xref:Microsoft.Office.Tools.Excel.ListObject>。  有关将控件绑定到数据的更多信息，请参见[将数据绑定到 Office 解决方案中的控件](../vsto/binding-data-to-controls-in-office-solutions.md)。  
  
#### 创建绑定到此数据集的实例的 ListObject  
  
1.  在**“数据源”**窗口中，展开**“AdventureWorksDataSet”**下的**“AdventureWorksLTDataSet”**节点。  
  
2.  选择**“Product”**节点，单击出现的下拉箭头，然后在下拉列表中选择**“ListObject”**。  
  
     如果未出现下拉箭头，请确认是否在设计器中打开了工作簿。  
  
3.  将**“Product”**表拖到 A1 单元格中。  
  
     这样就在工作簿中创建了一个名为 `productListObject` 的 <xref:Microsoft.Office.Tools.Excel.ListObject> 控件，此控件的起始单元格为 A1。  同时，会将一个名为 `adventureWorksLTDataSet` 的数据集对象和一个名为 `productBindingSource` 的 <xref:System.Windows.Forms.BindingSource> 添加到项目中。  此 <xref:Microsoft.Office.Tools.Excel.ListObject> 绑定到 <xref:System.Windows.Forms.BindingSource>，而后者又绑定到此数据集对象。  
  
## 将此数据集添加到数据缓存中  
 若要使 Excel 工作簿项目外部的代码能够访问工作簿中的此数据集，必须将此数据集添加到数据缓存中。  有关数据缓存的更多信息，请参见[文档级自定义项中的缓存数据](../vsto/cached-data-in-document-level-customizations.md)和[缓存数据](../vsto/caching-data.md)。  
  
#### 将此数据集添加到数据缓存中  
  
1.  在设计器中，单击**“adventureWorksLTDataSet”**。  
  
2.  在**“属性”**窗口中，将**“Modifiers”**属性设置为**“Public”**。  
  
3.  将**“CacheInDocument”**属性设置为**“True”**。  
  
## 初始化工作簿中的此数据集  
 必须先用数据填充缓存的数据集，然后才能通过使用控制台应用程序从缓存的数据集中检索数据。  
  
#### 初始化工作簿中的此数据集  
  
1.  在**“解决方案资源管理器”**中，右击**“Sheet1.cs”**或**“Sheet1.vb”**文件，再单击**“查看代码”**。  
  
2.  用下面的代码替换 `Sheet1_Startup` 事件处理程序。  如果缓存的数据集当前是空的，则此代码使用在 **AdventureWorksDataSet** 项目中定义的 `ProductTableAdapter` 类的一个实例在此缓存的数据集中填充数据。  
  
     [!code-csharp[Trin_CachedDataWalkthroughs#8](../snippets/csharp/VS_Snippets_OfficeSP/Trin_CachedDataWalkthroughs/CS/AdventureWorksReport/Sheet1.cs#8)]
     [!code-vb[Trin_CachedDataWalkthroughs#8](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_CachedDataWalkthroughs/VB/AdventureWorksReport/Sheet1.vb#8)]  
  
## 检查点  
 生成并运行此 Excel 工作簿项目，确保它在编译和运行时不出错。  此操作还会填充缓存的数据集并将数据保存在工作簿中。  
  
#### 生成并运行此项目  
  
1.  在**“解决方案资源管理器”**中右击**“AdventureWorksReport”**项目，选择**“调试”**，然后单击**“启动新实例”**。  
  
     即会生成此项目，并在 Excel 中打开此工作簿。  确认以下事项：  
  
    -   <xref:Microsoft.Office.Tools.Excel.ListObject> 中填充了数据。  
  
    -   <xref:Microsoft.Office.Tools.Excel.ListObject> 第一行的**“ListPrice”**列中的值为 1431.5。  在此演练后面的部分中，您将使用控制台应用程序来修改**“ListPrice”**列中的值。  
  
2.  保存工作簿。  请勿修改工作簿的文件名和位置。  
  
3.  关闭 Excel。  
  
## 创建控制台应用程序项目  
 创建一个控制台应用程序项目，用以修改工作簿中缓存的数据集中的数据。  
  
#### 创建控制台应用程序项目  
  
1.  在**“解决方案资源管理器”**中右击**“AdventureWorksDataSet”**解决方案，指向**“添加”**，再单击**“新建项目”**。  
  
2.  在**“项目类型”**窗格中，展开**“Visual C\#”**或**“Visual Basic”**，然后单击**“Windows”**。  
  
3.  在**“模板”**窗格中选择**“控制台应用程序”**。  
  
4.  在**“名称”**框中键入 **DataReader**。  请勿修改位置。  
  
5.  单击**“确定”**。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 即会将**“DataReader”**项目添加到**“解决方案资源管理器”**中，并打开**“Program.cs”**或**“Module1.vb”**代码文件。  
  
## 通过使用控制台应用程序从缓存的数据集中检索数据  
 在控制台应用程序中使用 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> 类将数据读入本地 `AdventureWorksLTDataSet` 对象。  为了确认本地数据集已使用来自缓存的数据集中的数据进行了初始化，应用程序会显示本地数据集中的行数。  
  
#### 从缓存的数据集中检索数据  
  
1.  在**“解决方案资源管理器”**中右击**“DataReader”**项目，然后单击**“添加引用”**。  
  
2.  在 **.NET** 选项，选择 Microsoft.VisualStudio.Tools.Applications.ServerDocument。  
  
3.  单击**“确定”**。  
  
4.  在**“解决方案资源管理器”**中右击**“DataReader”**项目，然后单击**“添加引用”**。  
  
5.  在**“项目”**选项卡上，选择**“AdventureWorksDataSet”**，然后单击**“确定”**。  
  
6.  在代码编辑器中打开 Program.cs 或 Module1.vb 文件。  
  
7.  将下面的 **using**（对于 C\#）或 **Imports**（对于 Visual Basic）语句添加到相应代码文件的顶部。  
  
     [!code-csharp[Trin_CachedDataWalkthroughs#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_CachedDataWalkthroughs/CS/DataWriter/Program.cs#1)]
     [!code-vb[Trin_CachedDataWalkthroughs#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_CachedDataWalkthroughs/VB/DataWriter/Module1.vb#1)]  
  
8.  将以下代码添加到 `Main` 方法中。  此代码声明了以下对象：  
  
    -   在 **AdventureWorksDataSet** 项目中定义的 `AdventureWorksLTDataSet` 类型的一个实例。  
  
    -   **AdventureWorksReport** 项目的生成文件夹中 AdventureWorksReport 工作簿的路径。  
  
    -   一个用于访问工作簿中数据缓存的 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> 对象。  
  
        > [!NOTE]  
        >  下面的代码假定工作簿是使用 .xlsx 扩展名保存的。  如果您项目中的工作簿具有不同的扩展名，请在必要时修改路径。  
  
     [!code-csharp[Trin_CachedDataWalkthroughs#10](../snippets/csharp/VS_Snippets_OfficeSP/Trin_CachedDataWalkthroughs/CS/DataWriter/Program.cs#10)]
     [!code-vb[Trin_CachedDataWalkthroughs#10](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_CachedDataWalkthroughs/VB/DataWriter/Module1.vb#10)]  
  
9. 将下面的代码添加到 `Main` 方法中，接在上一步添加的代码后面。  这段代码执行下列任务：  
  
    -   使用 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> 类的 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> 属性访问工作簿中缓存的数据集。  
  
    -   将缓存的数据集中的数据读入本地数据集。  
  
    -   显示本地数据集中的行数，以确认本地数据集中包含数据。  
  
     [!code-csharp[Trin_CachedDataWalkthroughs#11](../snippets/csharp/VS_Snippets_OfficeSP/Trin_CachedDataWalkthroughs/CS/DataWriter/Program.cs#11)]
     [!code-vb[Trin_CachedDataWalkthroughs#11](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_CachedDataWalkthroughs/VB/DataWriter/Module1.vb#11)]  
  
10. 在**“生成”**菜单上，单击**“生成 DataReader”**。  
  
## 测试项目  
 当您运行此控制台应用程序时，它会显示本地数据集中的行数。  
  
#### 测试此工作簿  
  
1.  在**“解决方案资源管理器”**中右击**“DataReader”**项目，指向**“调试”**，然后单击**“启动新实例”**。  
  
     验证此应用程序是否报告本地数据集具有 295 行。  
  
2.  按 Enter 可关闭应用程序。  
  
## 后续步骤  
 您可以从以下主题中了解到有关使用缓存的数据的更多内容：  
  
-   在不启动 Excel 的情况下更改缓存的数据集中的数据。  有关更多信息，请参见[演练：更改服务器上的工作簿中的缓存数据](../vsto/walkthrough-changing-cached-data-in-a-workbook-on-a-server.md)。  
  
## 请参阅  
 [演练：将数据插入到服务器上的工作簿中](../vsto/walkthrough-inserting-data-into-a-workbook-on-a-server.md)   
 [演练：更改服务器上的工作簿中的缓存数据](../vsto/walkthrough-changing-cached-data-in-a-workbook-on-a-server.md)   
 [连接到 Windows 窗体应用程序中的数据](/visual-studio/data-tools/connecting-to-data-in-windows-forms-applications)  
  
  