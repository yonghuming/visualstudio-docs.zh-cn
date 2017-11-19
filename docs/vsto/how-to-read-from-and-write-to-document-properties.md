---
title: "如何： 读取和写入向文档属性 |Microsoft 文档"
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
- Word [Office development in Visual Studio], document properties
- documents [Office development in Visual Studio], properties
- document properties [Office development in Visual Studio]
- Excel [Office development in Visual Studio], document properties
ms.assetid: e9ef9fa3-36b9-48fb-8148-f5152463c03c
caps.latest.revision: "54"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ca687f9482d65621ad848c2ca6459c6fe782f8ba
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-read-from-and-write-to-document-properties"></a>如何：从文档属性中读取或向文档属性写入
  可以存储文档以及文档属性。 Office 应用程序提供了许多内置的属性，例如作者、标题和主题。 本主题演示如何在 Microsoft Office Excel 和 Microsoft Office Word 中设置文档属性。  
  
 ![视频链接](../vsto/media/playvideo.gif "视频链接")相关的视频演示，请参阅[如何执行 i： 访问和 Microsoft Word 中操作自定义文档属性？](http://go.microsoft.com/fwlink/?LinkId=136772)。  
  
 [!INCLUDE[appliesto_docprops](../vsto/includes/appliesto-docprops-md.md)]  
  
## <a name="setting-document-properties-in-excel"></a>在 Excel 中设置文档属性  
 要使用 Excel 中的内置属性，请使用以下属性：  
  
-   在文档级项目中，使用 <xref:Microsoft.Office.Tools.Excel.Workbook.BuiltinDocumentProperties%2A> 类的 `ThisWorkbook` 属性。  
  
-   在 VSTO 外接程序项目中，使用 <xref:Microsoft.Office.Interop.Excel._Workbook.BuiltinDocumentProperties%2A> 对象的 <xref:Microsoft.Office.Interop.Excel.Workbook> 属性。  
  
 这些属性将返回 <xref:Microsoft.Office.Core.DocumentProperties> 对象，该对象为 <xref:Microsoft.Office.Core.DocumentProperty> 对象的集合。 可以使用集合的 `Item` 属性，按名称或索引检索该集合中的特定属性。  
  
 下面的代码示例演示了如何更改文档级项目中的内置 **Revision Number** 属性。  
  
#### <a name="to-change-the-revision-number-property-in-excel"></a>若要更改在 Excel 中的修订号属性  
  
1.  将内置文档属性分配给变量。  
  
     [!code-vb[Trin_VstcoreProgramming#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/ThisWorkbook.vb#7)]
     [!code-csharp[Trin_VstcoreProgramming#7](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/ThisWorkbook.cs#7)]  
  
2.  以 1 递增 `Revision Number` 属性。  
  
     [!code-vb[Trin_VstcoreProgramming#8](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/ThisWorkbook.vb#8)]
     [!code-csharp[Trin_VstcoreProgramming#8](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/ThisWorkbook.cs#8)]  
  
## <a name="setting-document-properties-in-word"></a>在 Word 中设置文档属性  
 若要使用 Word 中的内置属性，请使用以下属性：  
  
-   在文档级项目中，使用 <xref:Microsoft.Office.Tools.Word.Document.BuiltInDocumentProperties%2A> 类的 `ThisDocument` 属性。  
  
-   在 VSTO 外接程序项目中，使用 <xref:Microsoft.Office.Interop.Word._Document.BuiltInDocumentProperties%2A> 对象的 <xref:Microsoft.Office.Interop.Word.Document> 属性。  
  
 这些属性将返回 <xref:Microsoft.Office.Core.DocumentProperties> 对象，该对象为 <xref:Microsoft.Office.Core.DocumentProperty> 对象的集合。 可以使用集合的 `Item` 属性，按名称或索引检索该集合中的特定属性。  
  
 下面的代码示例演示了如何更改文档级项目中的内置 **Subject** 属性。  
  
#### <a name="to-change-the-subject-property"></a>若要更改主题属性  
  
1.  将内置文档属性分配给变量。  
  
     [!code-csharp[Trin_VstcoreProgrammingWord#1](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingWordCS/ThisDocument.cs#1)]
     [!code-vb[Trin_VstcoreProgrammingWord#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingWordVB/ThisDocument.vb#1)]  
  
2.  将 `Subject` 属性更改为“白皮书”。  
  
     [!code-csharp[Trin_VstcoreProgrammingWord#2](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingWordCS/ThisDocument.cs#2)]
     [!code-vb[Trin_VstcoreProgrammingWord#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingWordVB/ThisDocument.vb#2)]  
  
## <a name="robust-programming"></a>可靠编程  
 这些示例假定已在 Excel 文档级项目的 `ThisWorkbook` 类中和 Word 文档级项目中的 `ThisDocument` 类中编写代码。  
  
 虽然你可以使用 Word 和 Excel 及其对象，但 Microsoft Office 仍然提供了可用的内置文档属性的列表。 尝试访问未定义的属性会引发异常。  
  
## <a name="see-also"></a>另请参阅  
 [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md)   
 [文档级自定义项编程](../vsto/programming-document-level-customizations.md)   
 [如何：创建和修改自定义文档属性](../vsto/how-to-create-and-modify-custom-document-properties.md)  
  
  