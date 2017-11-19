---
title: "演练： 更改缓存中的服务器上的工作簿的数据 |Microsoft 文档"
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
- workbooks [Office development in Visual Studio], changing server data
- datasets [Office development in Visual Studio], accessing on server
- server-side data access [Office development in Visual Studio]
- data [Office development in Visual Studio], accessing on server
- documents [Office development in Visual Studio], server-side data access
ms.assetid: 69e13de3-9286-40cc-8c4b-1727caf761bf
caps.latest.revision: "38"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a438e34fa6c5a74d648772fd4a5d4580b5f547d6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-changing-cached-data-in-a-workbook-on-a-server"></a>演练：更改服务器上的工作簿中的缓存数据
  本演练演示如何修改而不启动 Excel 通过使用 Microsoft Office Excel 工作簿中缓存的数据集<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>类。  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 本演练阐释了以下任务：  
  
-   定义包含 AdventureWorksLT 数据库中的数据的数据集。  
  
-   在 Excel 工作簿项目和一个控制台应用程序项目中创建的数据集的实例。  
  
-   创建<xref:Microsoft.Office.Tools.Excel.ListObject>绑定到工作簿中的数据集和填充<xref:Microsoft.Office.Tools.Excel.ListObject>时打开工作簿的数据。  
  
-   将工作簿中的数据集添加到数据缓存。  
  
-   通过在控制台应用程序，运行代码，而不启动 Excel 修改中缓存的数据集的数据列。  
  
 虽然本演练假定你的开发计算机上运行代码，则可以在没有安装 Excel 的服务器上使用的本演练中所示的代码。  
  
> [!NOTE]  
>  以下说明中的某些 Visual Studio 用户界面元素在计算机上出现的名称或位置可能会不同。 这些元素取决于你所使用的 Visual Studio 版本和你所使用的设置。 有关详细信息，请参阅[个性化设置 Visual Studio IDE](../ide/personalizing-the-visual-studio-ide.md)。  
  
## <a name="prerequisites"></a>先决条件  
 你需要以下组件来完成本演练：  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)]。  
  
