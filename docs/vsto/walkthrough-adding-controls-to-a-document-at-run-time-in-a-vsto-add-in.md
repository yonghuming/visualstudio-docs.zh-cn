---
title: "演练： 在运行时在 VSTO 外接程序向文档添加控件 |Microsoft 文档"
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
- add-ins [Office development in Visual Studio], adding controls
- application-level add-ins [Office development in Visual Studio], adding controls
- controls [Office development in Visual Studio], adding to documents at run time
- documents [Office development in Visual Studio], adding controls at run time
ms.assetid: ab6dff40-9964-468a-938c-a71a3ac23718
caps.latest.revision: "29"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 0d220cca9ddd08004540768bbeb7322d28dedaa8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-adding-controls-to-a-document-at-run-time-in-a-vsto-add-in"></a>演练：运行时在 VSTO 外接程序中将控件添加到文档
  你可以使用 VSTO 外接程序向任何打开的 Microsoft Office Word 文档添加控件。 本演练演示如何使用功能区来允许用户向文档添加 <xref:Microsoft.Office.Tools.Word.Controls.Button> 或 <xref:Microsoft.Office.Tools.Word.RichTextContentControl> 。  
  
 **适用于：** 本主题中的信息适用于 Word 2010 的 VSTO 外接程序项目。 有关更多信息，请参见 [Features Available by Office Application and Project Type](../vsto/features-available-by-office-application-and-project-type.md)。  
  
 本演练阐释了以下任务：  
  
-   创建新的 Word VSTO 外接程序项目。  
  
-   提供用于向文档添加控件的用户界面 (UI)。  
  
-   在运行时向文档添加控件。  
  
-   从文档中删除控件。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>先决条件  
 你需要以下组件来完成本演练：  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] 或 [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)]。  
  
## <a name="creating-a-new-word-add-in-project"></a>创建新的 Word 外接程序项目  
 首先创建 Word VSTO 外接程序项目。  
  
#### <a name="to-create-a-new-word-vsto-add-in-project"></a>创建新的 Word VSTO 外接程序项目  
  
1.  为 Word 创建一个名为 **WordDynamicControls**的 VSTO 外接程序项目。 有关详细信息，请参阅 [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)。  
  
2.  添加对 **Microsoft.Office.Tools.Word.v4.0.Utilities.dll** 程序集的引用。 在本演练后面的部分中，需要此引用才能以编程方式向文档中添加 Windows 窗体控件。  
  
## <a name="providing-a-ui-to-add-controls-to-a-document"></a>提供用于向文档添加控件的 UI  
 向 Word 的功能区添加一个自定义选项卡。 用户可以通过选中该选项卡上的复选框来向文档添加控件。  
  
#### <a name="to-provide-a-ui-to-add-controls-to-a-document"></a>若要提供用于向文档添加控件的 UI  
  
1.  在 **“项目”** 菜单上，单击 **“添加新项”**。  
  
2.  在 **“添加新项”** 对话框中，选择 **“功能区(可视化设计器)”**。  
  
3.  将新功能区更名为 **“MyRibbon”**，然后单击 **“添加”**。  
  
     **MyRibbon.cs** 或 **MyRibbon.vb** 文件将在功能区设计器中打开，并显示一个默认选项卡和组。  
  
4.  在功能区设计器中，单击“group1”  组。  
  
5.  在“属性”  窗口中，将“group1”  的“Label”  属性更改为“添加控件” 。  
  
6.  从“工具箱”  的“Office 功能区控件” 选项卡中将“CheckBox”  控件拖到“group1” 上。  
  
7.  单击 **CheckBox1** 以将其选中。  
  
8.  在 **“属性”** 窗口中，更改下列属性。  
  
    |属性|值|  
    |--------------|-----------|  
    |**名称**|**addButtonCheckBox**|  
    |**标签**|**“添加”按钮**|  
  
9. 将第二个复选框添加到 **group1**，然后更改下列属性。  
  
    |属性|值|  
    |--------------|-----------|  
    |**名称**|**addRichTextCheckBox**|  
    |**标签**|**添加 RTF 控件**|  
  
10. 在功能区设计器中，双击“添加按钮” 。  
  
     “添加按钮” <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click>**复选框的** 事件处理程序将在代码编辑器中打开。  
  
