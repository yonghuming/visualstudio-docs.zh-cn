---
title: "演练：使用按钮在工作表的文本框中显示文本 | Microsoft Docs"
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
  - "文本 [Visual Studio 中的 Office 开发], 显示工作表"
  - "文本 [Visual Studio 中的 Office 开发], 文本框"
  - "文本框, 在工作表中显示文本"
  - "工作表, 显示文本"
ms.assetid: 59b73159-aab7-4f61-9ace-1723c18d78d6
caps.latest.revision: 56
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 55
---
# 演练：使用按钮在工作表的文本框中显示文本
  此演练演示在 Microsoft Office Excel 工作表中使用按钮和文本框的基本操作，以及如何使用 Visual Studio 中的 Office 开发工具来创建 Excel 项目。  若要查看结果（作为完整示例），请参见 [Office 开发示例和演练](../vsto/office-development-samples-and-walkthroughs.md)中的 Excel 控件示例。  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 通过此演练，您将学会如何执行以下任务：  
  
-   将控件添加到工作表中。  
  
-   单击按钮时填充文本框。  
  
-   测试项目。  
  
> [!NOTE]  
>  以下说明中的某些 Visual Studio 用户界面元素在计算机上出现的名称或位置可能会不同。  您安装的 Visual Studio 版本以及使用的设置决定了这些元素。  有关更多信息，请参见[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-cn/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
## 系统必备  
 您需要以下组件来完成本演练：  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] 或 [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)]。  
  
## 创建项目  
 在此步骤中，您将使用 Visual Studio 创建一个 Excel 工作簿项目。  
  
#### 创建新项目  
  
1.  创建一个名为“我的 Excel 按钮”的 Excel 工作簿项目。  确保已选择**“创建新文档”**。  有关更多信息，请参见[如何：在 Visual Studio 中创建 Office 项目](../vsto/how-to-create-office-projects-in-visual-studio.md)。  
  
     Visual Studio 会在设计器中打开新的 Excel 工作簿，并将**“我的 Excel 按钮”**项目添加到**“解决方案资源管理器”**中。  
  
## 将控件添加到工作表  
 对于此演练，您需要在第一个工作表中添加一个按钮和一个文本框。  
  
#### 添加按钮和文本框  
  
1.  验证 **My Excel Button.xlsx** 工作簿在 Visual Studio 中打开设计器，与 `Sheet1` 显示。  
  
2.  从“工具箱”的**“公共控件”**选项卡中将一个 <xref:Microsoft.Office.Tools.Excel.Controls.TextBox> 拖动到 `Sheet1`。  
  
3.  从**“视图”**菜单中选择**“属性窗口”**。  
  
4.  请确保在**“属性”**窗口的下拉框中可以看到**“TextBox1”**，并将文本框的**“Name”**属性更改为**“displayText”**。  
  
5.  将**“Button”**控件拖动到 `Sheet1` 上，并更改以下属性：  
  
    |属性|值|  
    |--------|-------|  
    |**名称**|**insertText**|  
    |**文本**|插入文本|  
  
 现在编写单击按钮时将运行的代码。  
  
## 单击按钮时填充文本框  
 用户每次单击按钮时，**Hello World\!** 追加到文本框。  
  
#### 单击按钮时向文本框写入内容  
  
1.  在**“解决方案资源管理器”**中右击**“Sheet1”**，再在快捷菜单上，单击**“查看代码”**。  
  
2.  在按钮的 <xref:System.Windows.Forms.Control.Click> 事件处理程序中添加以下代码：  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#11](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/Sheet1.cs#11)]
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#11](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/VB/Sheet1.vb#11)]  
  
3.  在 C\# 中，必须按下面所示向 <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> 事件添加事件处理程序。  有关创建事件处理程序的信息，请参见[如何：在 Office 项目中创建事件处理程序](../vsto/how-to-create-event-handlers-in-office-projects.md)。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#12](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/Sheet1.cs#12)]  
  
## 测试应用程序  
 现在可以测试工作簿，以确保消息 **Hello World\!** 出现在文本框中，当单击按钮时。  
  
#### 测试工作簿  
  
1.  按 F5 运行项目。  
  
2.  单击按钮。  
  
3.  确认 **Hello World\!** 出现在文本框中。  
  
## 后续步骤  
 此演练演示在 Excel 工作表中使用按钮和文本框的基本操作。  以下是接下来可能要执行的一些任务：  
  
-   部署项目。  有关更多信息，请参见[部署 Office 解决方案](../vsto/deploying-an-office-solution.md)。  
  
-   使用复选框更改格式设置。  有关更多信息，请参见[演练：使用 CheckBox 控件更改工作表格式设置](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md)。  
  
## 请参阅  
 [如何：为 Office 文档添加 Windows 窗体控件](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
 [使用 Excel 的演练](../vsto/walkthroughs-using-excel.md)   
 [Office 文档上的 Windows 窗体控件的限制](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)  
  
  