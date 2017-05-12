---
title: "演练：从操作窗格将文本插入到文档中"
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
ms.assetid: fd14c896-5737-4a20-94f7-6064b67112c5
caps.latest.revision: 70
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 69
---
# 演练：从操作窗格将文本插入到文档中
  此演练演示如何在 Microsoft Office Word 文档中创建操作窗格。  操作窗格包含两个控件，用于收集输入并随后将文本发送到文档。  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 本演练阐释了以下任务：  
  
-   在操作窗格控件上使用 Windows 窗体控件来设计界面。  
  
-   打开应用程序时显示操作窗格。  
  
> [!NOTE]  
>  以下说明中的某些 Visual Studio 用户界面元素在计算机上出现的名称或位置可能会不同。  您安装的 Visual Studio 版本以及使用的设置决定了这些元素。  有关更多信息，请参见[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-cn/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
## 系统必备  
 您需要以下组件来完成本演练：  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] 或 [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)]。  
  
## 创建项目  
 第一步是创建 Word 文档项目。  
  
#### 创建新项目  
  
1.  创建一个 Word 文档项目，并将其命名为“My Basic Actions Pane”。  在向导中，选择**“创建新文档”**。  有关更多信息，请参见[如何：在 Visual Studio 中创建 Office 项目](../vsto/how-to-create-office-projects-in-visual-studio.md)。  
  
     Visual Studio 将在设计器中打开新的 Word 文档，并将**“My Basic Actions Pane”**项目添加到**“解决方案资源管理器”**中。  
  
## 向文档中添加文本和书签  
 操作窗格将向文档中的书签发送文本。  若要设计文档，请键入一些文本以创建基本窗体。  
  
#### 向文档中添加文本  
  
1.  在 Word 文档中键入以下文本：  
  
     March 21, 2008  
  
     名称  
  
     地址  
  
     这是 Word 中基本操作窗格的示例。  
  
 通过将 <xref:Microsoft.Office.Tools.Word.Bookmark> 控件从 Visual Studio 中的**“工具箱”**拖动到文档中或使用 Word 中的**“书签”**对话框，可以将该控件添加到文档中。  
  
#### 向文档中添加 Bookmark 控件  
  
1.  从**“工具箱”**的**“Word 控件”**选项卡中，将一个 <xref:Microsoft.Office.Tools.Word.Bookmark> 控件拖动到文档中。  
  
     将出现**“添加书签控件”**对话框。  
  
2.  选择单词**“Name”**，而不选择段落标记，然后单击**“确定”**。  
  
    > [!NOTE]  
    >  段落标记应该在书签之外。  如果段落标记在文档中不可见，请单击**“工具”**菜单，指向**“Microsoft Office Word Tools”**，然后单击**“选项”**。  单击**“视图”**选项卡，然后在**“选项”**对话框的**“格式化标记”**区域中选择**“段落标记”**复选框。  
  
3.  在**“属性”**窗口中，将**“Bookmark1”**的**“Name”**属性更改为 **showName**。  
  
4.  选择单词**“Address”**，而不选择段落标记。  
  
5.  在功能区的**“插入”**选项卡上的**“链接”**组中，单击**“书签”**。  
  
6.  在**“书签”**对话框的**“书签名”**框中键入 **showAddress**，然后单击**“添加”**。  
  
## 向操作窗格中添加控件  
 若要设计操作窗格界面，请向项目中添加操作窗格控件，然后向操作窗格控件添加 Windows 窗体控件。  
  
#### 添加操作窗格控件  
  
1.  在**“解决方案资源管理器”**中选择**“My Basic Actions Pane”**项目。  
  
2.  在**“项目”**菜单上，单击**“添加新项”**。  
  
3.  在**“添加新项”**对话框中单击**“操作窗格控件”**，并将该控件命名为**“InsertTextControl”**，然后单击**“添加”**。  
  
#### 向操作窗格控件添加 Windows 窗体控件  
  
1.  如果操作窗格控件在设计器中不可见，请双击**“InsertTextControl”**。  
  
2.  从**“工具箱”**的**“公共控件”**选项卡中，将**“Label”**控件拖动到操作窗格控件中。  
  
3.  将 Label 控件的 **Text** 属性更改为**“Name”**。  
  
