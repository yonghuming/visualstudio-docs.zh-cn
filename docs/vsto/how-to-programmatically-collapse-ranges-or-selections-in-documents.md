---
title: "如何：以编程方式折叠文档中的范围或选定内容"
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
  - "选择，折叠"
  - "文档 [Visual Studio 中的 Office 开发]，折叠范围"
  - "折叠选择"
  - "范围，折叠"
  - "折叠范围"
ms.assetid: 0bd059dd-8606-42ae-a8a9-97f8f3bd5cc5
caps.latest.revision: 42
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 41
---
# 如何：以编程方式折叠文档中的范围或选定内容
  如果你在使用 <xref:Microsoft.Office.Interop.Word.Range> 或 <xref:Microsoft.Office.Interop.Word.Selection> 对象，则可能要在插入文本之前更改对插入点的选择，以避免覆盖现有文本。<xref:Microsoft.Office.Interop.Word.Range> 和 <xref:Microsoft.Office.Interop.Word.Selection> 对象都具有 Collapse 方法，该方法使用 <xref:Microsoft.Office.Interop.Word.WdCollapseDirection> 枚举值：  
  
-   <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseStart> 会将所选内容折叠到所选内容的开头。 如果未指定枚举值，则这是默认值。  
  
-   <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseEnd> 会将所选内容折叠到所选内容的结尾。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### 折叠范围并插入新文本  
  
1.  创建一个包含文档中第一个段落的 <xref:Microsoft.Office.Interop.Word.Range> 对象。  
  
     下面的代码示例可用于文档级自定义项。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#46](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#46)]
     [!code-vb[Trin_VstcoreWordAutomation#46](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#46)]  
  
     以下代码示例可用于 VSTO 外接程序。 此代码运用了活动文档。  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#46](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#46)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#46](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#46)]  
  
2.  使用 <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseStart> 枚举值折叠范围。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#47](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#47)]
     [!code-vb[Trin_VstcoreWordAutomation#47](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#47)]  
  
3.  插入新文本。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#48](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#48)]
     [!code-vb[Trin_VstcoreWordAutomation#48](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#48)]  
  
4.  选择 <xref:Microsoft.Office.Interop.Word.Range>。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#49](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#49)]
     [!code-vb[Trin_VstcoreWordAutomation#49](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#49)]  
  
 如果使用 <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseEnd> 枚举值，则文本会在后续段落开头处插入。  
  
 [!code-csharp[Trin_VstcoreWordAutomation#50](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#50)]
 [!code-vb[Trin_VstcoreWordAutomation#50](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#50)]  
  
 你可能预计插入新句子是在段落标记之前插入它，但情况并非如此，因为原始范围包含段落标记。 有关详细信息，请参阅[如何：以编程方式在创建范围时排除段落标记](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)。  
  
## 文档级自定义项示例  
  
#### 在文档级自定义项中折叠范围  
  
1.  下面的示例显示针对文档级自定项的完整方法。 若要使用此代码，请从项目中的 `ThisDocument` 类运行它。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#45](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#45)]
     [!code-vb[Trin_VstcoreWordAutomation#45](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#45)]  
  
## VSTO 外接程序示例  
  
#### 在 VSTO 外接程序中折叠范围  
  
1.  下面的示例显示针对 VSTO 外接程序的完整方法。 若要使用此代码，请从项目中的 `ThisAddIn` 类运行它。  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#45](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#45)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#45](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#45)]  
  
## 请参阅  
 [如何：以编程方式在 Word 文档中插入文本](../vsto/how-to-programmatically-insert-text-into-word-documents.md)   
 [如何：以编程方式在文档中定义和选择范围](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [如何：以编程方式检索范围中的开始字符和结束字符](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)   
 [如何：以编程方式在创建范围时排除段落标记](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)   
 [如何：以编程方式在文档中扩展范围](../vsto/how-to-programmatically-extend-ranges-in-documents.md)   
 [如何：以编程方式重置 Word 文档中的范围](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)  
  
  