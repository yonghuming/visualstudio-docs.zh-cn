---
title: "如何： 将操作窗格添加到 Word 文档或 Excel 工作簿 |Microsoft 文档"
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
- smart documents [Office development in Visual Studio], creating in Word
- smart documents [Office development in Visual Studio], adding controls
- actions panes [Office development in Visual Studio], creating in Word
- actions panes [Office development in Visual Studio], adding controls
ms.assetid: cea3c2b6-9364-4134-b812-50888ad8bd76
caps.latest.revision: "63"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ffdb997bbff96e99a456f7d4679a5da0e446ee4a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks"></a>如何：向 Word 文档或 Excel 工作簿添加操作窗格
  若要将操作窗格添加到 Microsoft Office Word 文档或 Microsoft Excel 工作簿，首先创建 Windows 窗体用户控件。 然后，用户将控件添加到<xref:Microsoft.Office.Tools.ActionsPane.Controls%2A>属性`ThisDocument.ActionsPane`字段 (Word) 或`ThisWorkbook.ActionsPane`你的项目中的字段 (Excel)。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
> [!NOTE]  
>  以下说明中的某些 Visual Studio 用户界面元素在计算机上出现的名称或位置可能会不同。 这些元素取决于你所使用的 Visual Studio 版本和你所使用的设置。 有关详细信息，请参阅[个性化设置 Visual Studio IDE](../ide/personalizing-the-visual-studio-ide.md)。  
  
## <a name="creating-the-user-control"></a>创建用户控件  
 下面的过程演示如何创建用户控件在 Word 或 Excel 项目。 它还添加到将文本写入的文档或工作簿上，单击时其用户控件的一个按钮。  
  
#### <a name="to-create-the-user-control"></a>若要创建用户控件  
  
1.  在 Visual Studio 中打开 Word 或 Excel 文档级项目。  
  
2.  在 **“项目”** 菜单上，单击 **“添加新项”**。  
  
3.  在**添加新项**对话框中，选择**操作窗格控件**，将其命名为**HelloControl**，然后单击**添加**。  
  
    > [!NOTE]  
    >  还可以添加**用户控件**到你的项目的项。 通过生成的类**操作窗格控件**和**用户控件**项在功能上等效。  
  
4.  从**Windows 窗体**选项卡**工具箱中，**拖动**按钮**拖到控件的控件。  
  
    > [!NOTE]  
    >  如果控件不可见设计器中，双击**HelloControl**中**解决方案资源管理器**。  
  
5.  将代码添加到<xref:System.Windows.Forms.Control.Click>按钮事件处理程序。 下面的示例显示 Microsoft Office Word 文档的代码。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#12](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/HelloControl.cs#12)]
     [!code-vb[Trin_VstcoreActionsPaneWord#12](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/HelloControl.vb#12)]  
  
6.  在 C# 中，你必须添加为按钮单击事件处理程序。 你可以将此代码放置在`HelloControl`构造函数调用的后面`IntializeComponent`。  
  
     有关如何创建事件处理程序的信息，请参阅[如何： 在 Office 项目中创建事件处理程序](../vsto/how-to-create-event-handlers-in-office-projects.md)。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#13](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/HelloControl.cs#13)]  
  
## <a name="adding-the-user-control-to-the-actions-pane"></a>将用户控件添加到操作窗格  
 若要显示操作窗格中，用户将控件添加到<xref:Microsoft.Office.Tools.ActionsPane.Controls%2A>属性`ThisDocument.ActionsPane`字段 (Word) 或`ThisWorkbook.ActionsPane`字段 (Excel)。  
  
#### <a name="to-add-the-user-control-to-the-actions-pane"></a>将用户控件添加到操作窗格  
  
1.  以下代码添加到`ThisDocument`或`ThisWorkbook`作为类级别声明的类 （不添加此代码的方法）。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#14](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#14)]
     [!code-vb[Trin_VstcoreActionsPaneWord#14](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#14)]  
  
2.  以下代码添加到`ThisDocument_Startup`事件处理程序`ThisDocument`类或`ThisWorkbook_Startup`事件处理程序`ThisWorkbook`类。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#15](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#15)]
     [!code-vb[Trin_VstcoreActionsPaneWord#15](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#15)]  
  
## <a name="see-also"></a>另请参阅  
 [操作窗格概述](../vsto/actions-pane-overview.md)   
 [演练： 将文本插入到操作窗格中的文档](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)   
 [如何： 管理操作窗格上的控件布局](../vsto/how-to-manage-control-layout-on-actions-panes.md)   
 [演练：将文本从操作窗格插入到文档](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)  
  
  