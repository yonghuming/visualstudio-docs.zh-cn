---
title: "演练：使用内容控件创建模板"
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
  - "生成块 [Visual Studio 中的 Office 开发]"
  - "内容控件 [Visual Studio 中的 Office 开发], 添加到文档"
  - "Word [Visual Studio 中的 Office 开发], 创建文档"
ms.assetid: 88fb9a60-dcc3-4a5f-a8c9-7aff01ca4b4b
caps.latest.revision: 46
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 42
---
# 演练：使用内容控件创建模板
  本演练演示如何创建使用内容控件在 Microsoft Office Word 模板中创建可重用结构化内容的文档级自定义项。  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Word 允许创建可重用的文档部件集合，称为*“构建基块”*。  本演练演示如何将两个表格作为构建基块创建。  每个表格包含几个内容控件，可以容纳不同类型的内容（如纯文本或日期）。  其中一个表格包含有关员工的信息，另一个表格包含客户反馈。  
  
 从模板创建文档后，可通过使用几个 <xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl> 对象将任一表格添加到文档，这些对象显示模板中的可用构建基块。  
  
 本演练阐释了以下任务：  
  
-   在设计时创建包含 Word 模板中内容控件的表格。  
  
-   以编程方式填充组合框内容控件和下拉列表内容控件。  
  
-   阻止用户编辑指定表格。  
  
-   将表格添加到模板的构建基块集合。  
  
-   创建一个内容控件来显示模板中的可用构建基块。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## 系统必备  
 你需要以下组件来完成本演练：  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Word。  
  
## 创建新的 Word 模板项目  
 创建 Word 模板，以便用户可以轻松地创建他们自己的副本。  
  
#### 创建新的 Word 模板项目  
  
1.  创建一个 Word 模板项目，将其命名为 MyBuildingBlockTemplate。  在向导中，选择在解决方案中创建新的文档。  有关详细信息，请参阅[如何：在 Visual Studio 中创建 Office 项目](../vsto/how-to-create-office-projects-in-visual-studio.md)。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 将在设计器中打开新的 Word 模板，并将**“MyBuildingBlockTemplate”**项目添加到**“解决方案资源管理器”**。  
  
## 创建员工表  
 创建一个包含四种不同类型的内容控件的表格，用户可以在其中输入有关员工的信息。  
  
#### 创建员工表  
  
1.  在承载于 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 设计器的 Word 模板中，在功能区上单击**“插入”**选项卡。  
  
2.  在**“表格”**组中，单击**“表格”**，并插入包含 2 列和 4 行的表格。  
  
3.  在第一列中键入文本，使之类似于以下列：  
  
    ||  
    |-|  
    |员工姓名|  
    |雇佣日期|  
    |标题|  
    |Picture|  
  
4.  单击第二列中的第一个单元格（**“雇员姓名”**旁边）。  
  
5.  在功能区上，单击**“开发人员”**选项卡。  
  
    > [!NOTE]  
    >  如果**“开发人员”**选项卡不可见，则必须首先显示它。  有关详细信息，请参阅[如何：在功能区上显示“开发人员”选项卡](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)。  
  
6.  在**“控件”**组中，单击**“文本”**按钮 ![PlainTextContentControl](~/vsto/media/plaintextcontrol.gif "PlainTextContentControl")，以将 <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> 添加到第一个单元格。  
  
7.  单击第二列中的第二个单元格（**“雇佣日期”**旁边）。  
  
8.  在**“控件”**组中，单击**“日期选取器”**按钮 ![DatePickerContentControl](~/vsto/media/datepicker.gif "DatePickerContentControl")，以将 <xref:Microsoft.Office.Tools.Word.DatePickerContentControl> 添加到第二个单元格。  
  
9. 单击第二列中的第三个单元格（**“职务”**旁边）。  
  
10. 在**“控件”**组中，单击**“组合框”**按钮 ![ComboBoxContentControl](~/vsto/media/combobox.gif "ComboBoxContentControl")，以将 <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> 添加到第三个单元格。  
  
11. 单击第二列中的最后一个单元格（**“照片”**旁边）。  
  
12. 在**“控件”**组中，单击**“图片内容控件”**按钮 ![PictureContentControl](~/vsto/media/pictcontentcontrol.gif "PictureContentControl")，以将 <xref:Microsoft.Office.Tools.Word.PictureContentControl> 添加到最后一个单元格。  
  
## 创建客户反馈表  
 创建一个包含三种不同类型的内容控件的表格，用户可以在其中输入客户反馈信息。  
  
#### 创建客户反馈表  
  
1.  在 Word 模板中，单击你先前添加的员工表之后的一行，然后按 Enter 以添加新段落。  
  
2.  在功能区上，单击**“插入”**选项卡。  
  
3.  在**“表格”**组中，单击**“表格”**，并插入包含 2 列和 3 行的表格。  
  
