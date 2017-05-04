---
title: "如何：以编程方式向文档中添加图片和艺术字 | Microsoft Docs"
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
  - "文档 [Visual Studio 中的 Office 开发], 添加图片"
  - "图形, 添加到 Word 文档"
  - "Word 文档, 添加图片"
  - "Word 文档, 添加 Word 艺术字"
  - "WordArt, 添加到文档"
ms.assetid: 944e1858-bc7c-471f-b5e7-adf3b0fa574d
caps.latest.revision: 24
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 23
---
# 如何：以编程方式向文档中添加图片和艺术字
  可以在设计时或运行时向文档中添加图片和图形对象。  可使用“艺术字”向 Microsoft Office Word 文档添加装饰性文本。  这些特殊文本效果是一些图形对象，你可以自定义这些图形对象并插入到文档中。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## 在设计时添加图片  
 如果正在开发文档级自定义项，则可以在设计时向文档中添加图片。  
  
#### 在设计时向 Word 文档添加图片  
  
1.  将光标置于文档中要插入图片的位置。  
  
2.  单击功能区的**“插入”**选项卡。  
  
3.  在**“插图”**组中，单击**“图片”**。  
  
4.  在**“插入图片”**对话框中，导航到要插入的图片，然后单击**“插入”**。  
  
     图片将被添加到文档中光标当前所在的位置。  
  
## 在运行时添加图片  
 可以将图片插入文档中光标当前所在的位置。  
  
#### 在光标位置添加图片  
  
1.  调用 <xref:Microsoft.Office.Interop.Word.InlineShapes> 集合的 <xref:Microsoft.Office.Interop.Word.InlineShapes.AddPicture%2A> 方法，并传入文件名。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#108](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#108)]
     [!code-vb[Trin_VstcoreWordAutomation#108](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#108)]  
  
## 在设计时添加艺术字  
 如果正在开发文档级自定义项，则可以在设计时向文档中添加艺术字。  
  
#### 在设计时向 Word 文档添加艺术字  
  
1.  将光标置于文档中要插入艺术字的位置。  
  
2.  单击功能区的**“插入”**选项卡。  
  
3.  在**“文本”**组中，单击**“艺术字”**，然后选择艺术字式样。  
  
4.  在**“编辑艺术字文本”**对话框中添加要在文档中显示的文本，然后单击**“确定”**。  
  
     这样文本就会添加到文档中，并应用选定的艺术字样式。  
  
## 在运行时添加艺术字  
 可以将艺术字插入文档中光标当前所在的位置。  对于文档级自定义项和 VSTO 外接程序，此过程有所不同。  
  
#### 在文档级自定义项中的光标位置处添加艺术字  
  
1.  获取当前光标位置的左上角位置。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#109](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#109)]
     [!code-vb[Trin_VstcoreWordAutomation#109](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#109)]  
  
2.  在文档中调用 <xref:Microsoft.Office.Interop.Word.Shapes> 对象的 <xref:Microsoft.Office.Interop.Word.Shapes.AddTextEffect%2A> 方法。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#110](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#110)]
     [!code-vb[Trin_VstcoreWordAutomation#110](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#110)]  
  
#### 在 VSTO 外接程序中的光标位置处添加艺术字  
  
1.  获取当前光标位置的左上角位置。  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#109](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#109)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#109](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#109)]  
  
2.  调用活动文档（或指定的其他文档）的 <xref:Microsoft.Office.Interop.Word.Shapes> 对象的 <xref:Microsoft.Office.Interop.Word.Shapes.AddTextEffect%2A> 方法。  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#110](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#110)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#110](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#110)]  
  
## 编译代码  
  
-   在驱动器 C 上必须存在一个名为 **SamplePicture.jpg** 的图片。  
  
## 请参阅  
 [如何：以编程方式打开现有文档](../vsto/how-to-programmatically-open-existing-documents.md)   
 [如何：以编程方式在 Word 文档中插入文本](../vsto/how-to-programmatically-insert-text-into-word-documents.md)   
 [如何：以编程方式在搜索后还原选定内容](../vsto/how-to-programmatically-restore-selections-after-searches.md)   
 [如何：以编程方式保存文档](../vsto/how-to-programmatically-save-documents.md)   
 [Office 解决方案中的可选参数](../vsto/optional-parameters-in-office-solutions.md)  
  
  