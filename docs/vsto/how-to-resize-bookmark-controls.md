---
title: "如何：调整 Bookmark 控件的大小 | Microsoft Docs"
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
  - "控件 [Visual Studio 中的 Office 开发]，重设大小"
  - "书签控件，重设大小"
ms.assetid: 3de1c774-921a-4113-a54a-e3b8d4a65d53
caps.latest.revision: 45
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 44
---
# 如何：调整 Bookmark 控件的大小
  当你将 <xref:Microsoft.Office.Tools.Word.Bookmark> 控件添加到 Microsoft Office Word 文档时，可以设置它的大小。 稍后还可以重设其大小。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 有三种方法可以重设书签的大小：  
  
-   添加或删除 <xref:Microsoft.Office.Tools.Word.Bookmark> 控件中的文本。  
  
     每次在书签中添加文本时，该书签的大小会自动增加以包含新的文本。 删除文本时，书签的大小会自动减小。  
  
-   更改 <xref:Microsoft.Office.Tools.Word.Bookmark> 控件的 <xref:Microsoft.Office.Tools.Word.Bookmark.Start%2A> 和 <xref:Microsoft.Office.Tools.Word.Bookmark.End%2A> 属性。  
  
     如果只将大小更改几个字符，此方法很有用。  
  
-   重新创建 <xref:Microsoft.Office.Tools.Word.Bookmark> 控件。  
  
     如果将对书签的大小或位置作出重大更改，此方法很有用。  
  
 在文档级项目中，你可以在设计时或在运行时向项目中的文档添加 <xref:Microsoft.Office.Tools.Word.Bookmark> 控件。 在 VSTO 外接程序项目中，可以在运行时向任何打开的文档添加 <xref:Microsoft.Office.Tools.Word.Bookmark> 控件。 有关详细信息，请参阅[如何：向 Word 文档添加书签控件](../vsto/how-to-add-bookmark-controls-to-word-documents.md)。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## 更改 Start 和 End 属性  
  
#### 在设计时重设文档级项目中的书签大小  
  
1.  在“属性”窗口中选择书签。  
  
2.  增大或减小 <xref:Microsoft.Office.Tools.Word.Bookmark.Start%2A> 属性的值。  
  
3.  增大或减小 <xref:Microsoft.Office.Tools.Word.Bookmark.End%2A> 属性的值。  
  
#### 在运行时重设文档级项目中的书签大小  
  
1.  修改在运行或设计时创建的 <xref:Microsoft.Office.Tools.Word.Bookmark> 的 <xref:Microsoft.Office.Tools.Word.Bookmark.Start%2A> 和 <xref:Microsoft.Office.Tools.Word.Bookmark.End%2A> 属性。  
  
     下面的代码示例演示添加五个字符到名为 `SampleBookmark` 的书签的起始位置。 此代码假定该书签之前的文本至少有五个字符。  
  
     [!code-csharp[Trin_VstcoreHostControlsWord#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsWord/CS/ThisDocument.cs#2)]
     [!code-vb[Trin_VstcoreHostControlsWord#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsWord/VB/ThisDocument.vb#2)]  
  
     下面的代码示例演示添加五个字符到同一个书签的结束位置。 此代码假定该书签之后的文本至少有五个字符。  
  
     [!code-csharp[Trin_VstcoreHostControlsWord#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsWord/CS/ThisDocument.cs#3)]
     [!code-vb[Trin_VstcoreHostControlsWord#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsWord/VB/ThisDocument.vb#3)]  
  
#### 在运行时重设 VSTO 外接程序项目中的书签大小  
  
1.  修改在运行时创建的 <xref:Microsoft.Office.Tools.Word.Bookmark> 的 <xref:Microsoft.Office.Tools.Word.Bookmark.Start%2A> 和 <xref:Microsoft.Office.Tools.Word.Bookmark.End%2A> 属性。  
  
     下面的代码示例演示创建包含活动文档第一段中文本的 <xref:Microsoft.Office.Tools.Word.Bookmark>，然后删除 <xref:Microsoft.Office.Tools.Word.Bookmark> 开始和结束位置的 5 个字符。  
  
     [!code-csharp[Trin_WordAddInDynamicControls#16](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/CS/ThisAddIn.cs#16)]
     [!code-vb[Trin_WordAddInDynamicControls#16](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/VB/ThisAddIn.vb#16)]  
  
## 重新创建书签  
 你可以通过添加与现有书签具有相同名称但大小不同的新书签来重设书签的大小。  
  
#### 在设计时重新创建文档级项目中的书签  
  
1.  选择要包含在新 <xref:Microsoft.Office.Tools.Word.Bookmark> 控件中的文本。  
  
2.  在“插入”菜单上，单击“书签”。  
  
3.  在“书签”对话框中，选择想要重设其大小的书签的名称，并单击“添加”。  
  
## 请参阅  
 [如何：向 Word 文档添加书签控件](../vsto/how-to-add-bookmark-controls-to-word-documents.md)   
 [使用扩展对象实现 Word 自动化](../vsto/automating-word-by-using-extended-objects.md)   
 [宿主项和宿主控件概述](../vsto/host-items-and-host-controls-overview.md)   
 [如何：调整 NamedRange 控件的大小](../vsto/how-to-resize-namedrange-controls.md)   
 [如何：调整 ListObject 控件的大小](../vsto/how-to-resize-listobject-controls.md)   
 [宿主项和宿主控件的编程限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  