-   对运行中实例的 Microsoft SQL Server 或 Microsoft SQL Server Express，已向其附加了 AdventureWorksLT 示例数据库的访问。 你可以下载 AdventureWorksLT 数据库从[CodePlex 网站](http://go.microsoft.com/fwlink/?linkid=87843)。 有关附加数据库的详细信息，请参阅下列主题：  
  
    -   若要使用 SQL Server Management Studio 或 SQL Server Management Studio Express 来附加数据库，请参阅 [如何：附加数据库 (SQL Server Management Studio)](http://msdn.microsoft.com/en-us/b4efb0ae-cfe6-4d81-a4b4-6e4916885caa)。  
  
    -   若要使用命令行来附加数据库，请参阅 [如何：将数据库文件附加到 SQL Server Express](http://msdn.microsoft.com/en-us/0f8e42b5-7a8c-4c30-8c98-7d2bdc8dcc68)。  
  
## <a name="creating-a-class-library-project-that-defines-a-dataset"></a>创建一个类库项目来定义数据集  
 若要使用的 Excel 工作簿项目和一个控制台应用程序中的相同数据集，必须在单独的程序集引用的这两个这些项目中定义数据集。 对于本演练中，定义在类库项目中的数据集。  
  
#### <a name="to-create-the-class-library-project"></a>若要创建类库项目  
  
1.  启动 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。  
  
2.  在 **“文件”** 菜单上，指向 **“新建”**，然后单击 **“项目”**。  
  
3.  在模板窗格中，展开**Visual C#**或**Visual Basic**，然后单击**Windows**。  
  
4.  在项目模板列表中，选择**类库**。  
  
5.  在**名称**框中，键入**AdventureWorksDataSet**。  
  
6.  单击**浏览**，导航到 %UserProfile%\My 文档 （对于 Windows XP 及更早版本） 或 （对于 Windows Vista) %UserProfile%\Documents 文件夹，然后单击**选择文件夹**。  
  
7.  在**新项目**对话框框中，确保**创建解决方案的目录**未选中复选框。  
  
8.  单击“确定”。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]将添加**AdventureWorksDataSet**项目合并为**解决方案资源管理器**并打开**Class1.cs**或**Class1.vb**代码文件。  
  
9. 在**解决方案资源管理器**，右键单击**Class1.cs**或**Class1.vb**，然后单击**删除**。 在本演练中不需要此文件。  
  
## <a name="defining-a-dataset-in-the-class-library-project"></a>在类库项目中定义数据集  
 定义为 SQL Server 2005 包含 AdventureWorksLT 数据库中的数据的类型化数据集。 稍后在本演练中，将从 Excel 工作簿项目和一个控制台应用程序项目中引用此数据集。  
  
 数据集是*类型化数据集*表示 AdventureWorksLT 数据库的产品表中的数据。 有关类型化数据集的详细信息，请参阅[Visual Studio 中的数据集工具](/visualstudio/data-tools/dataset-tools-in-visual-studio)。  
  
#### <a name="to-define-a-typed-dataset-in-the-class-library-project"></a>在类库项目中定义的类型化数据集  
  
1.  在**解决方案资源管理器**，单击**AdventureWorksDataSet**项目。  
  
2.  如果 **“数据源”** 窗口不可见，则在菜单栏上，通过选择 **“查看”**， **“其他窗口”**、 **“数据源”**显示它。  
  
3.  选择 **“添加新数据源”** 以启动 **“数据源配置向导”**。  
  
4.  单击“数据库” ，然后单击“下一步” 。  
  
5.  如果你有包含到 AdventureWorksLT 数据库的现有连接，选择此连接，然后单击**下一步**。  
  
     否则，单击“新建连接” ，然后使用“添加连接”  对话框创建新连接。 有关详细信息，请参阅[添加新连接](../data-tools/add-new-connections.md)。  
  
6.  在“将连接字符串保存到应用程序配置文件中”  页中，单击“下一步” 。  
  
7.  在**选择数据库对象**页上，展开**表**和选择**Product (SalesLT)**。  
  
8.  单击 **“完成”**。  
  
     AdventureWorksLTDataSet.xsd 文件添加到**AdventureWorksDataSet**项目。 此文件定义以下各项：  
  
    -   一个名为 `AdventureWorksLTDataSet`的类型化数据集。 此数据集表示 AdventureWorksLT 数据库中的产品表的内容。  
  
    -   名为 TableAdapter `ProductTableAdapter`。 此 TableAdapter 可用于读取和写入数据中`AdventureWorksLTDataSet`。 有关详细信息，请参阅 [TableAdapter Overview](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview)。  
  
     在本演练后面的部分中，你将使用这两个对象。  
  
9. 在**解决方案资源管理器**，右键单击**AdventureWorksDataSet**单击**生成**。  
  
     验证此项目是否已生成且未发生错误。  
  
## <a name="creating-an-excel-workbook-project"></a>创建 Excel 工作簿项目  
 创建数据的接口的 Excel 工作簿项目。 稍后在本演练中，你将创建<xref:Microsoft.Office.Tools.Excel.ListObject>显示数据，并将数据集实例添加到工作簿中的数据缓存。  
  
#### <a name="to-create-the-excel-workbook-project"></a>若要创建 Excel 工作簿项目  
  
1.  在**解决方案资源管理器**，右键单击**AdventureWorksDataSet**解决方案，指向**添加**，然后单击**新项目**。  
  
2.  在模板窗格中，展开**Visual C#**或**Visual Basic**，然后展开**Office**。  
  
3.  在展开**Office**节点中，选择**2010年**节点。  
  
4.  在项目模板列表中，选择 Excel 工作簿项目。  
  
5.  在**名称**框中，键入**AdventureWorksReport**。 请勿修改位置。  
  
6.  单击“确定”。  
  
     将打开“Visual Studio Tools for Office 项目向导”  。  
  
7.  确保**创建新文档**已选中，然后单击**确定**。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]打开**AdventureWorksReport**设计器中的工作簿并将添加**AdventureWorksReport**项目合并为**解决方案资源管理器**。  
  
## <a name="adding-the-dataset-to-data-sources-in-the-excel-workbook-project"></a>将数据集添加到 Excel 工作簿项目中的数据源  
 你可以在 Excel 工作簿中显示数据集之前，必须首先将数据集添加到 Excel 工作簿项目中的数据源。  
  
#### <a name="to-add-the-dataset-to-the-data-sources-in-the-excel-workbook-project"></a>若要将数据集添加到 Excel 工作簿项目中的数据源  
  
1.  在**解决方案资源管理器**，双击**Sheet1.cs**或**Sheet1.vb**下**AdventureWorksReport**项目。  
  
     在设计器中打开工作簿。  
  
2.  在 **“数据”** 菜单上，单击 **“添加新数据源”**。  
  
     **数据源配置向导**打开。  
  
3.  单击**对象**，然后单击**下一步**。  
  
4.  在**选择希望绑定到的对象**页上，单击**添加引用**。  
  
5.  上**项目**选项卡上，单击**AdventureWorksDataSet** ，然后单击**确定**。  
  
6.  下**AdventureWorksDataSet**命名空间的**AdventureWorksDataSet**程序集，请单击**AdventureWorksLTDataSet** ，然后单击**完成**.  
  
     **数据源**窗口将打开，和**AdventureWorksLTDataSet**添加到数据源的列表。  
  