11. 返回到功能区设计器，并双击“添加 RTF 控件” 。  
  
     “添加 RTF 控件” <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click>**复选框的** 事件处理程序将在代码编辑器中打开。  
  
 在本演练后面的部分中，你将向这些事件处理程序添加代码，以在活动文档中添加和删除控件。  
  
## <a name="adding-and-removing-controls-on-the-active-document"></a>在活动文档中添加和删除控件  
 在 VSTO 外接程序代码中，你必须先将活动文档转换为 <xref:Microsoft.Office.Tools.Word.Document>*宿主项* ，然后才能添加控件。 在 Office 解决方案中，只能将托管控件添加到充当控件容器的宿主项中。 在 VSTO 外接程序项目中，主机项可以创建在运行时通过使用 GetVstoObject 方法。  
  
 向 `ThisAddIn` 类添加相应的方法，调用这些方法可在活动文档中添加或删除 <xref:Microsoft.Office.Tools.Word.Controls.Button> 或 <xref:Microsoft.Office.Tools.Word.RichTextContentControl> 。 在本演练后面的部分中，你将在功能区中从复选框的 <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click> 事件处理程序调用这些方法。  
  
#### <a name="to-add-and-remove-controls-on-the-active-document"></a>若要在活动文档中添加和删除控件  
  
1.  在“解决方案资源管理器” 中，双击 ThisAddIn.cs 或 ThisAddIn.vb，以在代码编辑器中打开该文件。  
  
