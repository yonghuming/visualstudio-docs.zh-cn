---
title: "演练：使用 CheckBox 控件更改文档格式设置 | Microsoft Docs"
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
  - "复选框, Word 文档"
  - "控件 [Visual Studio 中的 Office 开发], 添加到文档"
  - "文档 [Visual Studio 中的 Office 开发], 复选框控件"
  - "文档 [Visual Studio 中的 Office 开发], 格式化"
  - "Word 文档, 使用控件更改格式"
ms.assetid: 3740e41d-a57e-43bb-87e7-6e5481ef290b
caps.latest.revision: 70
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 69
---
# 演练：使用 CheckBox 控件更改文档格式设置
  本演练演示在 Microsoft Office Word 的文档级自定义项中，如何使用 Windows 窗体控件来更改文本格式。  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 本演练阐释了以下任务：  
  
-   设计时在文档级项目中向文档添加文本和控件。  
  
-   选中选项时设置文本的格式。  
  
 若要查看完整示例，请参见 [Office 开发示例和演练](../vsto/office-development-samples-and-walkthroughs.md)中的 Word 控件示例。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## 系统必备  
 您需要以下组件来完成本演练：  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] 或 [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)]。  
  
## 创建项目  
 第一步是创建 Word 文档项目。  
  
#### 创建新项目  
  
1.  创建一个 Word 文档项目，并将其命名为“我的 Word 格式设置”。  在向导中，选择**“创建新文档”**。  
  
     有关更多信息，请参见[如何：在 Visual Studio 中创建 Office 项目](../vsto/how-to-create-office-projects-in-visual-studio.md)。  
  
     Visual Studio 将在设计器中打开新的 Word 文档，并将**“我的 Word 格式设置”**项目添加到**“解决方案资源管理器”**中。  
  
## 将文本和控件添加到 Word 文档中  
 对于此演练，要在 Word 文档中添加三个复选框，并在 <xref:Microsoft.Office.Tools.Word.Bookmark> 控件中添加一些文本。  这些复选框将向用户呈现用于设置文本格式的选项。  
  
#### 添加三个复选框  
  
1.  验证文档是否已在 Visual Studio 设计器中打开。  
  
2.  从**“工具箱”**的**“公共控件”**选项卡中，将第一个 <xref:Microsoft.Office.Tools.Word.Controls.CheckBox> 控件拖到文档中。  
  
3.  在**“属性”**窗口中，更改下列属性。  
  
    |属性|值|  
    |--------|-------|  
    |**名称**|**applyBoldFont**|  
    |**文本**|Bold|  
  
4.  按**“Enter”**将插入点移至第一个复选框下方。  
  
5.  将第二个复选框添加到文档中 `ApplyBoldFont` 复选框的下方，并更改以下属性。  
  
    |属性|值|  
    |--------|-------|  
    |**名称**|**applyItalicFont**|  
    |**文本**|Italic|  
  
6.  按**“Enter”**将插入点移至第二个复选框的下方。  
  
7.  将第三个复选框添加到文档中 `ApplyItalicFont` 复选框的下方，并更改以下属性。  
  
    |属性|值|  
    |--------|-------|  
    |**名称**|**applyUnderlineFont**|  
    |**文本**|Underline|  
  
#### 添加文本和书签控件  
  
1.  将插入点移至复选框控件的下方，并键入以下文本：  
  
     单击一个复选框以更改此文本的格式设置。  
  
2.  从**“工具箱”**的**“Word 控件”**选项卡中，将 <xref:Microsoft.Office.Tools.Word.Bookmark> 控件拖动到文档中。  
  
     将出现**“添加书签控件”**对话框。  
  
3.  选择已添加到文档中的文本，然后单击**“确定”**。  
  
     <xref:Microsoft.Office.Tools.Word.Bookmark> 控件**“Bookmark1”**被添加到文档中的选定文本中。  
  
4.  在**“属性”**窗口中，将**“\(Name\)”**属性更改为 **fontText**。  
  
 接下来，编写在选中或清除复选框时用于设置文本格式的代码。  
  
## 选中或清除复选框时设置文本的格式  
 当用户选择格式设置选项时，将更改文档中文本的格式。  
  
#### 选中复选框时更改格式设置  
  
1.  右击**“解决方案资源管理器”**中的 `ThisDocument`，再单击快捷菜单上的**“查看代码”**。  
  
2.  （仅适用于 C\#）将下列常量添加到 **ThisDocument** 类。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ThisDocument.cs#2)]  
  
3.  将以下代码添加到 `applyBoldFont` 复选框的 <xref:System.Windows.Forms.Control.Click> 事件处理程序中。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ThisDocument.cs#3)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/VB/ThisDocument.vb#3)]  
  
4.  将以下代码添加到 `applyItalicFont` 复选框的 <xref:System.Windows.Forms.Control.Click> 事件处理程序中。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ThisDocument.cs#4)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/VB/ThisDocument.vb#4)]  
  
5.  将以下代码添加到 `applyUnderlineFont` 复选框的 <xref:System.Windows.Forms.Control.Click> 事件处理程序中。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ThisDocument.cs#5)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/VB/ThisDocument.vb#5)]  
  
6.  在 C\# 中，必须将文本框的事件处理程序添加到 <xref:Microsoft.Office.Tools.Word.Document.Startup> 事件。  有关如何创建事件处理程序的信息，请参见[如何：在 Office 项目中创建事件处理程序](../vsto/how-to-create-event-handlers-in-office-projects.md)。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ThisDocument.cs#6)]  
  
## 测试应用程序  
 现在，可以对文档进行测试，以验证选择或清除复选框时文本的格式设置是否正确。  
  
#### 测试文档  
  
1.  按 F5 运行项目。  
  
2.  选择或清除复选框。  
  
3.  确认文本的格式设置正确。  
  
## 后续步骤  
 本演练演示在 Word 文档中使用复选框以及以编程方式更改文本格式设置的基本操作。  下一步可能要执行以下几项任务：  
  
-   使用按钮填充文本框。  有关更多信息，请参见[演练：使用按钮在文档的文本框中显示文本](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-document-using-a-button.md)。  
  
-   使用单选按钮选择图表样式。  有关更多信息，请参见[演练：使用单选按钮更新文档中的图表](../vsto/walkthrough-updating-a-chart-in-a-document-using-radio-buttons.md)。  
  
## 请参阅  
 [使用 Word 的演练](../vsto/walkthroughs-using-word.md)   
 [Office 开发示例和演练](../vsto/office-development-samples-and-walkthroughs.md)   
 [NamedRange 控件](../vsto/namedrange-control.md)   
 [Office 文档上的 Windows 窗体控件的限制](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)  
  
  