---
title: "如何：管理操作窗格上的控件布局"
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
  - "操作窗格 [Visual Studio 中的 Office 开发], 控件布局"
  - "控件 [Visual Studio 中的 Office 开发], 操作窗格上的布局"
  - "智能文档 [Visual Studio 中的 Office 开发], 控件布局"
ms.assetid: 857550d0-b9c0-4d2f-a947-dd955bcf2823
caps.latest.revision: 59
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 55
---
# 如何：管理操作窗格上的控件布局
  默认情况下，操作窗格停靠在文档或工作表的右侧；但也可以将其停靠在左侧、顶部或底部。  如果使用多个用户控件，则可以编写代码以在操作窗格上适当地堆叠用户控件。  有关更多信息，请参见[操作窗格概述](../vsto/actions-pane-overview.md)。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 这些控件的堆叠顺序取决于操作窗格是垂直停靠还是水平停靠。  
  
> [!NOTE]  
>  如果用户在运行时会调整操作窗格的大小，则可以设置控件，使其可随操作窗格一起调整大小。  可以使用 Windows 窗体控件的 <xref:System.Windows.Forms.Control.Anchor%2A> 属性将控件锚定到操作窗格。  有关更多信息，请参见[如何：在 Windows 窗体上锚定控件](http://msdn.microsoft.com/library/59ea914f-fbd3-427a-80fe-decd02f7ae6d)。  
  
> [!NOTE]  
>  以下说明中的某些 Visual Studio 用户界面元素在计算机上出现的名称或位置可能会不同。  您安装的 Visual Studio 版本以及使用的设置决定了这些元素。  有关更多信息，请参见[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-cn/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
### 设置操作窗格控件的堆叠顺序  
  
1.  打开 Microsoft Office Word 的文档级项目，该项目包含一个具有多个用户控件或嵌套操作窗格控件的操作窗格。  有关更多信息，请参见[如何：向 Word 文档或 Excel 工作簿添加操作窗格](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)。  
  
2.  在**“解决方案资源管理器”**中，右击**“ThisDocument.cs”**或**“ThisDocument.vb”**，然后单击**“查看代码”**。  
  
3.  在操作窗格的 <xref:Microsoft.Office.Tools.ActionsPane.OrientationChanged> 事件处理程序中检查操作窗格的方向是否为水平。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#30](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ThisDocument.cs#30)]
     [!code-vb[Trin_VstcoreActionsPaneWord#30](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ThisDocument.vb#30)]  
  
4.  如果方向为水平，则从左侧开始堆叠操作窗格控件；否则将从顶部开始堆叠控件。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#31](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ThisDocument.cs#31)]
     [!code-vb[Trin_VstcoreActionsPaneWord#31](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ThisDocument.vb#31)]  
  
5.  在 C\# 中，必须向 <xref:Microsoft.Office.Tools.Word.Document.Startup> 事件处理程序添加 `ActionsPane` 的事件处理程序。  有关创建事件处理程序的信息，请参见[如何：在 Office 项目中创建事件处理程序](../vsto/how-to-create-event-handlers-in-office-projects.md)。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#32](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ThisDocument.cs#32)]  
  
6.  运行项目，并确认当操作窗格停靠在文档项部时，操作窗格控件从左到右堆叠，而当操作窗格停靠在文档右侧时，操作窗格控件从上到下堆叠。  
  
## 示例  
 [!code-csharp[Trin_VstcoreActionsPaneWord#29](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ThisDocument.cs#29)]
 [!code-vb[Trin_VstcoreActionsPaneWord#29](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ThisDocument.vb#29)]  
  
## 编译代码  
 此示例需要：  
  
-   一个具有包含多个用户控件或嵌套操作窗格控件的操作窗格的 Word 文档级项目。  
  
## 请参阅  
 [操作窗格概述](../vsto/actions-pane-overview.md)   
 [如何：向 Word 文档或 Excel 工作簿添加操作窗格](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [如何：向 Word 文档或 Excel 工作簿添加操作窗格](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [演练：从操作窗格将文本插入到文档中](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)   
 [演练：从操作窗格将文本插入到文档中](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)  
  
  