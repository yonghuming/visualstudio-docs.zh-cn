---
title: "演练： 简单的数据绑定，在 VSTO 外接程序项目 |Microsoft 文档"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Office development in Visual Studio], binding data
- data binding [Office development in Visual Studio], Word
- data [Office development in Visual Studio], simple binding data
ms.assetid: b248d194-a8b1-4f87-94c4-24e940eea1fd
caps.latest.revision: "39"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: fe1626a818a6442e56e8934b142a31b65f83c0a7
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-simple-data-binding-in-vsto-add-in-project"></a>演练：VSTO 外接程序项目中的简单数据绑定
  可以将数据绑定到 VSTO 外接程序项目中的宿主控件和 Windows 窗体控件。 本演练演示如何在运行时向 Microsoft Office Word 文档中添加控件并将控件绑定到数据。  
  
 [!INCLUDE[appliesto_wdallapp](../vsto/includes/appliesto-wdallapp-md.md)]  
  
 本演练阐释了以下任务：  
  
-   在运行时向文档中添加 <xref:Microsoft.Office.Tools.Word.ContentControl> 。  
  
-   创建用于将该控件连接到某个数据集实例的 <xref:System.Windows.Forms.BindingSource> 。  
  
-   使用户可以滚动浏览记录以及在控件中查看记录。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>先决条件  
 你需要以下组件来完成本演练：  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] 或 [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)]。  
  
