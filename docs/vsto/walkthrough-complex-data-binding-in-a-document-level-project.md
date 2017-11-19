---
title: "演练： 文档级项目中的复杂数据绑定 |Microsoft 文档"
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
- complex data [Office development in Visual Studio]
- multiple column data binding [Office development in Visual Studio]
- data binding [Office development in Visual Studio], multiple columns
ms.assetid: 32ffad3d-fba4-476a-99b8-ef440434f4e1
caps.latest.revision: "50"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: dff7896b24508891a62ad3a0760880ed6a68a65a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-complex-data-binding-in-a-document-level-project"></a>演练：文档级项目中的复杂数据绑定
  本演练演示文档级项目中的复杂数据绑定的基础知识。 你可以将 Microsoft Office Excel 工作表中的多个单元格绑定到 Northwind SQL Server 数据库中的字段。  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 本演练阐释了以下任务：  
  
-   将数据源添加到工作簿项目。  
  
-   将数据绑定控件添加到工作表。  
  
-   将数据更改保存回数据库。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>先决条件  
 你需要以下组件来完成本演练：  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] 或 [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)]。  
  
-   到 Northwind SQL Server 示例数据库的服务器的访问。  
  
-   读取和写入到 SQL Server 数据库的权限。  
  
## <a name="creating-a-new-project"></a>创建新项目  
 第一步是创建 Excel 工作簿项目。  
  
#### <a name="to-create-a-new-project"></a>创建新项目  
  
1.  使用名称创建的 Excel 工作簿项目**我的复杂数据绑定**。 在向导中，选择**创建新文档**。  
  
     有关详细信息，请参阅 [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)。  
  
     Visual Studio 将在设计器中打开新的 Excel 工作簿并将添加**我的复杂数据绑定**项目合并为**解决方案资源管理器**。  
  
## <a name="creating-the-data-source"></a>创建数据源  
 使用 **“数据源”** 窗口将类型化数据集添加到项目中。  
  
#### <a name="to-create-the-data-source"></a>创建数据源  
  
1.  如果 **“数据源”** 窗口不可见，则在菜单栏上，通过选择 **“查看”**， **“其他窗口”**、 **“数据源”**显示它。  
  
2.  选择 **“添加新数据源”** 以启动 **“数据源配置向导”**。  
  
3.  选择**数据库**，然后单击**下一步**。  
  
4.  选择一个数据连接到 Northwind 示例 SQL Server 数据库，或通过添加新连接**新连接**按钮。  
  
5.  选择或创建连接后，单击**下一步**。  
  
6.  如果选中，将连接另存的选项，然后单击清除**下一步**。  
  
7.  展开**表**中的节点**数据库对象**窗口。  
  
8.  选中的复选框旁边**员工**表。  
  
9. 单击 **“完成”**。  
  
 该向导将添加**员工**表**数据源**窗口。 它还将类型化数据集添加到项目中的可见**解决方案资源管理器**。  
  
## <a name="adding-controls-to-the-worksheet"></a>向工作表添加控件  
 工作表将显示**员工**表打开工作簿时。 用户将能够对数据进行更改，然后通过单击的按钮将这些更改保存回数据库。  
  
 若要自动绑定到表的工作表，你可以添加<xref:Microsoft.Office.Tools.Excel.ListObject>到从工作表中的控件**数据源**窗口。 若要为用户提供的选项以保存更改，将添加<xref:System.Windows.Forms.Button>控件从**工具箱**。  
  
#### <a name="to-add-a-list-object"></a>若要添加的 list 对象  
  
1.  验证**我复杂数据 Binding.xlsx**工作簿是在 Visual Studio 设计器中，打开与**Sheet1**显示。  
  
2.  打开**数据源**窗口，然后选择**员工**节点。  
  
3.  单击显示的下拉箭头。  
  
4.  选择**ListObject**下拉列表中。  
  
5.  拖动**员工**表添加到单元格**A6**。  
  
     A<xref:Microsoft.Office.Tools.Excel.ListObject>控件名为`EmployeesListObject`单元格中创建**A6**。 同时，<xref:System.Windows.Forms.BindingSource>名为`EmployeesBindingSource`，一个表适配器和一个<xref:System.Data.DataSet>实例添加到项目。 该控件绑定到<xref:System.Windows.Forms.BindingSource>，后者又绑定到<xref:System.Data.DataSet>实例。  
  
#### <a name="to-add-a-button"></a>若要添加一个按钮  
  
1.  从**公共控件**选项卡**工具箱**，添加<xref:System.Windows.Forms.Button>控件添加到单元格**A4**工作表。  
  
 下一步是向按钮添加文本时打开工作表。  
  
## <a name="initializing-the-control"></a>初始化控件  
 将文本添加到中的按钮<xref:Microsoft.Office.Tools.Excel.Worksheet.Startup>事件处理程序。  
  
#### <a name="to-initialize-the-control"></a>若要初始化的控件  
  
1.  在**解决方案资源管理器**，右键单击**Sheet1.vb**或**Sheet1.cs**，然后单击**查看代码**快捷菜单上。  
  