4.  在第一列中键入文本，使之类似于以下列：  
  
    ||  
    |-|  
    |客户名称|  
    |满意度|  
    |批注|  
  
5.  单击第二列的第一个单元格（**“客户名称”**旁边）。  
  
6.  在功能区上，单击**“开发人员”**选项卡。  
  
7.  在**“控件”**组中，单击**“文本”**按钮 ![PlainTextContentControl](~/vsto/media/plaintextcontrol.gif "PlainTextContentControl")，以将 <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> 添加到第一个单元格。  
  
8.  单击第二列的第二个单元格（**“满意度”**旁边）。  
  
9. 在**“控件”**组中，单击**“下拉列表”**按钮 ![DropDownListContentControl](~/vsto/media/dropdownlist.gif "DropDownListContentControl")，以将 <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> 添加到第二个单元格。  
  
10. 单击第二列的第三个单元格（**“注释”**旁边）。  
  
11. 在**“控件”**组中，单击**“RTF”**按钮 ![RichTextContentControl](~/vsto/media/richtextcontrol.gif "RichTextContentControl")，以将 <xref:Microsoft.Office.Tools.Word.RichTextContentControl> 添加到第三个单元格。  
  
## 以编程方式填充组合框和下拉列表  
 使用 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中的**“属性”**窗口，可以在设计时初始化内容控件。  也可以在运行时初始化它们，这让你能够动态设置它们的初始状态。  对于本演练，使用代码在运行时填充 <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> 和 <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> 中的条目，以便你了解这些对象的工作方式。  
  
#### 以编程方式修改内容控件的 UI  
  
1.  在**“解决方案资源管理器”**中，右键单击**“ThisDocument.cs”**或**“ThisDocument.vb”**，然后单击**“查看代码”**。  
  
