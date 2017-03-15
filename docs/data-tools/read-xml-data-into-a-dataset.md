---
title: "演练：将 XML 数据读取到数据集 | Microsoft Docs"
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
  - "数据 [Visual Studio], 从 XML 文件读取"
  - "数据访问 [Visual Studio], XML 数据"
  - "数据集 [Visual Basic], 读取 XML 数据"
  - "读取数据, XML 文件"
  - "读取文件, XML"
  - "读取 XML"
  - "XML [Visual Studio], 读取"
  - "XML 文档, 读取"
ms.assetid: fae72958-0893-47d6-b3dd-9d42418418e4
caps.latest.revision: 18
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 演练：将 XML 数据读取到数据集
ADO.NET 提供使用 XML 数据的简单方法。  在此演练中，您将创建一个将 XML 数据加载到数据集中的 Windows 应用程序。  然后，该数据集将显示在一个 <xref:System.Windows.Forms.DataGridView> 中。  最后，将在一个文本框中显示基于 XML 文件内容的 XML 架构。  
  
 本演练由五个主要步骤组成：  
  
1.  创建新项目。  
  
2.  创建要读入数据集的 XML 文件。  
  
3.  创建用户界面。  
  
4.  创建数据集、读取 XML 文件并将其显示在 <xref:System.Windows.Forms.DataGridView> 控件中。  
  
5.  添加代码，以便根据 XML 文件在 <xref:System.Windows.Forms.TextBox> 控件中显示 XML 架构。  
  
> [!NOTE]
>  显示的对话框和菜单命令可能会与“帮助”中的描述不同，具体取决于您现用的设置或版本。  若要更改设置，请在**“工具”**菜单上选择**“导入和导出设置”**。  有关更多信息，请参见 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-cn/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
## 创建新项目  
 在此步骤中，您将创建一个将包含此演练的 Visual Basic 或 Visual C\# 项目。  
  
#### 创建新的 Windows 项目  
  
1.  从**“文件”**菜单创建一个新的项目。  
  
2.  将该项目命名为 `ReadingXML`。  
  
3.  选择**“Windows 应用程序”**，然后单击**“确定”**。  有关更多信息，请参见 [客户端应用程序](../Topic/Developing%20Client%20Applications%20with%20the%20.NET%20Framework.md)。  
  
     创建 **ReadingXML** 项目并将其添加到“解决方案资源管理器”中。  
  
## 生成要读入数据集的 XML 文件  
 由于本演练的重点在于将 XML 数据读入到数据集中，所以提供了 XML 文件的内容。  
  
#### 创建将读入数据集的 XML 文件  
  
1.  从**“项目”**菜单中选择**“添加新项”**。  
  
2.  选择**“XML 文件”**，指定文件名为 `authors.xml`，然后单击**“添加”**。  
  
     XML 文件即加载到设计器中并可供编辑。  
  
3.  将以下代码粘贴到 XML 声明下的编辑器中：  
  
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
  
4.  从**“文件”**菜单中，指向**“保存 authors.xml”**。  
  
## 创建用户界面  
 此应用程序的用户界面将包括以下内容：  
  
-   一个 <xref:System.Windows.Forms.DataGridView> 控件，它将 XML 文件的内容显示为数据。  
  
-   一个 <xref:System.Windows.Forms.TextBox> 控件，它显示 XML 文件的 XML 架构。  
  
-   两个 <xref:System.Windows.Forms.Button> 控件。  
  
    -   一个按钮将 XML 文件读入数据集并将其显示在 <xref:System.Windows.Forms.DataGridView> 控件中。  
  
    -   另一个按钮从数据集中提取架构，然后通过一个 <xref:System.IO.StringWriter> 将其显示在 <xref:System.Windows.Forms.TextBox> 控件中。  
  
#### 向窗体添加控件  
  
1.  在“设计”视图中打开 `Form1`。  
  
2.  将以下控件从**“工具箱”**中拖动到窗体上：  
  
    -   一个 <xref:System.Windows.Forms.DataGridView> 控件  
  
    -   一个 <xref:System.Windows.Forms.TextBox> 控件  
  
    -   两个 <xref:System.Windows.Forms.Button> 控件  
  
3.  设置下列属性：  
  
    |控件|属性|设置|  
    |--------|--------|--------|  
    |`TextBox1`|**Multiline**|`true`|  
    ||**ScrollBars**|**垂直**|  
    |`Button1`|**名称**|`ReadXmlButton`|  
    ||**Text**|`Read XML`|  
    |`Button2`|**名称**|`ShowSchemaButton`|  
    ||**Text**|`Show Schema`|  
  