-   对附加了 `AdventureWorksLT` 示例数据库且正在运行的 SQL Server 2005 或 SQL Server 2005 Express 实例的访问权限。 你可以从 `AdventureWorksLT` CodePlex 网站 [下载](http://go.microsoft.com/fwlink/?LinkId=115611)数据库。 有关附加数据库的详细信息，请参阅下列主题：  
  
    -   若要使用 SQL Server Management Studio 或 SQL Server Management Studio Express 来附加数据库，请参阅 [如何：附加数据库 (SQL Server Management Studio)](http://msdn.microsoft.com/en-us/b4efb0ae-cfe6-4d81-a4b4-6e4916885caa)。  
  
    -   若要使用命令行来附加数据库，请参阅 [如何：将数据库文件附加到 SQL Server Express](http://msdn.microsoft.com/en-us/0f8e42b5-7a8c-4c30-8c98-7d2bdc8dcc68)。  
  
## <a name="creating-a-new-project"></a>创建新项目  
 第一步是创建 Word VSTO 外接程序项目。  
  
#### <a name="to-create-a-new-project"></a>创建新项目  
  
1.  使用 Visual Basic 或 C# 创建一个名为“从数据库填充文档” 的 Word VSTO 外接程序项目。  
  
     有关详细信息，请参阅 [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)。  
  
     Visual Studio 会打开 ThisAddIn.vb 或 ThisAddIn.cs 文件，并将“从数据库填充文档”  项目添加到“解决方案资源管理器” 中。  
  
2.  如果项目面向 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或 [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]，则添加对 Microsoft.Office.Tools.Word.v4.0.Utilities.dll 程序集的引用。 在本演练后面的部分中，需要此引用才能以编程方式向文档中添加 Windows 窗体控件。  
  
## <a name="creating-a-data-source"></a>创建数据源  
 使用 **“数据源”** 窗口将类型化数据集添加到项目中。  
  
#### <a name="to-add-a-typed-dataset-to-the-project"></a>向项目中添加类型化数据集  
  
1.  如果 **“数据源”** 窗口不可见，则在菜单栏上，通过选择 **“查看”**， **“其他窗口”**、 **“数据源”**显示它。  
  
2.  选择 **“添加新数据源”** 以启动 **“数据源配置向导”**。  
  
3.  单击“数据库” ，然后单击“下一步” 。  
  
4.  如果已与 `AdventureWorksLT` 数据库建立连接，请选择此连接，然后单击“下一步” 。  
  
     否则，单击“新建连接” ，然后使用“添加连接”  对话框创建新连接。 有关详细信息，请参阅[添加新连接](../data-tools/add-new-connections.md)。  
  
5.  在“将连接字符串保存到应用程序配置文件中”  页中，单击“下一步” 。  
  
6.  在“选择数据库对象”  页中展开“表”  ，再选择“Customer (SalesLT)” 。  
  
7.  单击 **“完成”**。  
  
     AdventureWorksLTDataSet.xsd 文件即会添加到“解决方案资源管理器” 中。 此文件定义以下各项：  
  
    -   一个名为 `AdventureWorksLTDataSet`的类型化数据集。 此数据集表示 AdventureWorksLT 数据库中的“Customer (SalesLT)”  表的内容。  
  
    -   名为 TableAdapter `CustomerTableAdapter`。 此 TableAdapter 可用于读取和写入数据中`AdventureWorksLTDataSet`。 有关详细信息，请参阅 [TableAdapter Overview](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview)。  
  
     在本演练后面的部分中，你将使用这两个对象。  
  
## <a name="creating-controls-and-binding-controls-to-data"></a>创建控件并将控件绑定到数据  
 在本演练中，用于查看数据库记录的界面非常简单，它是直接在文档内部创建的。 一个 <xref:Microsoft.Office.Tools.Word.ContentControl> 一次显示一条数据库记录，两个 <xref:Microsoft.Office.Tools.Word.Controls.Button> 控件允许你以前后滚动的方式查看记录。 该内容控件使用 <xref:System.Windows.Forms.BindingSource> 来连接到数据库。  
  
 有关将控件绑定到数据的详细信息，请参阅 [Binding Data to Controls in Office Solutions](../vsto/binding-data-to-controls-in-office-solutions.md)。  
  
#### <a name="to-create-the-interface-in-the-document"></a>在文档中创建界面  
  
1.  在 `ThisAddIn` 类中声明下列控件，以显示和滚动查看 `Customer` 数据库的 `AdventureWorksLTDataSet` 表。  
  
     [!code-vb[Trin_WordAddInDatabase#1](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#1)]
     [!code-csharp[Trin_WordAddInDatabase#1](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#1)]  
  
2.  在 `ThisAddIn_Startup` 方法中添加下面的代码，以便初始化数据集并使用 `AdventureWorksLTDataSet` 数据库中的信息填充数据集。  
  
     [!code-vb[Trin_WordAddInDatabase#2](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#2)]
     [!code-csharp[Trin_WordAddInDatabase#2](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#2)]  
  
3.  将以下代码添加到 `ThisAddIn_Startup` 方法中。 这会生成一个扩展文档的宿主项。 有关详细信息，请参阅 [Extending Word Documents and Excel Workbooks in VSTO Add-ins at Run Time](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)。  
  
     [!code-vb[Trin_WordAddInDatabase#3](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#3)]
     [!code-csharp[Trin_WordAddInDatabase#3](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#3)]  
  
4.  在文档开始处定义多个范围。 这些范围标识用于插入文本和放置控件的位置。  
  
     [!code-vb[Trin_WordAddInDatabase#4](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#4)]
     [!code-csharp[Trin_WordAddInDatabase#4](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#4)]  
  
5.  将界面控件添加到前面定义的范围内。  
  
     [!code-vb[Trin_WordAddInDatabase#5](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#5)]
     [!code-csharp[Trin_WordAddInDatabase#5](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#5)]  
  
6.  使用 `AdventureWorksLTDataSet` 将内容控件绑定到 <xref:System.Windows.Forms.BindingSource>。 对于 C# 开发人员，为 <xref:Microsoft.Office.Tools.Word.Controls.Button> 控件添加两个事件处理程序。  
  
     [!code-vb[Trin_WordAddInDatabase#6](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#6)]
     [!code-csharp[Trin_WordAddInDatabase#6](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#6)]  
  
7.  添加下面的代码，以浏览数据库记录。  
  
     [!code-vb[Trin_WordAddInDatabase#7](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#7)]
     [!code-csharp[Trin_WordAddInDatabase#7](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#7)]  
  
## <a name="testing-the-add-in"></a>测试外接程序  
 打开 Word 后，内容控件随即显示 `AdventureWorksLTDataSet` 数据集中的数据。 通过单击“下一条”  和“上一条”  按钮来滚动查看数据库记录。  
  
#### <a name="to-test-the-vsto-add-in"></a>若要测试 VSTO 外接程序  
  
1.  按 F5 。  
  
     即会创建一个名为 `customerContentControl` 的内容控件，并向该控件填充数据。 同时，向项目添加了一个名为 `adventureWorksLTDataSet` 的数据集对象和一个名为 <xref:System.Windows.Forms.BindingSource> 的 `customerBindingSource` 。 已将 <xref:Microsoft.Office.Tools.Word.ContentControl> 绑定到 <xref:System.Windows.Forms.BindingSource>，而后者又绑定到该数据集对象。  
  
2.  单击“下一条”  和“上一条”  按钮来滚动查看数据库记录。  
  
## <a name="see-also"></a>另请参阅  
 [Office 解决方案中的数据](../vsto/data-in-office-solutions.md)   
 [将数据绑定到 Office 解决方案中的控件](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [如何： 用数据库中的数据填充工作表](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)   
 [如何： 用数据库中的数据填充文档](../vsto/how-to-populate-documents-with-data-from-a-database.md)   
 [如何： 用服务中的数据填充文档](../vsto/how-to-populate-documents-with-data-from-services.md)   
 [如何： 用对象中的数据填充文档](../vsto/how-to-populate-documents-with-data-from-objects.md)   
 [如何： 在工作表中的数据库记录滚动](../vsto/how-to-scroll-through-database-records-in-a-worksheet.md)   
 [如何： 使用主机控件中的数据更新数据源](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)   
 [演练： 文档级项目中的简单数据绑定](../vsto/walkthrough-simple-data-binding-in-a-document-level-project.md)   
 [演练： 文档级项目中的复杂数据绑定](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md)   
 [使用 Office 解决方案概述中的本地数据库文件](../vsto/using-local-database-files-in-office-solutions-overview.md)   
 [添加新数据源](/visualstudio/data-tools/add-new-data-sources)   
 [在 Visual Studio 中将 Windows 窗体控件绑定到数据](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [如何： 用对象中的数据填充文档](../vsto/how-to-populate-documents-with-data-from-objects.md)   
 [如何： 使用主机控件中的数据更新数据源](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)   
 [使用 Office 解决方案概述中的本地数据库文件](../vsto/using-local-database-files-in-office-solutions-overview.md)   
 [连接到 Windows 窗体应用程序中的数据](/visualstudio/data-tools/connecting-to-data-in-windows-forms-applications)   
 [BindingSource 组件概述](/dotnet/framework/winforms/controls/bindingsource-component-overview)  
  
  