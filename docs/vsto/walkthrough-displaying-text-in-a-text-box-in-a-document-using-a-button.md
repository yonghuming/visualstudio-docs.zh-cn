---
title: "演练：使用按钮在文档的文本框中显示文本 | Microsoft Docs"
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
  - "文本框, 在文档中显示文本"
ms.assetid: 04c54ed7-9f00-4068-aaec-1f3200110116
caps.latest.revision: 60
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 59
---
# 演练：使用按钮在文档的文本框中显示文本
  本演练演示如何在 Microsoft Office Word 的文档级自定义项中使用按钮和文本框。  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 本演练阐释了以下任务：  
  
-   设计时，将控件添加到文档级项目中的 Word 文档。  
  
-   单击按钮时将填充文本框。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## 系统必备  
 你需要以下组件来完成本演练：  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Word  
  
## 创建项目  
 第一步是创建 Word 文档项目。  
  
#### 创建新项目  
  
1.  创建一个名为“我的 Word 按钮”的 Word 文档项目。  在向导中，选择**“创建新文档”**。  
  
     有关详细信息，请参阅[如何：在 Visual Studio 中创建 Office 项目](../vsto/how-to-create-office-projects-in-visual-studio.md)。  
  
     Visual Studio 将在设计器中打开新的 Word 文档，并将**“我的 Word 按钮”**项目添加到**“解决方案资源管理器”**。  
  
## 将控件添加到 Word 文档  
 用户界面控件包含一个按钮和一个 Word 文档上的文本框。  
  
#### 添加一个按钮和一个文本框  
  
1.  验证该文档已在 Visual Studio 设计器中打开。  
  
2.  从**“工具箱”**的**“公共控件”**选项卡中，将 <xref:Microsoft.Office.Tools.Word.Controls.TextBox> 拖到文档中。  
  
    > [!NOTE]  
    >  在 Word 中，默认情况下控件将按照文本进行删除。  通过更改 Word 中**“选项”**对话框的**“编辑”**选项卡上的默认设置，你可以修改控件和形状对象的插入方式。  
  
3.  在**“视图”**菜单上，单击**“属性窗口”**。  
  
4.  在**“属性”**窗口下拉框中查找**“TextBox1”**，然后将文本框的**“名称”**属性更改为 **displayText**。  
  
5.  将**“按钮”**控件拖到该文档，并更改下列属性。  
  
    |属性|值|  
    |--------|-------|  
    |**名称**|**insertText**|  
    |**文本**|插入文本|  
  
 现在，你可以编写将在单击该按钮时运行的代码。  
  
## 单击按钮时将填充文本框  
 每次用户单击此按钮时，**“Hello World\!”**都会添加到文本框中。  
  
#### 在单击按钮时写入文本框  
  
1.  在**“解决方案资源管理器”**中，右键单击**“ThisDocument”**，然后在快捷菜单上单击**“查看代码”**。  
  
2.  将下列代码添加到按钮的 <xref:System.Windows.Forms.Control.Click> 事件处理程序。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#7](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ThisDocument.cs#7)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#7](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/VB/ThisDocument.vb#7)]  
  
3.  在 C\# 中，必须向 <xref:Microsoft.Office.Tools.Word.Document.Startup> 事件添加按钮的事件处理程序。  有关创建事件处理程序的信息，请参阅[如何：在 Office 项目中创建事件处理程序](../vsto/how-to-create-event-handlers-in-office-projects.md)。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#8](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ThisDocument.cs#8)]  
  
## 测试应用程序  
 你现在可以测试你的文档，以确保单击按钮时文本框中出现消息**“Hello World\!”**。  
  
#### 测试文档  
  
1.  按 F5 运行项目。  
  
2.  单击按钮。  
  
3.  确认文本框中出现**“Hello World\!”**。  
  
## 后续步骤  
 本演练演示在 Word 文档中使用按钮和文本框的基础知识。  以下是接下来可能要执行的一些任务：  
  
-   使用组合框来更改格式设置。  有关详细信息，请参阅[演练：使用 CheckBox 控件更改文档格式设置](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md)。  
  
-   使用单选按钮以选择图表样式。  有关详细信息，请参阅[演练：使用单选按钮更新文档中的图表](../vsto/walkthrough-updating-a-chart-in-a-document-using-radio-buttons.md)。  
  
## 请参阅  
 [Office 文档上的 Windows 窗体控件概述](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [使用 Word 的演练](../vsto/walkthroughs-using-word.md)   
 [Office 开发示例和演练](../vsto/office-development-samples-and-walkthroughs.md)   
 [如何：为 Office 文档添加 Windows 窗体控件](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
 [宿主项和宿主控件概述](../vsto/host-items-and-host-controls-overview.md)  
  
  