---
title: "如何： 以编程方式关闭文档 |Microsoft 文档"
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
- documents [Office development in Visual Studio], closing
- Word [Office development in Visual Studio], closing documents
ms.assetid: d5bee1dc-63d1-4307-828f-b7b077e20fb9
caps.latest.revision: "55"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 0cc6b310e0c376afb7e0e9a7ade5b91cb4bbb77d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-programmatically-close-documents"></a>如何：以编程方式关闭文档
  可以关闭活动文档，也可以指定关闭某个文档。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="closing-the-active-document"></a>关闭活动文档  
 关闭活动文档有两个过程：一个用于文档级自定义项；另一个用于 VSTO 外接程序。  
  
#### <a name="to-close-the-active-document-in-a-document-level-customization"></a>关闭文档级自定义项中的活动文档  
  
1.  调用项目中 <xref:Microsoft.Office.Tools.Word.Document.Close%2A> 类的 `ThisDocument` 方法，以关闭与自定义关联的文档。 若要使用以下代码示例，请从 `ThisDocument` 类中运行它。  
  
    > [!NOTE]  
    >  此示例将 <xref:Microsoft.Office.Interop.Word.WdSaveOptions.wdDoNotSaveChanges> 值传递给要关闭的 *SaveChanges* 参数，而无需保存更改或提示用户。  
  
     [!code-vb[Trin_VstcoreWordAutomation#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#3)]
     [!code-csharp[Trin_VstcoreWordAutomation#3](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#3)]  
  
#### <a name="to-close-the-active-document-in-a-vsto-add-in"></a>关闭 VSTO 外接程序中的活动文档  
  
1.  调用 <xref:Microsoft.Office.Interop.Word._Document.Close%2A> 属性的 <xref:Microsoft.Office.Interop.Word._Application.ActiveDocument%2A> 方法，以关闭活动文档。 若要使用下面的代码示例，请从项目的 `ThisAddIn` 类中运行它。  
  
    > [!NOTE]  
    >  此示例将 <xref:Microsoft.Office.Interop.Word.WdSaveOptions.wdDoNotSaveChanges> 值传递给要关闭的 *SaveChanges* 参数，而无需保存更改或提示用户。  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#3)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#3](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#3)]  
  
## <a name="closing-a-document-that-you-specify-by-name"></a>关闭按名称指定的文档  
 对于 VSTO 外接程序和文档级自定义项来说，按名称指定的文档的关闭方式是相同的。  
  
#### <a name="to-close-a-document-that-you-specify-by-name"></a>关闭按名称指定的文档  
  
1.  将文档名称指定为 <xref:Microsoft.Office.Interop.Word._Application.Documents%2A> 集合的参数，然后调用 <xref:Microsoft.Office.Interop.Word._Document.Close%2A> 方法。 以下代码示例假设在 Word 中打开了名为 **NewDocument** 的文档。  
  
    > [!NOTE]  
    >  此示例将 <xref:Microsoft.Office.Interop.Word.WdSaveOptions.wdDoNotSaveChanges> 值传递给要关闭的 *SaveChanges* 参数，而无需保存更改或提示用户。  
  
     [!code-vb[Trin_VstcoreWordAutomation#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#4)]
     [!code-csharp[Trin_VstcoreWordAutomation#4](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#4)]  
  
## <a name="see-also"></a>另请参阅  
 [如何： 以编程方式打开现有文档](../vsto/how-to-programmatically-open-existing-documents.md)   
 [如何： 以编程方式保存文档](../vsto/how-to-programmatically-save-documents.md)   
 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)   
 [Programmatic Limitations of Host Items and Host Controls](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Office 解决方案中的可选参数](../vsto/optional-parameters-in-office-solutions.md)  
  