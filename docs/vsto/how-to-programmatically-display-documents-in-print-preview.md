---
title: "如何： 以编程方式在打印预览中显示文档 |Microsoft 文档"
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
- Word [Office development in Visual Studio], displaying documents in print preview
- documents [Office development in Visual Studio], displaying in print preview
ms.assetid: 96c7faea-9c5c-42b4-a009-08894a6d15c9
caps.latest.revision: "39"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 79facc7d8232a1dac5adc5f9e57848d4a206ba82
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-programmatically-display-documents-in-print-preview"></a>如何：以编程方式在打印预览中显示文档
  如果你的解决方案生成了报告，你可能需要以打印预览模式向用户显示报告。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="procedures-for-document-level-customizations"></a>适用于文档级自定义项的过程  
  
#### <a name="to-display-a-document-in-print-preview-by-calling-the-printpreview-method"></a>通过调用 PrintPreview 方法在打印预览中显示文档  
  
1.  调用 <xref:Microsoft.Office.Tools.Word.Document.PrintPreview%2A> 类的 <xref:Microsoft.Office.Tools.Word.Document> 方法。 若要使用此代码示例，请从项目中的 `ThisDocument` 类运行它。  
  
     [!code-vb[Trin_VstcoreWordAutomation#13](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#13)]
     [!code-csharp[Trin_VstcoreWordAutomation#13](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#13)]  
  
#### <a name="to-display-a-document-in-print-preview-by-setting-the-printpreview-property"></a>通过设置 PrintPreview 属性在打印预览中显示文档  
  
1.  将 <xref:Microsoft.Office.Interop.Word._Application.PrintPreview%2A> 对象的 <xref:Microsoft.Office.Interop.Word.Application> 属性设置为 **true**。  
  
     [!code-vb[Trin_VstcoreWordAutomation#14](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#14)]
     [!code-csharp[Trin_VstcoreWordAutomation#14](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#14)]  
  
## <a name="procedures-for-vsto-add-ins"></a>适用于 VSTO 外接程序的过程  
  
#### <a name="to-display-a-document-in-print-preview-by-calling-the-printpreview-method"></a>通过调用 PrintPreview 方法在打印预览中显示文档  
  
1.  调用要预览的 <xref:Microsoft.Office.Interop.Word._Document.PrintPreview%2A> 的 <xref:Microsoft.Office.Interop.Word.Document> 方法。 若要使用此代码示例，请从项目中的 `ThisAddIn` 类运行它。  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#13](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#13)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#13](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#13)]  
  
#### <a name="to-display-a-document-in-print-preview-by-setting-the-printpreview-property"></a>通过设置 PrintPreview 属性在打印预览中显示文档  
  
1.  将 <xref:Microsoft.Office.Interop.Word._Application.PrintPreview%2A> 对象的 <xref:Microsoft.Office.Interop.Word.Application> 属性设置为 **true**。  
  
     [!code-vb[Trin_VstcoreWordAutomation#14](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#14)]
     [!code-csharp[Trin_VstcoreWordAutomation#14](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#14)]  
  
## <a name="see-also"></a>另请参阅  
 [如何： 以编程方式打印文档](../vsto/how-to-programmatically-print-documents.md)   
 [如何： 以编程方式打开现有文档](../vsto/how-to-programmatically-open-existing-documents.md)   
 [如何：以编程方式新建文档](../vsto/how-to-programmatically-create-new-documents.md)  
  
  