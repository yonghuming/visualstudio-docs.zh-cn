---
title: "如何：以编程方式在文档中扩展范围"
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
  - "范围，扩展"
  - "文档 [Visual Studio 中的 Office 开发]，扩展范围"
ms.assetid: 055af7a4-13d5-4236-b5fb-a112721482c5
caps.latest.revision: 41
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 40
---
# 如何：以编程方式在文档中扩展范围
  定义 Microsoft Office Word 文档中的 <xref:Microsoft.Office.Interop.Word.Range> 对象后，可以通过使用 <xref:Microsoft.Office.Interop.Word.Range.MoveStart%2A> 和 <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> 方法来更改其起点和终点。<xref:Microsoft.Office.Interop.Word.Range.MoveStart%2A> 和 <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> 方法采用相同的两个参数，即 *Unit* 和 *Count*。*Count* 参数是要移动的单位数，并且 *Unit* 参数可以是以下 <xref:Microsoft.Office.Interop.Word.WdUnits> 值之一：  
  
-   <xref:Microsoft.Office.Interop.Word.WdUnits.wdCharacter>  
  
-   <xref:Microsoft.Office.Interop.Word.WdUnits.wdWord>  
  
-   <xref:Microsoft.Office.Interop.Word.WdUnits.wdSentence>  
  
-   <xref:Microsoft.Office.Interop.Word.WdUnits.wdParagraph>  
  
-   <xref:Microsoft.Office.Interop.Word.WdUnits.wdSection>  
  
-   <xref:Microsoft.Office.Interop.Word.WdUnits.wdStory>  
  
-   <xref:Microsoft.Office.Interop.Word.WdUnits.wdCell>  
  
-   <xref:Microsoft.Office.Interop.Word.WdUnits.wdColumn>  
  
-   <xref:Microsoft.Office.Interop.Word.WdUnits.wdRow>  
  
-   <xref:Microsoft.Office.Interop.Word.WdUnits.wdTable>  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 下面的示例定义了七个字符长的范围。 然后它将在原始开始位置之后移动范围的开始位置七个字符。 因为范围的结束位置也是开始位置之后的 7 个字符，则结果将是零个字符组成的范围。 然后代码在当前结束位置后移动结束位置七个字符。  
  
### 若要扩展范围  
  
1.  定义字符的范围。 有关更多信息，请参见[如何：以编程方式在文档中定义和选择范围](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)。  
  
     下面的代码示例可用于文档级自定义项。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#39](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#39)]
     [!code-vb[Trin_VstcoreWordAutomation#39](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#39)]  
  
     以下代码示例可用于 VSTO 外接程序。 本示例使用活动文档。  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#39](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#39)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#39](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#39)]  
  
2.  使用 <xref:Microsoft.Office.Interop.Word.Range> 对象的 <xref:Microsoft.Office.Interop.Word.Range.MoveStart%2A> 方法移动范围的开始位置。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#40](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#40)]
     [!code-vb[Trin_VstcoreWordAutomation#40](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#40)]  
  
3.  使用 <xref:Microsoft.Office.Interop.Word.Range> 对象的 <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> 方法移动范围的结束位置。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#41](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#41)]
     [!code-vb[Trin_VstcoreWordAutomation#41](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#41)]  
  
## 文档级自定义项代码  
  
#### 若要在文档级自定义项中扩展范围  
  
1.  下面的示例显示文档级自定项的完整代码。 若要使用此代码，请从项目中的 `ThisDocument` 类运行它。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#38](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#38)]
     [!code-vb[Trin_VstcoreWordAutomation#38](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#38)]  
  
## VSTO 外接程序代码  
  
#### 若要扩展应用程序级 VSTO 外接程序中的范围  
  
1.  下面的示例显示 VSTO 外接程序的完整代码。 若要使用此代码，请从项目中的 `ThisAddIn` 类运行它。  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#38](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#38)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#38](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#38)]  
  
## 请参阅  
 [如何：以编程方式重置 Word 文档中的范围](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)   
 [如何：以编程方式折叠文档中的范围或选定内容](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)   
 [如何：以编程方式在文档中定义和选择范围](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [如何：以编程方式检索范围中的开始字符和结束字符](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)   
 [如何：以编程方式在创建范围时排除段落标记](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)  
  
  