2.  以下代码添加到`Sheet1_Startup`方法以设置 b 的文本`utton`。  
  
     [!code-csharp[Trin_VstcoreDataExcel#8](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet3.cs#8)]
     [!code-vb[Trin_VstcoreDataExcel#8](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet3.vb#8)]  
  
3.  仅适用于 C#，添加事件处理程序<xref:System.Windows.Forms.Control.Click>事件`Sheet1_Startup`方法。  
  
     [!code-csharp[Trin_VstcoreDataExcel#9](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet3.cs#9)]  
  
 现在添加代码以处理<xref:System.Windows.Forms.Control.Click>该按钮的事件。  
  
## <a name="saving-changes-to-the-database"></a>将更改保存到数据库  
 对已进行了任何更改数据只存在于本地的数据集之前它们显式保存回数据库。  
  
#### <a name="to-save-changes-to-the-database"></a>若要将更改保存到数据库  
  
1.  添加事件处理程序<xref:System.Windows.Forms.Control.Click>b 的事件`utton`，然后添加以下代码来提交回数据库做数据集中的所有更改。  
  
     [!code-csharp[Trin_VstcoreDataExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet3.cs#10)]
     [!code-vb[Trin_VstcoreDataExcel#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet3.vb#10)]  
  
## <a name="testing-the-application"></a>测试应用程序  
 现在，你可以测试你的工作簿以验证数据显示按预期方式运行并且你可以处理列表对象中的数据。  
  
#### <a name="to-test-the-data-binding"></a>若要测试的数据绑定  
  
-   按 F5。  
  
     验证，当工作簿打开后，则列表对象中的数据填充**员工**表。  
  
#### <a name="to-modify-data"></a>若要修改数据  
  
1.  单击单元格**B7**，其中应包含名称**李小明**。  
  
2.  键入的名称**Anderson**，然后按 ENTER。  
  
#### <a name="to-modify-a-column-header"></a>若要修改列标题  
  
1.  单击包含列标题的单元格**LastName**。  
  
2.  类型**姓氏**，包括两个词，之间留一个空格，然后按 enter 键。  
  
#### <a name="to-save-data"></a>若要保存数据  
  
1.  单击**保存**工作表上。  
  
2.  退出 Excel。 单击**否**当系统提示保存所做的更改。  
  
3.  按 F5 再次运行项目。  
  
     使用中的数据填充的列表对象**员工**表。  
  
4.  请注意，在单元格中的名称**B7**仍**Anderson**，这是的数据更改您所做并保存回数据库。 列标题**LastName**已改回其原始格式没有空格，因为列标头未绑定到数据库并且未保存到工作表中所做的更改。  
  
#### <a name="to-add-new-rows"></a>若要添加新行  
  
1.  选择的列表对象中的单元格。  
  
     新行显示在列表中，有一个星号的底部 (**\***) 的新行的第一个单元格中。  
  
2.  空的行中添加以下信息。  
  
    |EmployeeID|LastName|FirstName|标题|  
    |----------------|--------------|---------------|-----------|  
    |10|Ito|Shu|销售经理|  
  
#### <a name="to-delete-rows"></a>若要删除的行  
  
-   右击的数字 16 （行 16） 上最左侧工作表中，并依次**删除**。  
  
#### <a name="to-sort-the-rows-in-the-list"></a>若要在列表中的行进行排序  
  
1.  选择列表中的单元格。  
  
     箭头按钮显示在每个列标题。  
  
2.  单击箭头按钮在**姓氏**列标题。  
  
3.  单击**按升序排序**。  
  
     行按姓氏和名字按字母顺序排序。  
  
#### <a name="to-filter-information"></a>若要筛选器信息  
  
1.  选择列表中的单元格。  
  
2.  单击箭头按钮在**标题**列标题。  
  
3.  单击**销售代表**。  
  
     列表将显示包含的行**销售代表**中**标题**列。  
  
4.  单击箭头按钮在**标题**再次列标题。  
  
5.  单击**（全部）**。  
  
     筛选被删除，所有行都显示。  
  
## <a name="next-steps"></a>后续步骤  
 本演练演示在数据库中的表绑定到列表对象的基础知识。 以下是接下来可能要执行的一些任务：  
  
-   缓存数据，以便可以脱机使用。 有关详细信息，请参阅[如何： 缓存数据以脱机使用，或在服务器上](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)。  
  
-   部署解决方案。 有关详细信息，请参阅[部署 Office 解决方案](../vsto/deploying-an-office-solution.md)。  
  
-   创建一个字段和表之间的主/从关系。 有关详细信息，请参阅[演练： 创建 Master 详细信息的关系使用缓存数据集](../vsto/walkthrough-creating-a-master-detail-relation-using-a-cached-dataset.md)。  
  
## <a name="see-also"></a>另请参阅  
 [将数据绑定到 Office 解决方案中的控件](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Office 解决方案中的数据](../vsto/data-in-office-solutions.md)   
 [演练：文档级项目中的简单数据绑定](../vsto/walkthrough-simple-data-binding-in-a-document-level-project.md)  
  
  