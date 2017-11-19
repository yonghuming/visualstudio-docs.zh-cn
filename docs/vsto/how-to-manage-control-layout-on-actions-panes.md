---
title: "如何： 管理操作窗格上的控件布局 |Microsoft 文档"
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
- actions panes [Office development in Visual Studio], control layout
- controls [Office development in Visual Studio], layout on actions panes
- smart documents [Office development in Visual Studio], control layout
ms.assetid: 857550d0-b9c0-4d2f-a947-dd955bcf2823
caps.latest.revision: "59"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: dbc6f8876236d1a056874500aea4878f9643f91b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-manage-control-layout-on-actions-panes"></a>如何：管理操作窗格上的控件布局
  操作窗格停靠右侧的文档或工作表上，默认设置。但是，它可以停靠到左侧、 顶部或底部。 如果使用多个用户控件，你可以编写代码以堆叠上操作窗格的用户控件。 有关更多信息，请参见 [Actions Pane Overview](../vsto/actions-pane-overview.md)。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 控件的堆叠顺序取决于是否操作窗格是垂直停靠还是水平停靠。  
  
> [!NOTE]  
>  如果用户在运行时调整大小操作窗格中，你可以设置与操作窗格中调整大小的控件。 你可以使用 Windows 窗体控件的 <xref:System.Windows.Forms.Control.Anchor%2A> 属性将控件定位到操作窗格。 有关详细信息，请参阅[如何： 在 Windows 窗体上定位控件](/dotnet/framework/winforms/controls/how-to-anchor-controls-on-windows-forms)。  
  
> [!NOTE]  
>  以下说明中的某些 Visual Studio 用户界面元素在计算机上出现的名称或位置可能会不同。 这些元素取决于你所使用的 Visual Studio 版本和你所使用的设置。 有关详细信息，请参阅[个性化设置 Visual Studio IDE](../ide/personalizing-the-visual-studio-ide.md)。  
  
### <a name="to-set-the-stack-order-of-the-actions-pane-controls"></a>若要设置的操作窗格控件的堆叠顺序  
  
1.  包括具有多个用户控件或嵌套的操作窗格控件操作窗格中的 Microsoft Office word 中打开的文档级项目。 有关详细信息，请参阅[如何： 将操作窗格添加到 Word 文档或 Excel 工作簿](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)。  
  
2.  右键单击**ThisDocument.cs**或**ThisDocument.vb**中**解决方案资源管理器**，然后单击**查看代码**。  
  
3.  在<xref:Microsoft.Office.Tools.ActionsPane.OrientationChanged>事件处理程序的操作窗格中，检查是否在操作窗格的方向为水平方向。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#30](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#30)]
     [!code-vb[Trin_VstcoreActionsPaneWord#30](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#30)]  
  
4.  如果方向为水平，堆栈左侧; 从操作窗格控件否则，从顶部堆叠它们。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#31](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#31)]
     [!code-vb[Trin_VstcoreActionsPaneWord#31](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#31)]  
  
5.  在 C# 中，你必须添加的事件处理程序`ActionsPane`到<xref:Microsoft.Office.Tools.Word.Document.Startup>事件处理程序。 有关创建事件处理程序的信息，请参阅[如何： 在 Office 项目中创建事件处理程序](../vsto/how-to-create-event-handlers-in-office-projects.md)。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#32](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#32)]  
  
6.  运行该项目并验证时操作窗格停靠在顶部的文档，然后将控件堆积从顶部到底部的操作窗格停靠在文档的右侧时，操作窗格控件的堆叠从左到右。  
  
## <a name="example"></a>示例  
 [!code-csharp[Trin_VstcoreActionsPaneWord#29](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#29)]
 [!code-vb[Trin_VstcoreActionsPaneWord#29](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#29)]  
  
## <a name="compiling-the-code"></a>编译代码  
 此示例需要：  
  
-   Word 文档级项目与包含多个用户控件的操作窗格或嵌套的操作窗格控件。  
  
## <a name="see-also"></a>另请参阅  
 [操作窗格概述](../vsto/actions-pane-overview.md)   
 [如何： 向 Word 文档或 Excel 工作簿添加操作窗格](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [如何： 向 Word 文档或 Excel 工作簿添加操作窗格](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [演练： 将文本插入到操作窗格中的文档](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)   
 [演练：将文本从操作窗格插入到文档](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)  
  
  