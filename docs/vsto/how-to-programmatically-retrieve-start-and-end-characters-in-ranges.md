---
title: "如何： 以编程方式检索开始和结束范围中的字符 |Microsoft 文档"
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
- ranges, retrieving start and end characters
- end characters
- start characters
- documents [Office development in Visual Studio], retrieving ranges
ms.assetid: 734c630c-abc9-491d-94b6-429d1fc7a4cc
caps.latest.revision: "37"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e0cec972c731c823bb8c41f133ac721233a1b028
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-programmatically-retrieve-start-and-end-characters-in-ranges"></a>如何：以编程方式检索范围中的开始字符和结束字符
  此示例演示如何检索范围开始和结束位置的字符位置。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### <a name="to-retrieve-start-and-end-characters-of-a-range-in-a-document-level-customization"></a>检索文档级自定义项中范围的开始和结束字符  
  
1.  获取 <xref:Microsoft.Office.Interop.Word.Range.Start%2A> 的值和 <xref:Microsoft.Office.Interop.Word.Range.End%2A> 对象的 <xref:Microsoft.Office.Interop.Word.Range> 属性。 下面的代码示例获取了文档中第二个语句的开始和结束位置。 若要使用此代码示例，请从项目中的 `ThisDocument` 类运行它。  
  
     [!code-vb[Trin_VstcoreWordAutomation#25](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#25)]
     [!code-csharp[Trin_VstcoreWordAutomation#25](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#25)]  
  
### <a name="to-retrieve-start-and-end-characters-of-a-range-by-using-an-vsto-add-in"></a>使用 VSTO 外接程序检索范围的开始和结束字符  
  
1.  获取 <xref:Microsoft.Office.Interop.Word.Range.Start%2A> 的值和 <xref:Microsoft.Office.Interop.Word.Range.End%2A> 对象的 <xref:Microsoft.Office.Interop.Word.Range> 属性。 下面的代码示例获取了活动文档中第二个语句的开始和结束位置。 若要使用此代码示例，请从项目中的 `ThisAddIn` 类运行它。  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#25](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#25)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#25](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#25)]  
  
## <a name="see-also"></a>另请参阅  
 [如何： 以编程方式定义和在文档中选择范围](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [如何： 以编程方式扩展文档中的范围](../vsto/how-to-programmatically-extend-ranges-in-documents.md)   
 [如何： 以编程方式在 Word 中的重置范围文档](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)   
 [如何： 以编程方式折叠范围或在文档中的选定内容](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)   
 [如何： 以编程方式在创建范围时排除段落标记](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)   
 [如何：以编程方式统计文档中的字符数](../vsto/how-to-programmatically-count-characters-in-documents.md)  
  
  