2.  向 `ThisDocument` 类添加下面的代码。  此代码声明了几个对象，你稍后将在本演练中使用它们。  
  
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ContentControlTemplateWalkthrough/CS/ThisDocument.cs#1)]
     [!code-vb[Trin_ContentControlTemplateWalkthrough#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ContentControlTemplateWalkthrough/VB/ThisDocument.vb#1)]  
  
3.  将以下代码添加到 `ThisDocument` 类的 `ThisDocument_Startup` 方法。  此代码将条目添加到表格中的 <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> 和 <xref:Microsoft.Office.Tools.Word.DropDownListContentControl>，并在用户进行编辑前设置每个控件中显示的占位符文本。  
  
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ContentControlTemplateWalkthrough/CS/ThisDocument.cs#2)]
     [!code-vb[Trin_ContentControlTemplateWalkthrough#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ContentControlTemplateWalkthrough/VB/ThisDocument.vb#2)]  
  
## 阻止用户编辑员工表  
 使用你之前声明的 <xref:Microsoft.Office.Tools.Word.GroupContentControl> 对象保护员工表。  保护员工表后，用户仍可编辑该表格中的内容控件。  但是，他们无法编辑第一列中的文本或以其他方式修改该表格，如添加或删除行和列。  有关如何使用 <xref:Microsoft.Office.Tools.Word.GroupContentControl> 保护部分文档的详细信息，请参阅[内容控件](../vsto/content-controls.md)。  
  
#### 阻止用户编辑员工表  
  
1.  将以下代码添加到 `ThisDocument` 类的 `ThisDocument_Startup` 方法中上一步添加的代码之后。  此代码可防止用户通过将表格置于你之前声明的 <xref:Microsoft.Office.Tools.Word.GroupContentControl> 对象之中来编辑员工表。  
  
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ContentControlTemplateWalkthrough/CS/ThisDocument.cs#3)]
     [!code-vb[Trin_ContentControlTemplateWalkthrough#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ContentControlTemplateWalkthrough/VB/ThisDocument.vb#3)]  
  
## 将表格添加到构建基块集合  
 将表格添加到模板中的文档构建基块集合，使用户可以将你创建的表格插入到文档中。  有关文档构建基块的详细信息，请参阅[内容控件](../vsto/content-controls.md)。  
  
#### 将表格添加到模板中的构建基块  
  
1.  将以下代码添加到 `ThisDocument` 类的 `ThisDocument_Startup` 方法中上一步添加的代码之后。  此代码将包含表格的新构建基块添加到 Microsoft.Office.Interop.Word.BuildingBlockEntries 集合，该集合包含模板中的所有可重用构建基块。  新构建基块是在名为 **Employee and Customer Information** 的新类别中定义的，并对其分配了构建基块类型 Microsoft.Office.Interop.Word.WdBuildingBlockTypes.wdTypeCustom1。  
  
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ContentControlTemplateWalkthrough/CS/ThisDocument.cs#4)]
     [!code-vb[Trin_ContentControlTemplateWalkthrough#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ContentControlTemplateWalkthrough/VB/ThisDocument.vb#4)]  
  
2.  将以下代码添加到 `ThisDocument` 类的 `ThisDocument_Startup` 方法中上一步添加的代码之后。  此代码将从模板删除表格。  将不再需要表格，因为已在模板中将其添加到可重用构建基块库。  代码首先将文档设置为设计模式，从而可以删除受保护的员工表。  
  
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ContentControlTemplateWalkthrough/CS/ThisDocument.cs#5)]
     [!code-vb[Trin_ContentControlTemplateWalkthrough#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ContentControlTemplateWalkthrough/VB/ThisDocument.vb#5)]  
  
## 创建显示构建基块的内容控件  
 创建一个内容控件，用于提供对先前创建的构建基块（即表格）的访问权限。  用户可以单击此控件以将表格添加到文档。  
  
#### 创建显示构建基块的内容控件  
  
1.  将以下代码添加到 `ThisDocument` 类的 `ThisDocument_Startup` 方法中上一步添加的代码之后。  此代码将初始化之前声明的 <xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl> 对象。  <xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl> 将显示在 **Employee and Customer Information** 类别中定义的并具有构建基块类型 Microsoft.Office.Interop.Word.WdBuildingBlockTypes.wdTypeCustom1 的所有构建基块。  
  
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ContentControlTemplateWalkthrough/CS/ThisDocument.cs#6)]
     [!code-vb[Trin_ContentControlTemplateWalkthrough#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ContentControlTemplateWalkthrough/VB/ThisDocument.vb#6)]  
  
## 测试项目  
 用户可以单击文档中的构建基块库控件，以插入员工表或客户反馈表。  用户可以在两个表的内容控件中键入或选择响应。  用户可以修改客户反馈表的其他部分，但应无法修改员工表的其他部分。  
  
#### 测试员工表  
  
1.  按 F5 运行项目。  
  
2.  单击**选择你的第一个构建基块**以显示第一个构建基块库内容控件。  
  
3.  单击控件中**“自定义库 1”**标题旁边的下拉箭头，然后选择**“员工表”**。  
  
4.  单击“员工姓名”单元格右侧的单元格，并键入一个姓名。  
  
     验证你只能向此单元格添加纯文本。  <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> 仅允许用户添加纯文本，不允许添加其他类型的内容（如图片或表格）。  
  
5.  选择“雇佣日期”单元右侧的单元格，并在日期选取器中选择一个日期。  
  
6.  单击“职务”单元格右侧的单元格，并在组合框中选择一个职务。  
  
     也可以键入列表中不存在的职务名称。  此操作可行的原因是 <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> 允许用户从条目列表中选择或键入自己的条目。  
  
7.  单击“照片”单元格右侧单元中的图标，并浏览到要显示的图像。  
  
8.  尝试向表中添加行或列，并尝试从表中删除行和列。  验证你无法修改该表格。  <xref:Microsoft.Office.Tools.Word.GroupContentControl> 将阻止你进行任何修改。  
  
#### 测试客户反馈表  
  
1.  单击**选择你的第二个构建基块**以显示第二个构建基块库内容控件。  
  
2.  单击控件中**“自定义库 1”**标题旁边的下拉箭头，然后选择**“客户表”**。  
  
3.  单击“客户名称”单元格右侧的单元格，并键入一个名称。  
  
4.  单击“满意度”单元格右侧的单元格，并选择一个可用选项。  
  
     验证你无法键入自己的条目。  <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> 仅允许用户从条目列表中进行选择。  
  
5.  单击“注释”单元格右侧的单元格，并键入注释。  
  
     也可以添加文本以外的内容，如图像或嵌入式表格。  此操作可行的原因是 <xref:Microsoft.Office.Tools.Word.RichTextContentControl> 允许用户添加文本以外的内容。  
  
6.  验证你可以向表中添加行或列，且可以从表中删除行和列。  此操作可行的原因是你没有通过将表格置于 <xref:Microsoft.Office.Tools.Word.GroupContentControl> 来保护它。  
  
7.  关闭模板。  
  
## 后续步骤  
 可从以下主题了解有关如何使用内容控件的更多信息：  
  
-   将内容控件绑定到嵌入到文档中的 XML 片段（也称为自定义 XML 部件）。  有关详细信息，请参阅[演练：将内容控件绑定到自定义 XML 部件](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md)。  
  
## 请参阅  
 [使用扩展对象实现 Word 自动化](../vsto/automating-word-by-using-extended-objects.md)   
 [内容控件](../vsto/content-controls.md)   
 [如何：向 Word 文档添加内容控件](../vsto/how-to-add-content-controls-to-word-documents.md)   
 [如何：使用内容控件保护文档的某些部分](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md)   
 [宿主项和宿主控件概述](../vsto/host-items-and-host-controls-overview.md)   
 [宿主项和宿主控件的编程限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [在运行时向 Office 文档添加控件](../vsto/adding-controls-to-office-documents-at-run-time.md)  
  
  