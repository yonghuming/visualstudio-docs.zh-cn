---
title: "如何： 以编程方式保存文档 |Microsoft 文档"
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
- documents [Office development in Visual Studio], saving
- Word [Office development in Visual Studio], saving documents
ms.assetid: a6225ae9-94f5-421a-9860-5299002d543d
caps.latest.revision: "44"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 2c6a47bae9923d68acc189c53766d5206244f97c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-programmatically-save-documents"></a>如何：以编程方式保存文档
  有多种方法来保存 Microsoft Office Word 文档。 你可以将文档保存而无需更改该文档的名称或你可以使用新名称保存文档。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="saving-a-document-without-changing-the-name"></a>保存文档，而不更改名称  
  
#### <a name="to-save-the-document-associated-with-a-document-level-customization"></a>若要保存与文档级自定义关联的文档  
  
1.  调用 <xref:Microsoft.Office.Tools.Word.Document> 类的 <xref:Microsoft.Office.Tools.Word.Document.Save%2A> 方法。 若要使用此代码示例，请从项目中的 `ThisDocument` 类运行它。  
  
     [!code-vb[Trin_VstcoreWordAutomation#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#7)]
     [!code-csharp[Trin_VstcoreWordAutomation#7](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#7)]  
  
#### <a name="to-save-the-active-document"></a>若要保存活动文档  
  
1.  调用<xref:Microsoft.Office.Interop.Word._Document.Save%2A>活动文档的方法。 若要使用此代码模板，请从项目中的 `ThisDocument` 或 `ThisAddIn` 类运行它。  
  
     [!code-vb[Trin_VstcoreWordAutomation#8](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#8)]
     [!code-csharp[Trin_VstcoreWordAutomation#8](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#8)]  
  
 如果不能确定你想要保存的文档是否是活动文档时，可以按其名称来引用它。  
  
#### <a name="to-save-a-document-specified-by-name"></a>若要保存由名称指定的文档  
  
1.  使用作为参数的文档名称<xref:Microsoft.Office.Interop.Word.Documents>集合。 若要使用此代码模板，请从项目中的 `ThisDocument` 或 `ThisAddIn` 类运行它。  
  
     [!code-vb[Trin_VstcoreWordAutomation#9](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#9)]
     [!code-csharp[Trin_VstcoreWordAutomation#9](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#9)]  
  
## <a name="saving-a-document-with-a-new-name"></a>使用新名称保存文档  
 另存为方法用于使用新名称保存文档。 你可以使用此方法的<xref:Microsoft.Office.Tools.Word.Document>宿主项在文档级 Word 项目中，或者的本机<xref:Microsoft.Office.Interop.Word.Document>任何 Word 项目中的对象。 此方法要求指定新文件名，但其他参数是可选的。  
  
> [!NOTE]  
>  如果你显示**另存为**对话框内的<xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave>事件处理程序`ThisDocument`并设置*取消*参数**false**，应用程序可能会意外退出。 如果你设置*取消*参数**true**，一条错误消息显示，指示已禁用了自动保存。  
  
#### <a name="to-save-the-document-associated-with-a-document-level-customization-with-a-new-name"></a>若要保存的文档级自定义项使用新名称与关联的文档  
  
1.  调用<xref:Microsoft.Office.Tools.Word.Document.SaveAs%2A>方法`ThisDocument`类在项目中，使用完全限定的路径和文件名。 如果该文件夹中已存在具有该名称的文件，则以无提示方式覆盖它。 若要使用此代码示例，请从 `ThisDocument` 类中运行它。  
  
    > [!NOTE]  
    >  <xref:Microsoft.Office.Tools.Word.Document.SaveAs%2A>方法引发异常，如果目标目录不存在或者没有保存文件的其他问题。 它是一个好办法使用**try … catch**解决阻止<xref:Microsoft.Office.Tools.Word.Document.SaveAs%2A>方法或在调用方法。  
  
     [!code-vb[Trin_VstcoreWordAutomation#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#10)]
     [!code-csharp[Trin_VstcoreWordAutomation#10](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#10)]  
  
#### <a name="to-save-a-native-document-with-a-new-name"></a>若要使用新名称保存本机文档  
  
1.  调用<xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A>方法<xref:Microsoft.Office.Interop.Word.Document>你想要保存，请使用完全限定的路径和文件名。 如果该文件夹中已存在具有该名称的文件，则以无提示方式覆盖它。  
  
     下面的代码示例使用新名称保存活动文档。 若要使用此代码模板，请从项目中的 `ThisDocument` 或 `ThisAddIn` 类运行它。  
  
    > [!NOTE]  
    >  <xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A>方法引发异常，如果目标目录不存在或者没有保存文件的其他问题。 它是一个好办法使用**try … catch**解决阻止<xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A>方法或在调用方法。  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#10)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#10](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#10)]  
  
## <a name="compiling-the-code"></a>编译代码  
 此代码示例要求满足以下条件：  
  
-   若要按名称保存文档，名为 NewDocument.doc 的文档必须存在于名为驱动器 C 上的测试的目录  
  
-   若要使用新名称保存文档，一个名为测试目录必须存在驱动器 C 上。  
  
## <a name="see-also"></a>另请参阅  
 [如何： 以编程方式关闭文档](../vsto/how-to-programmatically-close-documents.md)   
 [如何： 以编程方式打开现有文档](../vsto/how-to-programmatically-open-existing-documents.md)   
 [文档主机项](../vsto/document-host-item.md)   
 [Office 解决方案中的可选参数](../vsto/optional-parameters-in-office-solutions.md)  
  
  