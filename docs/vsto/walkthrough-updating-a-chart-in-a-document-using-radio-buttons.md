---
title: "演练：使用单选按钮更新文档中的图表 | Microsoft Docs"
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
  - "控件 [Visual Studio 中的 Office 开发], 更新文档"
  - "文档 [Visual Studio 中的 Office 开发], 使用控件更新"
ms.assetid: 56e6d1f2-65a4-41f0-aff5-f0cfd96d7185
caps.latest.revision: 60
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 59
---
# 演练：使用单选按钮更新文档中的图表
  此演练演示如何使用 Microsoft Office Word 文档级自定义中的单选按钮，为用户提供在文档中选择图表样式的选项。  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 本演练阐释了以下任务：  
  
-   在文档级项目中，在设计时向文档中添加图表。  
  
-   通过将单选按钮添加到用户控件来对它们进行分组。  
  
-   在选择了某个选项时更改图表样式。  
  
 若要查看完整示例，请参阅[Office 开发示例和演练](../vsto/office-development-samples-and-walkthroughs.md)中的 Word 控件示例。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## 系统必备  
 你需要以下组件来完成本演练：  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] 或 [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)]。  
  
## 创建项目  
 第一步是创建 Word 文档项目。  
  
#### 创建新项目  
  
1.  创建一个名为**“我的图表选项”**的 Word 文档项目。  在向导中，选择**“创建新文档”**。  有关详细信息，请参阅[如何：在 Visual Studio 中创建 Office 项目](../vsto/how-to-create-office-projects-in-visual-studio.md)。  
  
     Visual Studio 将在设计器中打开新的 Word 文档并将**“我的图表选项”**项目添加到**“解决方案资源管理器”**中。  
  
## 向文档中添加图表  
  
#### 添加图表  
  
1.  在承载于 Visual Studio 设计器中的 Word 文档中，单击功能区上的**“插入”**选项卡。  
  
2.  在**“文本”**组中，单击**“插入对象”**下拉按钮，然后单击**“对象”**。  
  
     随即打开**“对象”**对话框。  
  
3.  在**“新建”**选项卡上的**“对象类型”**列表中，选择**“Microsoft Graph 图表**”，然后单击**“确定”**。  
  
     此时将在文档中的插入点处添加一个图表，并且出现**“数据表”**窗口，其中会显示一些默认数据。  
  
4.  关闭**“数据表”**窗口使图表接受默认值，然后单击文档内部将焦点从图表移开。  
  
5.  右击图表，然后单击**“设置对象格式”**。  
  
6.  在**“设置对象格式”**对话框的**“布局”**选项卡上，选择**“正方形”**，然后单击**“确定”**。  
  
## 将用户控件添加到项目中  
 文档上的单选按钮默认情况下不互相排斥。  通过将这些按钮添加到用户控件中，然后编写代码来控制选择，可使这些按钮正常工作。  
  
#### 添加用户控件  
  
1.  在**“解决方案资源管理器”**中选择**“我的图表选项”**项目。  
  
2.  在**“项目”**菜单上，单击**“添加新项”**。  
  
3.  在**“添加新项”**对话框中，单击**“用户控件”**，将控件命名为**“ChartOptions”**，然后单击**“添加”**。  
  
#### 向用户控件添加 Windows 窗体控件  
  
1.  如果该用户控件在设计器中不可见，请在**“解决方案资源管理器”**中双击**“ChartOptions”**。  
  
2.  从**“工具箱”**的**“公共控件”**选项卡中，将第一个**“单选按钮”**控件拖到该用户控件，然后更改以下属性。  
  
    |属性|值|  
    |--------|-------|  
    |**名称**|**columnChart**|  
    |**Text**|柱形图|  
  
3.  向用户控件添加第二个**“单选按钮”**，并更改以下属性。  
  
    |属性|值|  
    |--------|-------|  
    |**名称**|**barChart**|  
    |**Text**|条形图|  
  
4.  向用户控件添加第三个**“单选按钮”**，并更改以下属性。  
  
    |属性|值|  
    |--------|-------|  
    |**名称**|**lineChart**|  
    |**Text**|折线图|  
  
5.  向用户控件添加第四个**“单选按钮”**，并更改以下属性。  
  
    |属性|值|  
    |--------|-------|  
    |**名称**|**areaBlockChart**|  
    |**Text**|面积图|  
  
## 添加引用  
 若要从文档上的用户控件访问图表，则必须在项目中引用 Microsoft.Office.Interop.Graph 程序集。  
  
#### 添加对 Microsoft.Office.Interop.Graph 程序集的引用  
  
