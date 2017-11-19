---
title: "演练： 创建使用缓存的数据集 Master 从关系 |Microsoft 文档"
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
- master-detail tables [Office development in Visual Studio], walkthroughs
- data caching [Office development in Visual Studio], Master/Detail Relation
ms.assetid: 419f4e07-c67f-4fc9-973a-bc794f349ac3
caps.latest.revision: "41"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b392b4de0288478c73fba8cecd88be1f701cd5ae
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-creating-a-master-detail-relation-using-a-cached-dataset"></a>演练： 创建使用缓存的数据集 Master 从关系
  本演练演示在工作表上创建主/从关系以及缓存数据，以便可以脱机使用该解决方案。  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 在本演练中，你将学会如何执行以下任务：  
  
-   将控件添加到工作表。  
  
-   设置在工作表中缓存的数据集。  
  
-   添加代码以启用滚动记录。  
  
-   测试你的项目。  
  
> [!NOTE]  
>  以下说明中的某些 Visual Studio 用户界面元素在计算机上出现的名称或位置可能会不同。 这些元素取决于你所使用的 Visual Studio 版本和你所使用的设置。 有关详细信息，请参阅[个性化设置 Visual Studio IDE](../ide/personalizing-the-visual-studio-ide.md)。  
  
## <a name="prerequisites"></a>先决条件  
 你需要以下组件来完成本演练：  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] 或 [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)]。  
  
-   包含到 Northwind SQL Server 示例数据库的访问。 数据库可以为你的开发计算机上或在服务器上。  
  
-   读取和写入到 SQL Server 数据库的权限。  
  
## <a name="creating-a-new-project"></a>创建新项目  
 在此步骤中，你将创建的 Excel 工作簿项目。  
  
#### <a name="to-create-a-new-project"></a>创建新项目  
  
1.  使用名称创建的 Excel 工作簿项目**我主-从**，使用 Visual Basic 或 C#。 请确保**创建新文档**选择。 有关详细信息，请参阅 [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)。  
  
 Visual Studio 将在设计器中打开新的 Excel 工作簿并将添加**我主-从**项目合并为**解决方案资源管理器**。  
  
## <a name="creating-the-data-source"></a>创建数据源  
 使用 **“数据源”** 窗口将类型化数据集添加到项目中。  
  
#### <a name="to-create-the-data-source"></a>创建数据源  
  
1.  如果 **“数据源”** 窗口不可见，则在菜单栏上，通过选择 **“查看”**， **“其他窗口”**、 **“数据源”**显示它。  
  
2.  选择 **“添加新数据源”** 以启动 **“数据源配置向导”**。  
  
3.  选择**数据库**，然后单击**下一步**。  
  
4.  选择一个数据连接到 Northwind 示例 SQL Server 数据库，或通过添加新连接**新连接**按钮。  
  
5.  选择或创建连接后, 单击**下一步**。  
  
6.  如果选中，将连接另存的选项，然后单击清除**下一步**。  
  
7.  展开**表**中的节点**数据库对象**窗口。  
  
8.  选择**订单**表和**订单详细信息**表。  
  
9. 单击 **“完成”**。  
  
 该向导将添加到两个表**数据源**窗口。 它还将类型化数据集添加到项目中的可见**解决方案资源管理器**。  
  
## <a name="adding-controls-to-the-worksheet"></a>向工作表添加控件  
 在此步骤中，将向第一个工作表中添加命名的范围、 列表对象和两个按钮。 首先，添加命名的范围并从列表对象**数据源**窗口，从而使它们自动绑定到数据源。 接下来，添加从按钮**工具箱**。  
  
#### <a name="to-add-a-named-range-and-a-list-object"></a>若要添加的命名的区域和列表对象  
  
1.  验证**我 Master Detail.xlsx**工作簿是在 Visual Studio 设计器中，打开与**Sheet1**显示。  
  
2.  打开**数据源**窗口展开**订单**节点。  
  
3.  选择**OrderID**列，然后单击显示的下拉箭头。  
  
4.  单击**NamedRange**在下拉列表中，然后拖动**OrderID**到单元格的列**A2**。  
  
     A<xref:Microsoft.Office.Tools.Excel.NamedRange>控件名为`OrderIDNamedRange`单元格中创建**A2**。 同时，<xref:System.Windows.Forms.BindingSource>名为`OrdersBindingSource`，一个表适配器和一个<xref:System.Data.DataSet>实例添加到项目。 该控件绑定到<xref:System.Windows.Forms.BindingSource>，后者又绑定到<xref:System.Data.DataSet>实例。  
  
5.  向下滚动过的列下的**订单**表。 列表的底部是**订单详细信息**表; 这是此处，因为它是的子级**订单**表。 选择此**订单详细信息**表，不是在与相同的级别才**订单**表，，然后单击显示的下拉箭头。  
  
6.  单击**ListObject**在下拉列表中，然后拖动**OrderDetails**表添加到单元格**A6**。  
  
