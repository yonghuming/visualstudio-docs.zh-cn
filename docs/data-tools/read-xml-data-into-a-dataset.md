---
title: "读取 XML 数据读入数据集 |Microsoft 文档"
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
- reading XML
- data access [Visual Studio], XML data
- reading files, XML
- data [Visual Studio], reading from XML files
- reading data, XML files
- XML [Visual Studio], reading
- XML documents, reading
- datasets [Visual Basic], reading XML data
ms.assetid: fae72958-0893-47d6-b3dd-9d42418418e4
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 31c17df9b8b3e0a0b54d99f95e8a3d5704140cf7
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="read-xml-data-into-a-dataset"></a>XML 数据读入数据集
ADO.NET 提供用于处理 XML 数据的简单方法。 在本演练中，你创建的 Windows 应用程序将 XML 数据加载到数据集。 数据集随后显示在<xref:System.Windows.Forms.DataGridView>控件。 最后，根据 XML 文件的内容的 XML 架构被显示在文本框中。  
  
 本演练由五个主要步骤组成：  
  
1.  创建新项目  
  
2.  创建要将读取到数据集的 XML 文件  
  
3.  创建用户界面  
  
4.  创建数据集，读取 XML 文件中，并显示在<xref:System.Windows.Forms.DataGridView>控件  
  
5.  添加代码以显示 XML 架构中的 XML 文件基于<xref:System.Windows.Forms.TextBox>控件  
  
> [!NOTE]
>  显示的对话框和菜单命令可能与不同，具体取决于你现用的设置或版本帮助中的描述你正在使用。 若要更改你的设置，在**工具**菜单上，选择**导入和导出设置**。 有关详细信息，请参阅[个性化设置 Visual Studio IDE](../ide/personalizing-the-visual-studio-ide.md)。  
  
## <a name="create-a-new-project"></a>创建新项目  
 在此步骤中，创建一个包含此演练的 Visual Basic 或 Visual C# 项目。  
  
#### <a name="to-create-the-new-windows-project"></a>创建新的 Windows 项目  
  
1. 在 Visual Studio 中，在**文件**菜单上，选择**新建**，**项目...**.  
  
2. 展开**Visual C#**或**Visual Basic**在左侧窗格中，然后选择**Windows 经典桌面**。  

3. 在中间窗格中，选择**Windows 窗体应用程序**项目类型。  

4. 将项目**ReadingXML**，然后选择**确定**。 
  
     **ReadingXML**创建项目并将其添加到**解决方案资源管理器**。  
  
## <a name="generate-the-xml-file-to-be-read-into-the-dataset"></a>生成要将读取到数据集的 XML 文件  
 由于本演练的重点是 XML 数据读入数据集，所以提供 XML 文件的内容。  
  
#### <a name="to-create-the-xml-file-that-will-be-read-into-the-dataset"></a>若要创建将读入数据集的 XML 文件  
  
1.  上**项目**菜单上，选择**添加新项**。  
  
2.  选择**XML 文件**，命名该文件`authors.xml`，然后选择**添加**。  
  
     XML 文件加载到设计器，并可供编辑。  
  
3.  将以下代码粘贴到下面的 XML 声明编辑器：  
  
    ```xml  
    <Authors_Table>  
      <authors>  
        <au_id>172-32-1176</au_id>  
        <au_lname>White</au_lname>  
        <au_fname>Johnson</au_fname>  
        <phone>408 496-7223</phone>  
        <address>10932 Bigge Rd.</address>  
        <city>Menlo Park</city>  
        <state>CA</state>  
        <zip>94025</zip>  
        <contract>true</contract>  
      </authors>  
      <authors>  
        <au_id>213-46-8915</au_id>  
        <au_lname>Green</au_lname>  
        <au_fname>Margie</au_fname>  
        <phone>415 986-7020</phone>  
        <address>309 63rd St. #411</address>  
        <city>Oakland</city>  
        <state>CA</state>  
        <zip>94618</zip>  
        <contract>true</contract>  
      </authors>  
      <authors>  
        <au_id>238-95-7766</au_id>  
        <au_lname>Carson</au_lname>  
        <au_fname>Cheryl</au_fname>  
        <phone>415 548-7723</phone>  
        <address>589 Darwin Ln.</address>  
        <city>Berkeley</city>  
        <state>CA</state>  
        <zip>94705</zip>  
        <contract>true</contract>  
      </authors>  
      <authors>  
        <au_id>267-41-2394</au_id>  
        <au_lname>Hunter</au_lname>  
        <au_fname>Anne</au_fname>  
        <phone>408 286-2428</phone>  
        <address>22 Cleveland Av. #14</address>  
        <city>San Jose</city>  
        <state>CA</state>  
        <zip>95128</zip>  
        <contract>true</contract>  
      </authors>  
      <authors>  
        <au_id>274-80-9391</au_id>  
        <au_lname>Straight</au_lname>  
        <au_fname>Dean</au_fname>  
        <phone>415 834-2919</phone>  
        <address>5420 College Av.</address>  
        <city>Oakland</city>  
        <state>CA</state>  
        <zip>94609</zip>  
        <contract>true</contract>  
      </authors>  
    </Authors_Table>  
    ```  
  
4.  上**文件**菜单上，选择**保存 authors.xml**。  
  
## <a name="create-the-user-interface"></a>创建用户界面  
 此应用程序的用户界面由以下内容组成：  
  
-   A<xref:System.Windows.Forms.DataGridView>显示为数据的 XML 文件的内容的控件。  
  
-   A<xref:System.Windows.Forms.TextBox>显示 XML 文件的 XML 架构的控件。  
  