1.  在**“项目”**菜单上，单击**“添加引用”**。  
  
     将显示**“添加引用”**对话框。  
  
2.  在**“.NET”**选项卡上，选择**“Microsoft.Office.Interop.Graph”**，然后单击**“确定”**。  选择该程序集的 14.0.0.0 版。  
  
## 当某个单选按钮处于选定状态时更改图表样式  
 若要使这些按钮正常工作，请创建用户控件的公共事件，添加属性以设置选择类型，并为每个单选按钮的 `CheckedChanged` 事件创建过程。  
  
#### 创建用户控件的事件和属性  
  
1.  在**“解决方案资源管理器”**中右击用户控件，然后单击**“查看代码”**。  
  
2.  向 `ChartOptions` 类添加代码以创建 `SelectionChanged` 事件和 `Selection` 属性。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#9](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ChartOptions.cs#9)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#9](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/VB/ChartOptions.vb#9)]  
  
#### 处理单选按钮的 CheckedChange 事件  
  
1.  设置 `areaBlockChart` 单选按钮的 `CheckedChanged` 事件处理程序中的图表类型，然后引发事件。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#10](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ChartOptions.cs#10)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#10](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/VB/ChartOptions.vb#10)]  
  
2.  设置 `barChart` 单选按钮的 `CheckedChanged` 事件处理程序中的图表类型。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#11](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ChartOptions.cs#11)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#11](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/VB/ChartOptions.vb#11)]  
  
3.  设置 `columnChart` 单选按钮的 `CheckedChanged` 事件处理程序中的图表类型。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#12](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ChartOptions.cs#12)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#12](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/VB/ChartOptions.vb#12)]  
  
4.  设置 `lineChart` 单选按钮的 `CheckedChanged` 事件处理程序中的图表类型。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#13](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ChartOptions.cs#13)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#13](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/VB/ChartOptions.vb#13)]  
  
5.  在 C\# 中，必须为单选按钮添加事件处理程序。  可以将此代码添加到 `ChartOptions` 构造函数中 `InitializeComponent` 调用的下面。  有关创建事件处理程序的信息，请参阅[如何：在 Office 项目中创建事件处理程序](../vsto/how-to-create-event-handlers-in-office-projects.md)。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#14](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ChartOptions.cs#14)]  
  
## 向文档添加用户控件  
 生成解决方案时，新的用户控件将自动添加到**“工具箱”**中。  然后可以将该控件从**“工具箱”**拖动到文档中。  
  
#### 向文档添加用户控件  
  
1.  在**“生成”**菜单上，单击**“生成解决方案”**。  
  
     **“ChartOptions”**用户控件便会被添加到**“工具箱”**中。  
  
2.  在**“解决方案资源管理器”**中，右击**“ThisDocument.vb”**或**“ThisDocument.cs”**，然后单击**“视图设计器”**。  
  
3.  将 `ChartOptions` 控件从**“工具箱”**拖动到文档中。  
  
     在**“属性”**窗口中，命名你刚添加到文档 `ChartOptions1` 的控件。  
  
## 更改图表类型  
 创建一个事件处理程序，以根据在用户控件中选择的选项更改图表类型。  
  
#### 更改文档中显示的图表类型  
  
1.  向 `ThisDocument` 类添加以下事件处理程序。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#15](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ThisDocument.cs#15)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#15](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/VB/ThisDocument.vb#15)]  
  
2.  在 C\# 中，必须向 <xref:Microsoft.Office.Tools.Word.Document.Startup> 事件添加用户控件的事件处理程序。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#16](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ThisDocument.cs#16)]  
  
## 测试应用程序  
 现在，你可以对文档进行测试，以确保选择单选按钮时能正确更新图表样式。  
  
#### 测试文档  
  
1.  按 F5 运行项目。  
  
2.  选择不同的单选按钮。  
  
3.  确认图表样式随所选选项发生了相应的更改。  
  
## 后续步骤  
 以下是接下来可能要执行的一些任务：  
  
-   使用按钮填充文本框。  有关详细信息，请参阅[演练：使用按钮在文档的文本框中显示文本](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-document-using-a-button.md)。  
  
-   通过从组合框中选择样式来更改格式设置。  有关详细信息，请参阅[演练：使用 CheckBox 控件更改文档格式设置](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md)。  
  
## 请参阅  
 [使用 Word 的演练](../vsto/walkthroughs-using-word.md)   
 [Office 开发示例和演练](../vsto/office-development-samples-and-walkthroughs.md)   
 [Office 文档上的 Windows 窗体控件的限制](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)  
  
  