---
title: "如何： 以编程方式定义和选择文档中的范围 |Microsoft 文档"
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
- documents [Office development in Visual Studio], selecting sentences
- documents [Office development in Visual Studio], ranges
- sentences, selecting in documents
- ranges, selecting in documents
- ranges, defining in documents
ms.assetid: 0727c1cb-d44c-4f1c-a699-4365dd13be5d
caps.latest.revision: "46"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 2fcc1b96607c36fdfbc2f9940a7b7984b3b299fa
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-programmatically-define-and-select-ranges-in-documents"></a>如何：以编程方式在文档中定义和选择范围
  你也可以通过使用 <xref:Microsoft.Office.Interop.Word.Range> 对象在 Microsoft Office Word 文档中定义一个范围。 你可以通过使用例如，选择整个文档多种方式，<xref:Microsoft.Office.Interop.Word.Range.Select%2A>方法<xref:Microsoft.Office.Interop.Word.Range>对象，或通过使用的内容属性<xref:Microsoft.Office.Tools.Word.Document>类 （在文档级自定义项） 或<xref:Microsoft.Office.Interop.Word.Document>类 (在VSTO 外接程序）。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="defining-a-range"></a>定义范围  
 下面的示例演示如何创建一个新的 <xref:Microsoft.Office.Interop.Word.Range> 对象，该对象包括活动文档中的前七个字符，其中包括非打印字符。 然后，它选择范围内的文本。  
  
#### <a name="to-define-a-range-in-a-document-level-customization"></a>在文档级自定义项中定义范围  
  
1.  通过将开始和结束字符传递到 <xref:Microsoft.Office.Tools.Word.Document> 类的 <xref:Microsoft.Office.Tools.Word.Document.Range%2A> 方法来将范围添加到文档中。 若要使用此代码示例，请从项目中的 `ThisDocument` 类运行它。  
  
     [!code-vb[Trin_VstcoreWordAutomation#18](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#18)]
     [!code-csharp[Trin_VstcoreWordAutomation#18](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#18)]  
  
#### <a name="to-define-a-range-by-using-a-vsto-add-in"></a>通过使用 VSTO 外接程序定义范围  
  
1.  通过将开始和结束字符传递到 <xref:Microsoft.Office.Interop.Word.Document> 类的 <xref:Microsoft.Office.Interop.Word._Document.Range%2A> 方法来将范围添加到文档中。 下面的代码示例将一个范围添加到活动文档。 若要使用此代码示例，请从项目中的 `ThisAddIn` 类运行它。  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#18](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#18)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#18](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#18)]  
  
## <a name="selecting-a-range-in-a-document-level-customization"></a>在文档级自定义项中选择范围  
 下面的示例演示如何通过使用 <xref:Microsoft.Office.Interop.Word.Range> 对象的 <xref:Microsoft.Office.Interop.Word.Range.Select%2A> 方法，或者通过使用 <xref:Microsoft.Office.Tools.Word.Document> 类的 <xref:Microsoft.Office.Tools.Word.Document.Content%2A> 属性来选择整个文档。  
  
#### <a name="to-select-the-entire-document-as-a-range-by-using-the-select-method"></a>通过使用 Select 方法来选择整个文档作为范围  
  
1.  使用包含整个文档的 <xref:Microsoft.Office.Interop.Word.Range> 的 <xref:Microsoft.Office.Interop.Word.Range.Select%2A> 方法。 若要使用下面的代码示例，请从项目的 `ThisDocument` 类中运行它。  
  
     [!code-vb[Trin_VstcoreWordAutomation#19](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#19)]
     [!code-csharp[Trin_VstcoreWordAutomation#19](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#19)]  
  
#### <a name="to-select-the-entire-document-as-a-range-by-using-the-content-property"></a>通过使用 Content 属性来选择整个文档作为范围  
  
1.  使用 <xref:Microsoft.Office.Tools.Word.Document.Content%2A> 属性定义包含整个文档的范围。  
  
     [!code-vb[Trin_VstcoreWordAutomation#20](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#20)]
     [!code-csharp[Trin_VstcoreWordAutomation#20](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#20)]  
  
 你还可以使用其他对象的方法和属性来定义范围。  
  
#### <a name="to-select-a-sentence-in-the-active-document"></a>在活动文档中选择一个句子  
  
1.  通过使用 <xref:Microsoft.Office.Interop.Word.Sentences> 集合设置范围。 使用你要选择的句子的索引。  
  
     [!code-vb[Trin_VstcoreWordAutomation#21](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#21)]
     [!code-csharp[Trin_VstcoreWordAutomation#21](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#21)]  
  
 选择句子的另一种方法是手动设置范围的开始和结束值。  
  
#### <a name="to-select-a-sentence-by-manually-setting-the-start-and-end-values"></a>通过手动设置开始和结束值来选择一个句子  
  
1.  创建一个范围变量。  
  
     [!code-vb[Trin_VstcoreWordAutomation#23](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#23)]
     [!code-csharp[Trin_VstcoreWordAutomation#23](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#23)]  
  
2.  检查以确定在文档中，是否有至少两个句子设置*启动*和*结束*的范围，然后选择该范围的自变量。  
  
     [!code-vb[Trin_VstcoreWordAutomation#24](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#24)]
     [!code-csharp[Trin_VstcoreWordAutomation#24](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#24)]  
  
## <a name="selecting-a-range-by-using-a-vsto-add-in"></a>通过使用 VSTO 外接程序定义范围  
 下面的示例演示如何通过使用 <xref:Microsoft.Office.Interop.Word.Range> 对象的 <xref:Microsoft.Office.Interop.Word.Range.Select%2A> 方法，或者通过使用 <xref:Microsoft.Office.Interop.Word.Document> 类的 <xref:Microsoft.Office.Interop.Word._Document.Content%2A> 属性来选择整个文档。  
  
#### <a name="to-select-the-entire-document-as-a-range-by-using-the-select-method"></a>通过使用 Select 方法来选择整个文档作为范围  
  
1.  使用包含整个文档的 <xref:Microsoft.Office.Interop.Word.Range> 的 <xref:Microsoft.Office.Interop.Word.Range.Select%2A> 方法。 下面的代码示例选择活动文档的内容。 若要使用此代码示例，请从项目中的 `ThisAddIn` 类运行它。  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#19](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#19)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#19](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#19)]  
  
#### <a name="to-select-the-entire-document-as-a-range-by-using-the-content-property"></a>通过使用 Content 属性来选择整个文档作为范围  
  
1.  使用 <xref:Microsoft.Office.Interop.Word._Document.Content%2A> 属性定义包含整个文档的范围。  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#20](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#20)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#20](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#20)]  
  
 你还可以使用其他对象的方法和属性来定义范围。  
  
#### <a name="to-select-a-sentence-in-the-active-document"></a>在活动文档中选择一个句子  
  
1.  通过使用 <xref:Microsoft.Office.Interop.Word.Sentences> 集合设置范围。 使用你要选择的句子的索引。  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#21](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#21)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#21](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#21)]  
  
 选择句子的另一种方法是手动设置范围的开始和结束值。  
  
#### <a name="to-select-a-sentence-by-manually-setting-the-start-and-end-values"></a>通过手动设置开始和结束值来选择一个句子  
  
1.  创建一个范围变量。  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#23](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#23)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#23](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#23)]  
  
2.  检查以确定在文档中，是否有至少两个句子设置*启动*和*结束*的范围，然后选择该范围的自变量。  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#24](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#24)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#24](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#24)]  
  
## <a name="see-also"></a>另请参阅  
 [Word 对象模型概述](../vsto/word-object-model-overview.md)   
 [如何： 以编程方式扩展文档中的范围](../vsto/how-to-programmatically-extend-ranges-in-documents.md)   
 [如何： 以编程方式检索开始和结束范围中的字符](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)   
 [如何： 以编程方式扩展文档中的范围](../vsto/how-to-programmatically-extend-ranges-in-documents.md)   
 [如何： 以编程方式在 Word 中的重置范围文档](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)   
 [如何： 以编程方式折叠范围或在文档中的选定内容](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)   
 [如何：以编程方式在创建范围时排除段落标记](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)  
  
  