7.  A<xref:Microsoft.Office.Tools.Excel.ListObject>控件名为**Order_DetailsListObject**单元格中创建**A6**，并将其绑定到<xref:System.Windows.Forms.BindingSource>。  
  
#### <a name="to-add-two-buttons"></a>若要添加两个按钮  
  
1.  从**公共控件**选项卡**工具箱**，添加<xref:System.Windows.Forms.Button>控件添加到单元格**A3**工作表。  
  
     此按钮名为`Button1`。  
  
2.  添加另一个<xref:System.Windows.Forms.Button>控件添加到单元格**B3**工作表。  
  
     此按钮名为`Button2`。  
  
 接下来，将标记要缓存到文档中的数据集。  
  
## <a name="caching-the-dataset"></a>缓存数据集  
 标记要通过公共和设置数据集缓存到文档中的数据集**CacheInDocument**属性。  
  
#### <a name="to-cache-the-dataset"></a>缓存数据集  
  
1.  选择**NorthwindDataSet**在组件栏中。  
  
2.  在**属性**窗口中，更改**修饰符**属性**公共**。  
  
     数据集必须是公共的之前启用缓存。  
  
3.  更改**CacheInDocument**属性**True**。  
  
 下一步是将文本添加到按钮，并在 C# 中添加代码来挂钩的事件处理程序。  
  
## <a name="initializing-the-controls"></a>初始化的控件  
 设置按钮文本和添加事件处理程序期间<xref:Microsoft.Office.Tools.Excel.Workbook.Startup>事件。  
  
#### <a name="to-initialize-the-data-and-the-controls"></a>若要初始化的数据和控件  
  
1.  在**解决方案资源管理器**，右键单击**Sheet1.vb**或**Sheet1.cs**，然后单击**查看代码**快捷菜单上。  
  
2.  以下代码添加到`Sheet1_Startup`方法以设置按钮的文本。  
  
     [!code-vb[Trin_VstcoreDataExcel#15](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet2.vb#15)]
     [!code-csharp[Trin_VstcoreDataExcel#15](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs#15)]  
  
3.  仅适用于 C#，添加事件处理程序按钮的 click 事件与`Sheet1_Startup`方法。  
  
     [!code-csharp[Trin_VstcoreDataExcel#16](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs#16)]  
  
## <a name="adding-code-to-enable-scrolling-through-the-records"></a>添加代码以启用滚动记录  
 将代码添加到<xref:System.Windows.Forms.Control.Click>记录之间移动每个按钮的事件处理程序。  
  
#### <a name="to-scroll-through-the-records"></a>滚动显示记录  
  
1.  添加事件处理程序<xref:System.Windows.Forms.Control.Click>事件`Button1`，并添加以下代码以在记录间前后移动：  
  
     [!code-vb[Trin_VstcoreDataExcel#17](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet2.vb#17)]
     [!code-csharp[Trin_VstcoreDataExcel#17](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs#17)]  
  
2.  添加事件处理程序<xref:System.Windows.Forms.Control.Click>事件`Button2`，并添加以下代码无法进一步处理记录：  
  
     [!code-vb[Trin_VstcoreDataExcel#18](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet2.vb#18)]
     [!code-csharp[Trin_VstcoreDataExcel#18](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs#18)]  
  
## <a name="testing-the-application"></a>测试应用程序  
 现在，你可以测试你的工作簿，以确保按预期方式显示数据，并且可以脱机使用的解决方案。  
  
#### <a name="to-test-the-data-caching"></a>若要测试的数据缓存  
  
1.  按 F5 。  
  
2.  验证命名的区域和列表对象已填满数据源的数据。  
  
3.  通过单击按钮来滚动通过某些记录。  
  
4.  保存该工作簿，然后关闭的工作簿和 Visual Studio。  
  
5.  禁用数据库的连接。 拔下你的计算机的网络电缆，如果数据库位于在服务器上，或停止 SQL Server 服务，如果数据库位于开发计算机上。  
  
6.  打开 Excel，然后打开**我 Master Detail.xlsx**从 \bin 目录 （在 Visual Basic 中的 \My Master-Detail\bin 或 \My Master-Detail\bin\debug C# 中的）。  
  
7.  滚动一些记录，以查看断开连接时，工作表进行正常操作。  
  
8.  重新连接到数据库。 你的计算机重新连接到网络如果数据库位于在服务器上，或如果数据库位于开发计算机上启动该 SQL Server 服务。  
  
## <a name="next-steps"></a>后续步骤  
 本演练演示在工作表上创建主/详细信息数据关系以及缓存数据集的基础知识。 以下是接下来可能要执行的一些任务：  
  
-   部署解决方案。 有关详细信息，请参阅[部署 Office 解决方案](../vsto/deploying-an-office-solution.md)  
  
## <a name="see-also"></a>另请参阅  
 [将数据绑定到 Office 解决方案中的控件](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Office 解决方案中的数据](../vsto/data-in-office-solutions.md)   
 [缓存数据](../vsto/caching-data.md)   
 [主机项和主机控件概述](../vsto/host-items-and-host-controls-overview.md)  
  
  