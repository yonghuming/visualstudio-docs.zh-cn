---
title: "演练：根据 NamedRange 控件的事件进行编程"
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
  - "NamedRange 控件, 事件"
  - "范围, 针对事件编程"
  - "工作表, 自动化"
  - "工作表, 更改单元格值"
  - "工作表, 事件"
ms.assetid: b69676f9-23b2-4ed6-83ab-8868c3f10948
caps.latest.revision: 57
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 56
---
# 演练：根据 NamedRange 控件的事件进行编程
  本演练演示如何使用 Visual Studio 中的 Office 开发工具将 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控件根据其事件使用方法添加到 Microsoft Office Excel 工作表和程序中。  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 通过本演练，您将学会如何执行以下任务：  
  
-   向工作表添加 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控件。  
  
-   对 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控件事件进行编程。  
  
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
  
1.  创建一个名为“My Named Range Events”的 Excel 工作簿项目。  确保已选择**“创建新文档”**。  有关更多信息，请参见[如何：在 Visual Studio 中创建 Office 项目](../vsto/how-to-create-office-projects-in-visual-studio.md)。  
  
     Visual Studio 在设计器中打开新的 Excel 工作簿，并将“My Named Range Events”（我的命名范围事件）项目添加到**“解决方案资源管理器”**中。  
  
## 向工作表添加文本和命名范围  
 由于宿主控件是扩展的 Office 对象，因此可以像添加本机对象那样将它们添加到文档中。  例如，通过打开**“插入”**菜单，指向**“名称”**，然后选择**“定义”**，可以将 Excel <xref:Microsoft.Office.Tools.Excel.NamedRange> 控件添加到工作表中。  也可以通过将 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控件从**“工具箱”**拖动到工作表上来添加该控件。  
  
 在此步骤中，您将使用**“工具箱”**向工作表添加两个命名范围控件，然后向工作表添加文本。  
  
#### 向工作表添加范围  
  
1.  验证 **my named Range Events.xlsx** 工作簿在 Visual Studio 中打开设计器，与 `Sheet1` 显示。  
  
2.  从“工具箱”的**“Excel 控件”**选项卡中，将一个 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控件拖动到 `Sheet1` 中的单元格**“A1”**中。  
  
     随即出现**“添加 NamedRange 控件”**对话框。  
  
3.  验证可编辑文本框中是否出现**“$A$1”**，并且已选中单元格**“A1”**。  如果没有，则请单击单元格**“A1”**选中它。  
  
4.  单击**“确定”**。  
  
     单元格**“A1”**即成为一个名为 `namedRange1` 的范围。  当选中单元格**“A1”**时，工作表上没有可见指示，但在**“名称”**框（就在左侧工作表的上面）中出现 `namedRange1`。  
  
5.  向单元格**“B3”**中添加另一个 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控件。  
  
6.  验证可编辑文本框中是否出现**“$B$3”**，并且已选中单元格**“B3”**。  如果没有，则请单击单元格**“B3”**选中它。  
  
7.  单击**“确定”**。  
  
     单元格**“B3”**变为名为 `namedRange2` 的范围。  
  
#### 向工作表添加文本  
  
1.  在单元格**“A1”**中键入以下文本：  
  
     这是 NamedRange 控件的一个示例。  
  
2.  在单元格**“A3”**（在 `namedRange2` 左侧）中键入以下文本：  
  
     事件：  
  
 在以下部分中，您将编写 `namedRange1` 的 <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick>、<xref:Microsoft.Office.Tools.Excel.NamedRange.Change> 和 <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange> 事件的响应代码，以向 `namedRange2` 插入文本和修改 `namedRange2` 控件的属性。  
  
## 添加代码以响应 BeforeDoubleClick 事件  
  
#### 基于 BeforeDoubleClick 事件向 NamedRange2 插入文本  
  
1.  在**“解决方案资源管理器”**中右击**“Sheet1.vb”**或**“Sheet1.cs”**，并选择**“查看代码”**。  
  
2.  添加适当代码，以使 `namedRange1_BeforeDoubleClick` 事件处理程序与以下所示类似：  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#24](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet1.cs#24)]
     [!code-vb[Trin_VstcoreHostControlsExcel#24](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet1.vb#24)]  
  
3.  在 C\# 中，必须按照下面的 <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> 事件所示添加命名范围事件处理程序。  有关创建事件处理程序的信息，请参见[如何：在 Office 项目中创建事件处理程序](../vsto/how-to-create-event-handlers-in-office-projects.md)。  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#25](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet1.cs#25)]  
  
## 添加代码以响应 Change 事件  
  
#### 基于 Change 事件向 namedRange2 插入文本  
  
1.  添加适当代码，以使 `NamedRange1_Change` 事件处理程序与以下所示类似：  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#26](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet1.cs#26)]
     [!code-vb[Trin_VstcoreHostControlsExcel#26](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet1.vb#26)]  
  
    > [!NOTE]  
    >  由于双击 Excel 范围中的单元格会进入编辑模式，因此当将选择移出该范围时，即使没有对文本做任何更改也会引发 <xref:Microsoft.Office.Tools.Excel.NamedRange.Change> 事件。  
  
## 添加代码以响应 SelectionChange 事件  
  
#### 基于 SelectionChange 事件向 namedRange2 插入文本  
  
1.  添加适当代码，以使**“NamedRange1\_SelectionChange”**事件处理程序与以下所示类似：  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#27](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet1.cs#27)]
     [!code-vb[Trin_VstcoreHostControlsExcel#27](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet1.vb#27)]  
  
    > [!NOTE]  
    >  由于双击 Excel 范围中的单元格会导致选择移至该范围内，因此在引发 <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick> 事件之前会引发 <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange> 事件。  
  
## 测试应用程序  
 现在可以测试工作簿，以验证当引发 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控件的事件时是否能将描述这些事件的文本插入到另一个命名范围中。  
  
#### 测试文档  
  
1.  按 F5 运行项目。  
  
2.  将光标放在 `namedRange1` 中，然后验证是否已将有关 <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange> 事件的文本以及注释插入到工作表中。  
  
3.  在 `namedRange1` 中双击，验证是否已使用红色斜体文本将有关 <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick> 事件的文本插入到 `namedRange2` 中。  
  
4.  在 `namedRange1` 外单击，注意当退出编辑模式时，即使没有对文本做任何更改，也会引发更改事件。  
  
5.  在 `namedRange1` 内更改文本。  
  
6.  在 `namedRange1` 外单击，验证是否已使用蓝色文本将有关 <xref:Microsoft.Office.Tools.Excel.NamedRange.Change> 事件的文本插入到 `namedRange2` 中。  
  
## 后续步骤  
 此演练演示对 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控件的事件进行编程的基本操作。  以下是接下来可能要执行的任务：  
  
-   部署项目。  有关更多信息，请参见[部署 Office 解决方案](../vsto/deploying-an-office-solution.md)。  
  
## 请参阅  
 [宿主项和宿主控件概述](../vsto/host-items-and-host-controls-overview.md)   
 [使用扩展对象实现 Excel 自动化](../vsto/automating-excel-by-using-extended-objects.md)   
 [NamedRange 控件](../vsto/namedrange-control.md)   
 [如何：调整 NamedRange 控件的大小](../vsto/how-to-resize-namedrange-controls.md)   
 [如何：向工作表添加 NamedRange 控件](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [宿主项和宿主控件的编程限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [如何：在 Office 项目中创建事件处理程序](../vsto/how-to-create-event-handlers-in-office-projects.md)  
  
  