---
title: "演练： 更改文档格式使用复选框控件 |Microsoft 文档"
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
- Word documents, changing formatting using controls
- documents [Office development in Visual Studio], formatting
- check boxes, Word documents
- documents [Office development in Visual Studio], check box controls
- controls [Office development in Visual Studio], adding to documents
ms.assetid: 3740e41d-a57e-43bb-87e7-6e5481ef290b
caps.latest.revision: "70"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: cf214f2ffc55cf0846373fcaa226253f276e3d69
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-changing-document-formatting-using-checkbox-controls"></a>演练：使用 CheckBox 控件更改文档格式设置
  本演练演示如何在 Microsoft Office Word 的文档级自定义项中使用 Windows 窗体控件来更改格式设置的文本。  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 本演练阐释了以下任务：  
  
-   在设计时向文档级项目中的文档添加文本和控件。  
  
-   设置文本格式时选择了某个选项。  
  
 若要查看结果为已完成的示例，请参阅在 Word 控件示例[Office 开发示例和演练](../vsto/office-development-samples-and-walkthroughs.md)。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>先决条件  
 你需要以下组件来完成本演练：  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] 或 [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)]。  
  
## <a name="creating-the-project"></a>创建项目  
 第一步是创建 Word 文档项目。  
  
#### <a name="to-create-a-new-project"></a>创建新项目  
  
1.  使用名称创建的 Word 文档项目**我的 Word 格式**。 在向导中，选择**创建新文档**。  
  
     有关详细信息，请参阅 [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)。  
  
     Visual Studio 将在设计器中打开新的 Word 文档和添加**我的 Word 格式**项目合并为**解决方案资源管理器**。  
  
## <a name="adding-text-and-controls-to-the-word-document"></a>将文本和控件添加到 Word 文档  
 对于本演练中，添加三个复选框和中的某些文本<xref:Microsoft.Office.Tools.Word.Bookmark>控件添加到 Word 文档。 复选框将向用户显示选项，用于设置文本格式。  
  
#### <a name="to-add-three-check-boxes"></a>若要添加三个复选框  
  
1.  验证该文档已在 Visual Studio 设计器中打开。  
  
2.  从**公共控件**选项卡**工具箱**，将第一个<xref:Microsoft.Office.Tools.Word.Controls.CheckBox>控件添加到文档。  
  
3.  在 **“属性”** 窗口中，更改下列属性。  
  
    |属性|值|  
    |--------------|-----------|  
    |**Name**|**applyBoldFont**|  
    |**“文本”**|**加粗**|  
  
4.  按**Enter**移动第一个复选框下面的插入点。  
  
5.  将第二个复选框添加到下面的文档`ApplyBoldFont`复选框并更改以下属性。  
  
    |属性|值|  
    |--------------|-----------|  
    |**Name**|**applyItalicFont**|  
    |**“文本”**|**斜体**|  
  
6.  按**Enter**移动插入点下面第二个复选框。  
  
7.  将第三个复选框添加到下面的文档`ApplyItalicFont`复选框并更改以下属性。  
  
    |属性|值|  
    |--------------|-----------|  
    |**Name**|**applyUnderlineFont**|  
    |**“文本”**|**下划线**|  
  
#### <a name="to-add-text-and-a-bookmark-control"></a>若要添加文本和书签控件  
  
1.  将插入点下面的复选框控件移动，并键入以下文本：  
  
     **单击复选框来更改此文本的格式设置。**  
  
2.  从**Word 控件**选项卡**工具箱**，拖动<xref:Microsoft.Office.Tools.Word.Bookmark>控件添加到文档。  
  
     **添加书签控件**对话框随即出现。  
  
3.  选择添加到文档的文本，然后单击**确定**。  
  
     A<xref:Microsoft.Office.Tools.Word.Bookmark>控件名为**Bookmark1**添加到文档中选定的文本。  
  
4.  在**属性**窗口中，更改的值**（名称）**属性**fontText。**  
  
 接下来，编写代码以设置文本格式时选中或清除复选框。  
  
## <a name="formatting-the-text-when-a-check-box-is-checked-or-cleared"></a>选中或清除格式文本复选框时是  
 当用户选择的格式设置选项，则更改文档中文本的格式。  
  
#### <a name="to-change-formatting-when-a-check-box-is-selected"></a>若要更改格式设置复选框时被选择  
  
1.  右键单击`ThisDocument`中**解决方案资源管理器**，然后单击**查看代码**快捷菜单上。  
  
2.  仅适用于 C#，添加以下常量**ThisDocument**类。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#2](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#2)]  
  
3.  以下代码添加到<xref:System.Windows.Forms.Control.Click>事件处理程序`applyBoldFont`复选框。  
  
     [!code-vb[Trin_VstcoreProgrammingControlsWord#3](../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb#3)]
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#3](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#3)]  
  
4.  以下代码添加到<xref:System.Windows.Forms.Control.Click>事件处理程序`applyItalicFont`复选框。  
  
     [!code-vb[Trin_VstcoreProgrammingControlsWord#4](../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb#4)]
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#4](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#4)]  
  
5.  以下代码添加到<xref:System.Windows.Forms.Control.Click>事件处理程序`applyUnderlineFont`复选框。  
  
     [!code-vb[Trin_VstcoreProgrammingControlsWord#5](../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb#5)]
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#5](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#5)]  
  
6.  必须在 C# 中，添加事件处理程序的文本框<xref:Microsoft.Office.Tools.Word.Document.Startup>事件。 有关如何创建事件处理程序的信息，请参阅[如何： 在 Office 项目中创建事件处理程序](../vsto/how-to-create-event-handlers-in-office-projects.md)。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#6](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#6)]  
  
## <a name="testing-the-application"></a>测试应用程序  
 你现在可以测试你的文档，以验证在选择或清除复选框文本的格式设置正确。  
  
#### <a name="to-test-your-document"></a>测试文档  
  
1.  按 F5 运行项目。  
  
2.  选中或清除复选框。  
  
3.  确认文本格式正确。  
  
## <a name="next-steps"></a>后续步骤  
 本演练演示了使用复选框以及以编程方式更改文本在 Word 文档格式设置的基础知识。 以下是接下来可能要执行的一些任务：  
  
-   使用按钮填充文本框。 有关详细信息，请参阅[演练： 在文档使用按钮的文本框中显示的文本](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-document-using-a-button.md)。  
  
-   使用单选按钮以选择图表样式。 有关详细信息，请参阅[演练： 更新文档使用单选按钮中的图表](../vsto/walkthrough-updating-a-chart-in-a-document-using-radio-buttons.md)。  
  
-  
  
## <a name="see-also"></a>另请参阅  
 [使用 Word 的演练](../vsto/walkthroughs-using-word.md)   
 [Office 开发示例和演练](../vsto/office-development-samples-and-walkthroughs.md)   
 [NamedRange 控件](../vsto/namedrange-control.md)   
 [Office 文档上的 Windows 窗体控件限制](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)  
  
  