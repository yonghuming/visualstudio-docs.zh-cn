---
title: "演练：使用 Windows 窗体收集数据 | Microsoft Docs"
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
  - "数据 [Visual Studio 中的 Office 开发]，Windows 窗体"
  - "Windows 窗体 [Visual Studio 中的 Office 开发]，收集数据"
  - "窗体 [Visual Studio 中的 Office 开发]，演练"
  - "工作表 [Visual Studio 中的 Office 开发]，收集数据"
ms.assetid: 40e87f7f-cfbb-4761-bf1b-d042f45f4f09
caps.latest.revision: 54
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 53
---
# 演练：使用 Windows 窗体收集数据
  本演练演示如何从 Microsoft Office Excel 文档级自定义项打开 Windows 窗体、从用户处收集信息并将这些信息写入工作表单元格。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 虽然本演练具体使用的是 Excel 文档级项目，但其中所阐释的概念同样适用于其他 Office 项目。  
  
## 系统必备  
 你需要以下组件来完成本演练：  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] 或 [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)]。  
  
> [!NOTE]  
>  以下说明中的某些 Visual Studio 用户界面元素在计算机上出现的名称或位置可能会不同。 这些元素取决于你所使用的 Visual Studio 版本和你所使用的设置。 有关详细信息，请参阅[在 Visual Studio 中自定义开发设置](http://msdn.microsoft.com/zh-cn/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
## 创建新项目  
 第一步是创建一个 Excel 工作簿项目。  
  
#### 创建新项目  
  
1.  创建名为 **WinFormInput** 的 Excel 工作簿项目，然后在向导中选择“创建新文档”。 有关详细信息，请参阅[如何：在 Visual Studio 中创建 Office 项目](../vsto/how-to-create-office-projects-in-visual-studio.md)。  
  
     Visual Studio 将在设计器中打开新的 Excel 工作簿，并将“WinFormInput”项目添加到“解决方案资源管理器”中。  
  
## 将 NamedRange 控件添加到工作表  
  
#### 将命名范围添加到 Sheet1  
  
1.  在 `Sheet1` 上选择 **A1**。  
  
2.  在“名称”框中，键入 **formInput**。  
  
     “名称”框位于公式栏的左侧，工作表 **A** 列的正上方。  
  
3.  按 Enter。  
  
     <xref:Microsoft.Office.Tools.Excel.NamedRange> 控件即会添加到 **A1** 单元格。 工作表上没有可见的指示，但选择 **A1** 单元格时，**formInput** 会显示在“名称”框（左侧工作表的正上方）和“属性”窗口中。  
  
## 向项目添加 Windows 窗体  
 创建 Windows 窗体以向用户提供信息提示。  
  
#### 添加 Windows 窗体  
  
1.  在“解决方案资源管理器”中选择项目 **WinFormInput**。  
  
2.  在“项目”菜单上，单击“添加 Windows 窗体”。  
  
3.  将窗体命名为 **GetInputString.vb** 或 **GetInputString.cs**，然后单击“添加”。  
  
     新窗体即在设计器中打开。  
  
4.  向窗体添加 <xref:System.Windows.Forms.TextBox> 和 <xref:System.Windows.Forms.Button>。  
  
5.  选择按钮，在“属性”窗口找到属性“Text”，将文本更改为“OK”。  
  
 接下来，将代码添加到 `ThisWorkbook.vb` 或 `ThisWorkbook.cs` 以收集用户的信息。  
  
## 显示 Windows 窗体和收集信息  
 创建 `GetInputString` Windows 窗体的一个实例并将其显示出来，然后将用户的信息写入工作表的一个单元格中。  
  
#### 显示窗体和收集信息  
  
1.  右键单击“解决方案资源管理器”中的 **ThisWorkbook.vb** 或 **ThisWorkbook.cs**，然后单击“查看代码”。  
  
2.  在 `ThisWorkbook` 的 <xref:Microsoft.Office.Tools.Excel.Workbook.Open> 事件处理程序中，添加以下代码以声明窗体 `GetInputString` 的变量，然后显示窗体。  
  
    > [!NOTE]  
    >  在 C\# 中，必须如下方 <xref:Microsoft.Office.Tools.Excel.Workbook.Startup> 事件中所示添加事件处理程序。 有关创建事件处理程序的信息，请参阅[如何：在 Office 项目中创建事件处理程序](../vsto/how-to-create-event-handlers-in-office-projects.md)。  
  
     [!code-csharp[Trin_VstcoreProgrammingCollectingData#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingCollectingData/CS/ThisWorkbook.cs#1)]
     [!code-vb[Trin_VstcoreProgrammingCollectingData#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingCollectingData/VB/ThisWorkbook.vb#1)]  
  
3.  创建一个名为 `WriteStringToCell` 的将文本写入命名范围的方法。 此方法从窗体调用，用户输入传递到 **A1** 单元格上的 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控件 `formInput`。  
  
     [!code-csharp[Trin_VstcoreProgrammingCollectingData#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingCollectingData/CS/ThisWorkbook.cs#2)]
     [!code-vb[Trin_VstcoreProgrammingCollectingData#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingCollectingData/VB/ThisWorkbook.vb#2)]  
  
 接下来，将代码添加到窗体以处理按钮的 click 事件。  
  
## 将信息发送到工作表  
  
#### 将信息发送到工作表  
  
1.  在**“解决方案资源管理器”**中，右键单击 **GetInputString**，然后单击**“视图设计器”**。  
  
2.  双击按钮以打开添加了 <xref:System.Windows.Forms.Control.Click> 事件处理程序的代码文件。  
  
3.  将代码添加到事件处理程序以从文本框提取输入，将其发送给该函数 `WriteStringToCell`，然后关闭窗体。  
  
     [!code-csharp[Trin_VstcoreProgrammingCollectingData#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingCollectingData/CS/GetInputString.cs#3)]
     [!code-vb[Trin_VstcoreProgrammingCollectingData#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingCollectingData/VB/GetInputString.vb#3)]  
  
## 正在测试  
 你现在可以运行项目。 Windows 窗体显示，你的输入将在工作表中显示。  
  
#### 测试工作簿  
  
1.  按 F5 运行项目。  
  
2.  确认 Windows 窗体显示。  
  
3.  在文本框中键入**“Hello World”**，然后单击“确定”。  
  
4.  确认工作表的 **A1** 单元格中出现**“Hello World”**。  
  
## 后续步骤  
 本演练演示了显示 Windows 窗体和将数据传递到工作表的基础知识。 你可能想要执行的其他任务包括：  
  
-   在 Excel 工作簿或 Word 文档中使用 Windows 窗体控件。 有关详细信息，请参阅[Office 文档上的 Windows 窗体控件概述](../vsto/windows-forms-controls-on-office-documents-overview.md)。  
  
-   从文档级自定义项或 VSTO 外接程序修改 Microsoft Office 应用程序的用户界面。 有关详细信息，请参阅[Office UI 自定义](../vsto/office-ui-customization.md)。  
  
## 请参阅  
 [开发 Office 解决方案](../vsto/developing-office-solutions.md)   
 [在 Office 解决方案中编写代码](../vsto/writing-code-in-office-solutions.md)   
 [VSTO 外接程序编程](../vsto/programming-vsto-add-ins.md)   
 [对文档级自定义项进行编程](../vsto/programming-document-level-customizations.md)   
 [使用 Word 的演练](../vsto/walkthroughs-using-word.md)   
 [使用 Excel 的演练](../vsto/walkthroughs-using-excel.md)  
  
  