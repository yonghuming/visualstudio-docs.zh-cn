---
title: "如何：向 Word 文档添加书签控件 | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VST.Bookmark.Dialog"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Bookmark 控件，添加到文档"
  - "“创建 Bookmark 控件”对话框"
  - "控件 [Visual Studio 中的 Office 开发]，添加到文档"
ms.assetid: 2940704e-31f5-4486-854e-76298a9e2ee4
caps.latest.revision: 52
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 51
---
# 如何：向 Word 文档添加书签控件
  在文档级项目中，你可以在设计时或在运行时向项目中的文档添加 <xref:Microsoft.Office.Tools.Word.Bookmark> 控件。 在 VSTO 外接程序项目中，可以在运行时向任何打开的文档添加 <xref:Microsoft.Office.Tools.Word.Bookmark> 控件。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 本主题介绍了以下任务：  
  
-   [在设计时添加书签控件](#designtime)  
  
-   [在运行时在文档级项目中添加书签控件](#runtimedoclevel)  
  
-   [在运行时，向 VSTO 外接程序项目中添加 Bookmark 控件](#runtimeaddin)  
  
 有关 <xref:Microsoft.Office.Tools.Word.Bookmark> 控件的详细信息，请参阅 [Bookmark 控件](../vsto/bookmark-control.md)。  
  
##  <a name="designtime"></a> 在设计时添加书签控件  
 可通过几种方式在设计时向文档级项目中的文档添加 <xref:Microsoft.Office.Tools.Word.Bookmark> 控件：  
  
-   从 Visual Studio **“工具箱”**。  
  
     你可以将 <xref:Microsoft.Office.Tools.Word.Bookmark> 控件从**“工具箱”**拖动到文档中。 如果你已在使用**“工具箱”**向文档添加 Windows 窗体控件，则你可能会想要选择这种方式。  
  
-   从 Word 内。  
  
     你可以以添加本机书签相同的方式向你的文档添加 <xref:Microsoft.Office.Tools.Word.Bookmark> 控件。 用这种方式添加的优点是你可以在创建控件时对其命名。  
  
-   从**“数据源”**窗口。  
  
     你可以从**“数据源”**窗口将 <xref:Microsoft.Office.Tools.Word.Bookmark> 控件拖动到你的文档中。 当你想要在同一时间将控件绑定到数据时，这一方式会非常有用。 可以用从**“数据源”**窗口添加 Windows 窗体控件相同的方式添加主机控件。 有关详细信息，请参阅[数据绑定和 Windows 窗体](http://msdn.microsoft.com/library/419aac5e-819b-4aad-88b0-73a2f8c0bd27)。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
#### 若要从工具箱向文档添加书签控件  
  
1.  打开**“工具箱”**并单击**“Word 控件”**选项卡。  
  
2.  将 <xref:Microsoft.Office.Tools.Word.Bookmark> 控件拖动到文档。  
  
     **“添加书签”**对话框随即出现。  
  
3.  选择文本或你想要包括在书签中的其他项。  
  
4.  单击“确定”。  
  
     如果不希望保留默认书签名称，可以在**“属性”**窗口中更改名称。  
  
#### 若要在 Word 中向文档添加书签控件  
  
1.  在托管在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 设计器的文档中，将光标置于要添加书签的地方，或选择你想要书签括起来的文本。  
  
2.  在功能区**“插入”**选项卡上的**“链接”**组中，单击**“书签”**按钮。  
  
3.  在**“书签”**对话框中，键入新书签的名称，然后单击**“添加”**。  
  
##  <a name="runtimedoclevel"></a> 在运行时在文档级项目中添加书签控件  
 你可以通过使用项目中 `ThisDocument` 类的 <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> 属性的方法在运行时以编程方式向文档添加 <xref:Microsoft.Office.Tools.Word.Bookmark> 控件。 有两种方法重载可用于按以下方式添加 <xref:Microsoft.Office.Tools.Word.Bookmark> 控件：  
  
-   在指定范围内添加 <xref:Microsoft.Office.Tools.Word.Bookmark>。  
  
-   添加基于文档中的本机书签的 <xref:Microsoft.Office.Tools.Word.Bookmark>（即，<xref:Microsoft.Office.Interop.Word.Bookmark>）。  
  
 文档关闭时，动态创建的 <xref:Microsoft.Office.Tools.Word.Bookmark> 控件将不保留在文档中。 但是，本机 <xref:Microsoft.Office.Interop.Word.Bookmark> 保留在文档中。 在下次打开该文档时，你可以重新创建基于本机书签的 <xref:Microsoft.Office.Tools.Word.Bookmark>。 有关详细信息，请参阅[在运行时向 Office 文档添加控件](../vsto/adding-controls-to-office-documents-at-run-time.md)。  
  
#### 以编程方式向文档添加书签控件  
  
1.  在项目中的 `ThisDocument_Startup` 事件处理程序中，插入以下代码以将 <xref:Microsoft.Office.Tools.Word.Bookmark> 控件添加到文档中的第一个段落。  
  
     [!code-csharp[Trin_VstcoreHostControlsWord#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsWord/CS/ThisDocument.cs#1)]
     [!code-vb[Trin_VstcoreHostControlsWord#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsWord/VB/ThisDocument.vb#1)]  
  
    > [!NOTE]  
    >  如果你想要从现有的 <xref:Microsoft.Office.Interop.Word.Bookmark> 创建 <xref:Microsoft.Office.Tools.Word.Bookmark> 控件，请使用 <xref:Microsoft.Office.Tools.Word.ControlCollection.AddBookmark%2A> 方法并传入现有的 <xref:Microsoft.Office.Interop.Word.Bookmark>。  
  
##  <a name="runtimeaddin"></a> 在运行时，向 VSTO 外接程序项目中添加 Bookmark 控件  
 你可以通过使用 VSTO 外接程序在运行时以编程方式将 <xref:Microsoft.Office.Tools.Word.Bookmark> 控件添加到任何打开的文档。 若要执行此操作，生成基于打开的文档的 <xref:Microsoft.Office.Tools.Word.Document> 主机项，然后使用此主机项的 <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> 属性的方法。 有两种方法重载可用于按以下方式添加 <xref:Microsoft.Office.Tools.Word.Bookmark> 控件：  
  
-   在指定范围内添加 <xref:Microsoft.Office.Tools.Word.Bookmark>。  
  
-   添加基于文档中的本机书签的 <xref:Microsoft.Office.Tools.Word.Bookmark>（即，<xref:Microsoft.Office.Interop.Word.Bookmark>）。  
  
 文档关闭时，动态创建的 <xref:Microsoft.Office.Tools.Word.Bookmark> 控件将不保留在文档中。 但是，本机 <xref:Microsoft.Office.Interop.Word.Bookmark> 保留在文档中。 在下次打开该文档时，你可以重新创建基于本机书签的 <xref:Microsoft.Office.Tools.Word.Bookmark>。 有关详细信息，请参阅[在 Office 文档中保存动态控件](../vsto/persisting-dynamic-controls-in-office-documents.md)。  
  
 有关在 VSTO 外接程序项目中生成宿主项的详细信息，请参阅 [在运行时在 VSTO 外接程序中扩展 Word 文档和 Excel 工作簿](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)。  
  
#### 若要在指定范围内添加书签控件  
  
1.  使用 <xref:Microsoft.Office.Tools.Word.ControlCollection.AddBookmark%2A> 方法，并在你想要添加 <xref:Microsoft.Office.Tools.Word.Bookmark> 的地方传入 <xref:Microsoft.Office.Interop.Word.Range>。  
  
     下面的代码示例将一个新 <xref:Microsoft.Office.Tools.Word.Bookmark> 添加到活动文档的开头。 若要使用此示例，在 Word VSTO 外接程序项目中运行来自 `ThisAddIn_Startup` 事件处理程序的代码。  
  
     [!code-csharp[Trin_WordAddInDynamicControls#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/CS/ThisAddIn.cs#4)]
     [!code-vb[Trin_WordAddInDynamicControls#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/VB/ThisAddIn.vb#4)]  
  
#### 若要添加基于本机书签控件的书签控件  
  
1.  使用 <xref:Microsoft.Office.Tools.Word.ControlCollection.AddBookmark%2A> 方法，并传入你想要用作新 <xref:Microsoft.Office.Tools.Word.Bookmark> 的基础的现有的 <xref:Microsoft.Office.Interop.Word.Bookmark>。  
  
     下面的代码示例创建一个新 <xref:Microsoft.Office.Tools.Word.Bookmark>，它基于活动文档中的第一个 <xref:Microsoft.Office.Interop.Word.Bookmark>。 若要使用此示例，在 Word VSTO 外接程序项目中运行来自 `ThisAddIn_Startup` 事件处理程序的代码。  
  
     [!code-csharp[Trin_WordAddInDynamicControls#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/CS/ThisAddIn.cs#5)]
     [!code-vb[Trin_WordAddInDynamicControls#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/VB/ThisAddIn.vb#5)]  
  
## 请参阅  
 [使用扩展对象实现 Word 自动化](../vsto/automating-word-by-using-extended-objects.md)   
 [宿主项和宿主控件概述](../vsto/host-items-and-host-controls-overview.md)   
 [在运行时向 Office 文档添加控件](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [宿主项和宿主控件的编程限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [VSTO 外接程序编程](../vsto/programming-vsto-add-ins.md)   
 [对文档级自定义项进行编程](../vsto/programming-document-level-customizations.md)   
 [如何：调整 Bookmark 控件的大小](../vsto/how-to-resize-bookmark-controls.md)  
  
  