## <a name="creating-a-listobject-that-is-bound-to-an-instance-of-the-dataset"></a>创建 ListObject 绑定到数据集的实例  
 若要在工作簿中显示数据集，请创建<xref:Microsoft.Office.Tools.Excel.ListObject>，它绑定到数据集的实例。 有关将控件绑定到数据的详细信息，请参阅 [Binding Data to Controls in Office Solutions](../vsto/binding-data-to-controls-in-office-solutions.md)。  
  
#### <a name="to-create-a-listobject-that-is-bound-to-an-instance-of-the-dataset"></a>若要创建绑定到数据集的某个实例 ListObject  
  
1.  在**数据源**窗口中，展开**AdventureWorksLTDataSet**节点下的**AdventureWorksDataSet**。  
  
2.  选择**产品**节点，单击下拉箭头将出现，并选择**ListObject**下拉列表中。  
  
     如果未显示的下拉箭头，确认工作簿是在设计器中打开。  
  
3.  拖动**产品**A1 单元格的表。  
  
     A<xref:Microsoft.Office.Tools.Excel.ListObject>控件名为`productListObject`工作表中，从开始 A1 单元格上创建。 同时，名为的数据集对象`adventureWorksLTDataSet`和<xref:System.Windows.Forms.BindingSource>名为`productBindingSource`添加到项目。 已将 <xref:Microsoft.Office.Tools.Excel.ListObject> 绑定到 <xref:System.Windows.Forms.BindingSource>，而后者又绑定到该数据集对象。  
  
## <a name="adding-the-dataset-to-the-data-cache"></a>将数据集添加到数据缓存  
 若要启用要访问工作簿中的数据集的 Excel 工作簿项目之外的代码，必须将数据集添加到数据缓存。 有关数据缓存的详细信息，请参阅[文档级自定义项中缓存数据](../vsto/cached-data-in-document-level-customizations.md)和[缓存数据](../vsto/caching-data.md)。  
  
#### <a name="to-add-the-dataset-to-the-data-cache"></a>将数据集添加到数据缓存  
  
1.  在设计器中，单击**adventureWorksLTDataSet**。  
  
2.  在**属性**窗口中，设置**修饰符**属性**公共**。  
  
3.  设置**CacheInDocument**属性**True**。  
  
## <a name="initializing-the-dataset-in-the-workbook"></a>初始化工作簿中的数据集  
 你也可以通过使用控制台应用程序从缓存的数据集检索数据之前，你必须先用数据填充数据缓存的数据集。  
  
#### <a name="to-initialize-the-dataset-in-the-workbook"></a>若要初始化该工作簿中的数据集  
  
1.  在**解决方案资源管理器**，右键单击**Sheet1.cs**或**Sheet1.vb**文件并单击**查看代码**。  
  