-   两个<xref:System.Windows.Forms.Button>控件。  
  
    -   一个按钮读入数据集的 XML 文件，然后将其显示在<xref:System.Windows.Forms.DataGridView>控件。  
  
    -   第二个按钮提取架构集中的数据，并通过<xref:System.IO.StringWriter>将其显示在<xref:System.Windows.Forms.TextBox>控件。  
  
#### <a name="to-add-controls-to-the-form"></a>向窗体添加控件  
  
1.  打开`Form1`在设计视图中。  
  
2.  从**工具箱**，将以下控件拖到窗体：  
  
    -   一个<xref:System.Windows.Forms.DataGridView>控件  
  
    -   一个<xref:System.Windows.Forms.TextBox>控件  
  
    -   两个<xref:System.Windows.Forms.Button>控件  
  
3.  设置以下属性：  
  
    |控件|属性|设置|  
    |-------------|--------------|-------------|  
    |`TextBox1`|**多行**|`true`|  
    ||**滚动条**|**垂直**|  
    |`Button1`|**Name**|`ReadXmlButton`|  
    ||**“文本”**|`Read XML`|  
    |`Button2`|**Name**|`ShowSchemaButton`|  
    ||**“文本”**|`Show Schema`|  
  
## <a name="create-the-dataset-that-receives-the-xml-data"></a>创建数据集，它接收 XML 数据  
 在此步骤中，创建名为的新数据集`authors`。 关于数据集的详细信息，请参阅[Visual Studio 中的数据集工具](../data-tools/dataset-tools-in-visual-studio.md)。  
  
#### <a name="to-create-a-new-dataset-that-receives-the-xml-data"></a>若要创建新的数据集，它接收 XML 数据  
  
1.  在**解决方案资源管理器**，选择的源文件**Form1**，然后选择**视图设计器**按钮上**解决方案资源管理器**工具栏。  
  
2.  从[工具箱，数据选项卡](../ide/reference/toolbox-data-tab.md)，拖动**数据集**到**Form1**。  
  
3.  在**添加数据集**对话框中，选择**非类型化数据集**，然后选择**确定**。  
  
     **DataSet1**添加到组件栏。  
  
4.  在**属性**窗口中，设置**名称**和<xref:System.Data.DataSet.DataSetName%2A>属性`AuthorsDataSet`。  
  
## <a name="create-the-event-handler-to-read-the-xml-file-into-the-dataset"></a>创建 XML 文件读入数据集的事件处理程序  
 **读取 XML**按钮将 XML 文件读入数据集。 然后，它设置属性上<xref:System.Windows.Forms.DataGridView>将其绑定到数据集的控件。  
  
#### <a name="to-add-code-to-the-readxmlbuttonclick-event-handler"></a>若要将代码添加到 ReadXmlButton_Click 事件处理程序  
  
1.  在**解决方案资源管理器**，选择**Form1**，然后选择**视图设计器**按钮上**解决方案资源管理器**工具栏。  
  
2.  选择**读取 XML**按钮。  
  
     **代码编辑器**在打开`ReadXmlButton_Click`事件处理程序。  
  
3.  键入下面的代码插入`ReadXmlButton_Click`事件处理程序：  
  
     [!code-csharp[VbRaddataFillingAndExecuting#2](../data-tools/codesnippet/CSharp/read-xml-data-into-a-dataset_1.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#2](../data-tools/codesnippet/VisualBasic/read-xml-data-into-a-dataset_1.vb)]  
  
4.  在`ReadXMLButton_Click`事件处理程序代码中，更改`filepath =`条目为正确的路径。  
  
## <a name="create-the-event-handler-to-display-the-schema-in-the-textbox"></a>创建要在文本框中显示架构的事件处理程序  
 **显示架构**按钮创建<xref:System.IO.StringWriter>对象，使用架构填充并显示在<xref:System.Windows.Forms.TextBox>控件。  
  
#### <a name="to-add-code-to-the-showschemabuttonclick-event-handler"></a>若要将代码添加到 ShowSchemaButton_Click 事件处理程序  
  
1.  在**解决方案资源管理器**，选择**Form1**，然后选择**视图设计器**按钮。  
  
2.  选择**显示架构**按钮。  
  
     **代码编辑器**在打开`ShowSchemaButton_Click`事件处理程序。  
  
3.  键入下面的代码插入`ShowSchemaButton_Click`事件处理程序。  
  
     [!code-csharp[VbRaddataFillingAndExecuting#3](../data-tools/codesnippet/CSharp/read-xml-data-into-a-dataset_2.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#3](../data-tools/codesnippet/VisualBasic/read-xml-data-into-a-dataset_2.vb)]  
  
## <a name="test-the-form"></a>测试窗体  
 你现在可以测试窗体，以确保其行为与预期相同。  
  
#### <a name="to-test-the-form"></a>若要测试窗体  
  
1.  选择**F5**运行该应用程序。  
  
2.  选择**读取 XML**按钮。  
  
     DataGridView 显示 XML 文件的内容。  
  
3.  选择**显示架构**按钮。  
  
     文本框中显示的 XML 文件的 XML 架构。  
  
## <a name="next-steps"></a>后续步骤  
 本演练介绍了 XML 文件读取到数据集，以及创建基于 XML 文件的内容的架构的基础知识。 以下是接下来你可能会执行一些任务：  
  
-   编辑数据集和其写出为 XML 中的数据。 有关详细信息，请参阅<xref:System.Data.DataSet.WriteXml%2A>。  
  
-   编辑数据集中的数据并将其写出到数据库。 有关详细信息，请参阅[保存数据](../data-tools/saving-data.md)。  
  
## <a name="see-also"></a>另请参阅  
 [在 Visual Studio 中访问数据](../data-tools/accessing-data-in-visual-studio.md)       
 [Visual Studio 中的 XML 工具](../xml-tools/xml-tools-in-visual-studio.md)