## 创建将接收 XML 数据的数据集  
 在此下一个过程中，会创建一个名为 `authors` 的新数据集。  有关数据集的更多信息，请参见 [在 Visual Studio 中使用数据集](../data-tools/dataset-tools-in-visual-studio.md)。  
  
#### 创建将接收 XML 数据的新数据集  
  
1.  对于在**“解决方案资源管理器”**中选择的**“Form1”**的源文件，在**“解决方案资源管理器”**工具栏中单击**“视图设计器”**按钮。  
  
2.  从 [工具箱，“数据”选项卡](../ide/reference/toolbox-data-tab.md) 中将 **DataSet** 拖动到 **Form1** 上。  
  
3.  选择在 **添加数据集** 对话框的 **非类型化数据集** ，然后单击 **好**。  
  
     **DataSet1**随即被添加到组件栏。  
  
4.  在**“属性”**窗口中，将 **Name** 和 <xref:System.Data.DataSet.DataSetName%2A> 属性设置为 `AuthorsDataSet`。  
  
## 创建将 XML 读入数据集的事件处理程序  
 **“Read XML”**按钮将 XML 文件读入数据集并对 <xref:System.Windows.Forms.DataGridView> 设置将其绑定到该数据集的属性。  
  
#### 添加代码到 ReadXmlButton\_Click 事件处理程序  
  
1.  在**“解决方案资源管理器”**中，选择**“Form1”**，然后单击**“解决方案资源管理器”**工具栏上的**“视图设计器”**按钮。  
  
2.  双击 **Read XML** 按钮。  
  
     **“代码编辑器”**打开并定位到 `ReadXmlButton_Click` 事件处理程序。  
  
3.  将下列代码键入到 `ReadXmlButton_Click` 事件处理程序中：  
  
     [!code-cs[VbRaddataFillingAndExecuting#2](../data-tools/codesnippet/CSharp/read-xml-data-into-a-dataset_1.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#2](../data-tools/codesnippet/VisualBasic/read-xml-data-into-a-dataset_1.vb)]  
  
4.  在 `ReadXMLButton_Click` 事件处理程序代码中，将 `filepath =` 项更改为正确的路径。  
  
## 创建在 Textbox 中显示架构的事件处理程序  
 **“Show Schema”**按钮将创建一个填充架构并在 <xref:System.Windows.Forms.TextBox> 中显示的 <xref:System.IO.StringWriter> 对象。  
  
#### 添加代码到 ShowSchemaButton\_Click 事件处理程序  
  
1.  在**“解决方案资源管理器”**中，选择**“Form1”**，并单击**“视图设计器”**按钮。  
  
2.  双击 **Show Schema** 按钮。  
  
     **“代码编辑器”**打开并定位到 `ShowSchemaButton_Click` 事件处理程序。  
  
3.  将下列代码键入到 `ShowSchemaButton_Click` 事件处理程序中。  
  
     [!code-cs[VbRaddataFillingAndExecuting#3](../data-tools/codesnippet/CSharp/read-xml-data-into-a-dataset_2.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#3](../data-tools/codesnippet/VisualBasic/read-xml-data-into-a-dataset_2.vb)]  
  
## 测试  
 现在可以测试窗体，以确保其行为与预期相同。  
  
#### 测试窗体  
  
1.  按 F5 运行该应用程序。  
  
2.  单击 **Read XML** 按钮。  
  
     DataGridView 显示 XML 文件的内容。  
  
3.  单击 **Show Schema** 按钮。  
  
     文本框显示 XML 文件的 XML 架构。  
  
## 后续步骤  
 本演练显示将 XML 文件读入数据集以及基于 XML 文件内容创建架构的基本步骤。  下一步可能要执行以下几项任务：  
  
-   编辑数据集中的数据并将其写出为 XML。  有关更多信息，请参见 <xref:System.Data.DataSet.WriteXml%2A>。  
  
-   编辑数据集中的数据并将其写出到数据库中。  有关更多信息，请参见 [保存数据](../data-tools/saving-data.md)。  
  
## 请参阅  
 [数据演练](../Topic/Data%20Walkthroughs.md)   
 [在 Visual Studio 中访问数据](../data-tools/accessing-data-in-visual-studio.md)   
 [准备应用程序以接收数据](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Visual Studio 中的 XML 工具](../xml-tools/xml-tools-in-visual-studio.md)