2.  向 `ThisAddIn` 类添加下面的代码。 此代码声明 <xref:Microsoft.Office.Tools.Word.Controls.Button> 和 <xref:Microsoft.Office.Tools.Word.RichTextContentControl> 对象，这两个对象表示将要添加到文档中的控件。  
  
     [!code-vb[Trin_WordAddInDynamicControlsWalkthrough#1](../vsto/codesnippet/VisualBasic/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.vb#1)]
     [!code-csharp[Trin_WordAddInDynamicControlsWalkthrough#1](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.cs#1)]  
  
3.  将以下方法添加到 `ThisAddIn` 类。 当用户单击功能区中的“添加按钮”  复选框时，如果选中了该复选框，此方法会向文档中的当前选定内容添加一个 <xref:Microsoft.Office.Tools.Word.Controls.Button> ；如果清除了该复选框，此方法会删除 <xref:Microsoft.Office.Tools.Word.Controls.Button> 。  
  
     [!code-vb[Trin_WordAddInDynamicControlsWalkthrough#2](../vsto/codesnippet/VisualBasic/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.vb#2)]
     [!code-csharp[Trin_WordAddInDynamicControlsWalkthrough#2](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.cs#2)]  
  
4.  将以下方法添加到 `ThisAddIn` 类。 当用户单击功能区中的“添加 RTF 控件”  复选框时，如果选中了该复选框，此方法会向文档中的当前选定内容添加一个 <xref:Microsoft.Office.Tools.Word.RichTextContentControl> ；如果清除了该复选框，此方法会删除 <xref:Microsoft.Office.Tools.Word.RichTextContentControl> 。  
  
     [!code-vb[Trin_WordAddInDynamicControlsWalkthrough#3](../vsto/codesnippet/VisualBasic/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.vb#3)]
     [!code-csharp[Trin_WordAddInDynamicControlsWalkthrough#3](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.cs#3)]  
  
## <a name="removing-the-button-control-when-the-document-is-saved"></a>保存文档后删除 Button 控件  
 保存并关闭文档后，Windows 窗体控件不会保留在文档中。 但是，每个控件的 ActiveX 包装会保留在文档中，并且重新打开文档后，最终用户会看到各包装的边框。 可通过多种方法清除在 VSTO 外接程序中动态创建的 Windows 窗体控件。在本演练中，你将以编程方式在保存文档后删除 <xref:Microsoft.Office.Tools.Word.Controls.Button> 控件。  
  
#### <a name="to-remove-the-button-control-when-the-document-is-saved"></a>保存文档后删除 Button 控件  
  
1.  在 ThisAddIn.cs 或 ThisAddIn.vb 代码文件中，将下面的方法添加到 `ThisAddIn` 类中。 此方法是 <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> 事件的事件处理程序。 如果保存的文档有一个与之关联的 <xref:Microsoft.Office.Tools.Word.Document> 宿主项，该事件处理程序会获取此宿主项，并删除 <xref:Microsoft.Office.Tools.Word.Controls.Button> 控件（如果存在）。  
  
     [!code-vb[Trin_WordAddInDynamicControlsWalkthrough#4](../vsto/codesnippet/VisualBasic/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.vb#4)]
     [!code-csharp[Trin_WordAddInDynamicControlsWalkthrough#4](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.cs#4)]  
  
2.  在 C# 中，将下面的代码添加到 `ThisAddIn_Startup` 事件处理程序中。 在 C# 中，此代码是必需的，用于连接 `Application_DocumentBeforeSave` 事件处理程序和 <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> 事件。  
  
     [!code-csharp[Trin_WordAddInDynamicControlsWalkthrough#5](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.cs#5)]  
  
## <a name="adding-and-removing-controls-when-the-user-clicks-the-check-boxes-on-the-ribbon"></a>用户单击功能区中的复选框时添加和删除控件  
 最后，修改添加到功能区中的复选框的 <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click> 事件处理程序，以在文档中添加或删除控件。  
  
#### <a name="to-add-or-remove-controls-when-the-user-clicks-the-check-boxes-on-the-ribbon"></a>用户单击功能区中的复选框时添加或删除控件  
  
1.  在 MyRibbon.cs 或 MyRibbon.vb 代码文件中，将生成的 `addButtonCheckBox_Click` 和 `addRichTextCheckBox_Click` 事件处理程序替换为下面的代码。 此代码重新定义这些事件处理程序，以调用之前在本演练中添加到 `ToggleButtonOnDocument` 类中的 `ToggleRichTextControlOnDocument` 和 `ThisAddIn` 方法。  
  
     [!code-vb[Trin_WordAddInDynamicControlsWalkthrough#6](../vsto/codesnippet/VisualBasic/Trin_WordAddInDynamicControlsWalkthrough/MyRibbon.vb#6)]
     [!code-csharp[Trin_WordAddInDynamicControlsWalkthrough#6](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControlsWalkthrough/MyRibbon.cs#6)]  
  
## <a name="testing-the-solution"></a>测试解决方案  
 通过在功能区的自定义选项卡中选择控件来向文档添加控件。 保存文档后， <xref:Microsoft.Office.Tools.Word.Controls.Button> 控件会被删除。  
  
#### <a name="to-test-the-solution"></a>若要测试解决方案。  
  
1.  按 F5 运行项目。  
  
2.  在活动文档中，多次按 Enter 以向文档添加新的空段落。  
  
3.  选择第一个段落。  
  
4.  单击 **“外接程序”** 选项卡。  
  
5.  在“添加控件”  组中，单击“添加按钮” 。  
  
     一个按钮随即显示在第一个段落中。  
  
6.  选择最后一个段落。  
  
7.  在“添加控件”  组中，单击“添加 RTF 控件” 。  
  
     一个 RTF 内容控件随即添加到最后一个段落中。  
  
8.  保存文档。  
  
     按钮随即从文档中删除。  
  
## <a name="next-steps"></a>后续步骤  
 你可以从以下主题中了解有关 VSTO 外接程序中的控件的详细信息：  
  
-   有关演示如何在运行时向文档添加许多其他类型的控件以及在重新打开文档后重新创建控件的示例，请参阅 [Office Development Samples and Walkthroughs](../vsto/office-development-samples-and-walkthroughs.md)中的“Word 外接程序动态控件示例”。  
  
-   有关演示如何将控件添加到工作表，VSTO 外接程序中使用 for Excel 的演练，请参阅[演练： 将控件添加到工作表中在运行时在 VSTO 外接程序项目](../vsto/walkthrough-adding-controls-to-a-worksheet-at-run-time-in-vsto-add-in-project.md)。  
  
## <a name="see-also"></a>另请参阅  
 [Word 解决方案](../vsto/word-solutions.md)   
 [在运行时向 Office 文档添加控件](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [在 Office 文档中保留动态控件](../vsto/persisting-dynamic-controls-in-office-documents.md)   
 [如何： 添加 Windows 窗体控件添加到 Office 文档](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
 [如何： 向 Word 文档添加内容控件](../vsto/how-to-add-content-controls-to-word-documents.md)   
 [在运行时在 VSTO 外接程序中扩展 Word 文档和 Excel 工作簿](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)  
  
  