4.  将**“Textbox”**控件添加到操作窗格控件中，然后更改以下属性。  
  
    |属性|值|  
    |--------|-------|  
    |**名称**|**getName**|  
    |**大小**|**130, 20**|  
  
5.  将第二个**“Label”**控件添加到操作窗格控件中，然后将**“Text”**属性更改为**“Address”**。  
  
6.  将第二个**“Textbox”**控件添加到操作窗格控件中，然后更改以下属性。  
  
    |属性|值|  
    |--------|-------|  
    |**名称**|**getAddress**|  
    |**Accepts Return**|**True**|  
    |**Multiline**|**True**|  
    |**大小**|**130, 40**|  
  
7.  将**“Button”**控件添加到操作窗格控件中，然后更改以下属性。  
  
    |属性|值|  
    |--------|-------|  
    |**名称**|**addText**|  
    |**文本**|**Insert**|  
  
## 添加用于将文本插入文档的代码  
 在操作窗格中，编写用于将文本框中的文本插入文档中相应 <xref:Microsoft.Office.Tools.Word.Bookmark> 控件的代码。  可以使用 `Globals` 类通过操作窗格上的控件来访问文档上的控件。  有关更多信息，请参见[对 Office 项目中对象的全局访问](../vsto/global-access-to-objects-in-office-projects.md)。  
  
#### 将操作窗格中的文本插入文档中的书签  
  
1.  将以下代码添加到**“addText”**按钮的 <xref:System.Windows.Forms.Control.Click> 事件处理程序。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#8](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/InsertTextControl.cs#8)]
     [!code-vb[Trin_VstcoreActionsPaneWord#8](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/InsertTextControl.vb#8)]  
  
2.  在 C\# 中，必须为按钮单击添加一个事件处理程序。  可以将此代码放在 `InsertTextControl` 构造函数中 `IntializeComponent` 调用的后面。  有关创建事件处理程序的信息，请参见[如何：在 Office 项目中创建事件处理程序](../vsto/how-to-create-event-handlers-in-office-projects.md)。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#9](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/InsertTextControl.cs#9)]  
  
## 添加用于显示操作窗格的代码  
 若要显示操作窗格，请将您创建的控件添加到控件集合中。  
  
#### 显示操作窗格  
  
1.  在 `ThisDocument` 类中创建一个新的操作窗格控件实例。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#10](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ThisDocument.cs#10)]
     [!code-vb[Trin_VstcoreActionsPaneWord#10](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ThisDocument.vb#10)]  
  
2.  将以下代码添加到 `ThisDocument` 的 <xref:Microsoft.Office.Tools.Word.Document.Startup> 事件处理程序中。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#11](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ThisDocument.cs#11)]
     [!code-vb[Trin_VstcoreActionsPaneWord#11](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ThisDocument.vb#11)]  
  
## 测试应用程序  
 对文档进行测试，以验证在打开文档时操作窗格也同时打开，并确保单击相应按钮时将已键入文本框中的文本插入到书签中。  
  
#### 测试文档  
  
1.  按 F5 运行项目。  
  
2.  确认操作窗格可见。  
  
3.  在操作窗格的文本框中键入姓名和地址，然后单击**“插入”**。  
  
## 后续步骤  
 下一步可能要执行以下几项任务：  
  
-   在 Excel 中创建操作窗格。  有关更多信息，请参见[How to: Add an Actions Pane to Excel Workbooks](http://msdn.microsoft.com/zh-cn/62abfce6-e44f-419d-85d8-26bf59f33872)。  
  
-   将数据绑定到操作窗格上的控件。  有关更多信息，请参见[演练：将数据绑定到“Word 操作”窗格上的控件](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md)。  
  
## 请参阅  
 [操作窗格概述](../vsto/actions-pane-overview.md)   
 [如何：向 Word 文档或 Excel 工作簿添加操作窗格](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [How to: Add an Actions Pane to Excel Workbooks](http://msdn.microsoft.com/zh-cn/62abfce6-e44f-419d-85d8-26bf59f33872)   
 [如何：管理操作窗格上的控件布局](../vsto/how-to-manage-control-layout-on-actions-panes.md)   
 [Bookmark 控件](../vsto/bookmark-control.md)  
  
  