2.  将 `Sheet1_Startup` 事件处理程序替换为以下代码。 此代码使用的实例`ProductTableAdapter`中定义的类**AdventureWorksDataSet**项目以缓存的数据集用数据填充，如果它是当前为空。  
  
     [!code-csharp[Trin_CachedDataWalkthroughs#8](../vsto/codesnippet/CSharp/AdventureWorksDataSet/AdventureWorksReport/Sheet1.cs#8)]
     [!code-vb[Trin_CachedDataWalkthroughs#8](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/AdventureWorksReport/Sheet1.vb#8)]  
  
## <a name="checkpoint"></a>检查点  
 生成并运行 Excel 工作簿项目，以确保它在编译和运行且未发生错误。 此操作还会填充缓存的数据集，并将数据保存在工作簿中。  
  
#### <a name="to-build-and-run-the-project"></a>生成并运行此项目  
  
1.  在**解决方案资源管理器**，右键单击**AdventureWorksReport**项目，选择**调试**，然后单击**启动新实例**。  
  
     生成该项目，并在 Excel 中打开工作簿。 验证以下内容：  
  
    -   <xref:Microsoft.Office.Tools.Excel.ListObject>用数据填充。  
  
    -   中的值**ListPrice**列的第一行<xref:Microsoft.Office.Tools.Excel.ListObject>是 1431.5。 在本演练后面将使用一个控制台应用程序，来修改中的值**ListPrice**列。  
  
2.  保存工作簿。 不要修改该文件名或工作簿的位置。  
  
3.  关闭 Excel。  
  
## <a name="creating-a-console-application-project"></a>创建控制台应用程序项目  
 创建控制台应用程序项目以使用在工作簿中缓存的数据集中修改数据。  
  
#### <a name="to-create-the-console-application-project"></a>若要创建控制台应用程序项目  
  
1.  在**解决方案资源管理器**，右键单击**AdventureWorksDataSet**解决方案，指向**添加**，然后单击**新项目**。  
  
2.  在**项目类型**窗格中，展开**Visual C#**或**Visual Basic**，然后单击**Windows**。  
  
3.  在**模板**窗格中，选择**控制台应用程序**。  
  
4.  在**名称**框中，键入**DataWriter**。 请勿修改位置。  
  
5.  单击“确定”。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]将添加**DataWriter**项目合并为**解决方案资源管理器**并打开**Program.cs**或**Module1.vb**代码文件。  
  
## <a name="changing-data-in-the-cached-dataset-by-using-the-console-application"></a>更改使用控制台应用程序中缓存的数据集的数据  
 使用<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>类在控制台应用程序，以将数据读入本地`AdventureWorksLTDataSet`对象，修改此数据，然后将其保存回缓存的数据集。  
  
#### <a name="to-change-data-in-the-cached-dataset"></a>若要更改中缓存的数据集的数据  
  
1.  在**解决方案资源管理器**，右键单击**DataWriter**项目，然后单击**添加引用**。  
  
2.  上**.NET**选项卡上，选择 Microsoft.VisualStudio.Tools.Applications。  
  
3.  单击“确定”。  
  
4.  在**解决方案资源管理器**，右键单击**DataWriter**项目，然后单击**添加引用**。  
  
5.  上**项目**选项卡上，选择**AdventureWorksDataSet**，然后单击**确定**。  
  
6.  在代码编辑器中打开 Program.cs 或 Module1.vb 文件。  
  
7.  添加以下**使用**（对于 C# 中) 或**导入**（对于 Visual Basic) 语句与代码文件的顶部。  
  
     [!code-csharp[Trin_CachedDataWalkthroughs#1](../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs#1)]
     [!code-vb[Trin_CachedDataWalkthroughs#1](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb#1)]  
  
8.  将以下代码添加到 `Main` 方法中。 此代码声明了以下对象：  
  
    -   实例`AdventureWorksLTDataSet`中定义的类型**AdventureWorksDataSet**项目。  
  
    -   中的生成文件夹的 AdventureWorksReport 工作簿的路径**AdventureWorksReport**项目。  
  
    -   A<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>要用来访问该工作簿中的数据缓存对象。  
  
        > [!NOTE]  
        >  以下代码假定你正在使用具有.xlsx 文件扩展名的工作簿。 如果你的项目中的工作簿具有不同的文件扩展名，修改根据需要的路径。  
  
     [!code-csharp[Trin_CachedDataWalkthroughs#6](../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs#6)]
     [!code-vb[Trin_CachedDataWalkthroughs#6](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb#6)]  
  
9. 以下代码添加到`Main`方法，你在上一步中添加的代码之后。 这段代码执行下列任务：  
  
    -   它使用<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A>属性<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>类来访问工作簿中缓存的数据集。  
  
    -   它从缓存的数据集中读取的数据到本地数据集。  
  
    -   它更改`ListPrice`的数据集的产品表中每个产品的值。  
  
    -   它将所做的更改保存到工作簿中缓存的数据集。  
  
     [!code-csharp[Trin_CachedDataWalkthroughs#7](../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs#7)]
     [!code-vb[Trin_CachedDataWalkthroughs#7](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb#7)]  
  
10. 在**解决方案资源管理器**，右键单击**DataWriter**项目，指向**调试**，然后单击**启动新实例**。  
  
     控制台应用程序显示消息，而其缓存的数据集读入本地数据集、 修改产品价格的本地数据集，并将新值保存到缓存的数据集。 按 ENTER 可以关闭该应用程序。  
  
## <a name="testing-the-workbook"></a>测试此工作簿  
 当你打开工作簿，<xref:Microsoft.Office.Tools.Excel.ListObject>现在显示对所做的更改`ListPrice`中缓存的数据集的数据列。  
  
#### <a name="to-test-the-workbook"></a>若要测试此工作簿  
  
1.  如果它仍处于打开状态，请关闭 Visual Studio 设计器中中的 AdventureWorksReport 工作簿。  
  
2.  打开位于生成文件夹中的 AdventureWorksReport 工作簿**AdventureWorksReport**项目。 默认情况下，生成文件夹均位于以下位置之一：  
  
    -   %UserProfile%\My Documents\AdventureWorksReport\bin\Debug （对于 Windows XP 及更早版本）  
  
    -   %UserProfile%\Documents\AdventureWorksReport\bin\Debug （对于 Windows Vista)  
  
3.  验证中的值**ListPrice**列的第一行<xref:Microsoft.Office.Tools.Excel.ListObject>现 1574.65。  
  
4.  关闭工作簿。  
  
## <a name="see-also"></a>另请参阅  
 [演练： 将数据插入到一台服务器上的工作簿](../vsto/walkthrough-inserting-data-into-a-workbook-on-a-server.md)   
 [连接到 Windows 窗体应用程序中的数据](/visualstudio/data-tools/connecting-to-data-in-windows-forms-applications)  
  
  