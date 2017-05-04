---
title: "如何：向 Word 文档或 Excel 工作簿添加操作窗格 | Microsoft Docs"
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
  - "操作窗格 [Visual Studio 中的 Office 开发], 添加控件"
  - "操作窗格 [Visual Studio 中的 Office 开发], 在 Word 中创建"
  - "智能文档 [Visual Studio 中的 Office 开发], 添加控件"
  - "智能文档 [Visual Studio 中的 Office 开发], 在 Word 中创建"
ms.assetid: cea3c2b6-9364-4134-b812-50888ad8bd76
caps.latest.revision: 63
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 62
---
# 如何：向 Word 文档或 Excel 工作簿添加操作窗格
  若要操作窗格添加到 Microsoft Office Word 文档或 Microsoft Excel 工作簿，首先创建一个 Windows 窗体用户控件。  然后，将用户控件添加到 `ThisDocument.ActionsPane` 字段 \(Word\) 或 `ThisWorkbook.ActionsPane` 字段 \(Excel 工作表\) 的 <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> 属性在项目中。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
> [!NOTE]  
>  以下说明中的某些 Visual Studio 用户界面元素在计算机上出现的名称或位置可能会不同。  您安装的 Visual Studio 版本以及使用的设置决定了这些元素。  有关更多信息，请参见[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-cn/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
## 创建用户控件  
 下面的过程在 Word 或 Excel 项目演示如何创建用户控件。  它还将一个按钮添加到写入文本。对该文档或工作簿的用户控件，当单击该控件时。  
  
#### 创建用户控件  
  
1.  在 Visual Studio 中打开 Word 或 Excel 文档级项目。  
  
2.  在**“项目”**菜单上，单击**“添加新项”**。  
  
3.  在**“添加新项”**对话框中选择**“操作窗格控件”**，将其命名为**“HelloControl”**，然后单击**“添加”**。  
  
    > [!NOTE]  
    >  还可以向项目中添加**“用户控件”**项。  **“操作窗格控件”**项与**“用户控件”**项生成的类在功能上等效。  
  
4.  从**“工具箱”**的**“Windows 窗体”**选项卡中，将**“按钮”**控件拖到控件上。  
  
    > [!NOTE]  
    >  如果在设计器中看不到控件，请双击**“解决方案资源管理器”**中的**“HelloControl”**。  
  
5.  将代码添加到按钮的 <xref:System.Windows.Forms.Control.Click> 事件处理程序。  Microsoft Office Word 的下面的示例演示代码文档。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#12](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/HelloControl.cs#12)]
     [!code-vb[Trin_VstcoreActionsPaneWord#12](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/HelloControl.vb#12)]  
  
6.  在 C\# 中，必须为按钮单击添加一个事件处理程序。  可以将这些代码放在 `HelloControl` 构造函数中 `IntializeComponent` 调用的后面。  
  
     有关如何创建事件处理程序的信息，请参见[如何：在 Office 项目中创建事件处理程序](../vsto/how-to-create-event-handlers-in-office-projects.md)。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#13](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/HelloControl.cs#13)]  
  
## 将用户控件添加到操作窗格中  
 若要显示操作窗格，请将用户控件添加到 `ThisDocument.ActionsPane` 字段 \(Word\) 或 `ThisWorkbook.ActionsPane` 字段 \(Excel 工作表\) 的 <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> 属性。  
  
#### 将用户控件添加到操作窗格中  
  
1.  将以下代码添加到 `ThisDocument` 或 `ThisWorkbook` 选件类作为一个选件类级声明 \(不要将此代码添加到方法中\)。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#14](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ThisDocument.cs#14)]
     [!code-vb[Trin_VstcoreActionsPaneWord#14](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ThisDocument.vb#14)]  
  
2.  将以下代码添加到 `ThisDocument` 选件类的 `ThisDocument_Startup` 事件处理程序或 `ThisWorkbook` 选件类的 `ThisWorkbook_Startup` 事件处理程序。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#15](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ThisDocument.cs#15)]
     [!code-vb[Trin_VstcoreActionsPaneWord#15](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ThisDocument.vb#15)]  
  
## 请参阅  
 [操作窗格概述](../vsto/actions-pane-overview.md)   
 [演练：从操作窗格将文本插入到文档中](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)   
 [如何：管理操作窗格上的控件布局](../vsto/how-to-manage-control-layout-on-actions-panes.md)   
 [演练：从操作窗格将文本插入到文档中](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)  
  
  