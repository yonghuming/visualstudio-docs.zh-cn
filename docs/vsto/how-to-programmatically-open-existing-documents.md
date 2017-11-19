---
title: "如何： 以编程方式打开现有文档 |Microsoft 文档"
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
- documents [Office development in Visual Studio], opening
- Word [Office development in Visual Studio], opening documents
ms.assetid: 08f7fe4b-d96d-4a0c-b32a-aa7fd7992316
caps.latest.revision: "44"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 528245e33f3157bf42f70b3918ee9f8fc9539f9a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-programmatically-open-existing-documents"></a>如何：以编程方式打开现有文档
  <xref:Microsoft.Office.Interop.Word.Documents.Open%2A>方法打开指定的完全限定的路径和文件名称的现有 Microsoft Office Word 文档。 此方法返回<xref:Microsoft.Office.Interop.Word.Document>表示打开的文档。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### <a name="to-open-a-document"></a>若要打开的文档  
  
-   调用<xref:Microsoft.Office.Interop.Word.Documents.Open%2A>方法<xref:Microsoft.Office.Interop.Word.Documents>集合并提供到文档的路径。  
  
     [!code-vb[Trin_VstcoreWordAutomation#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#5)]
     [!code-csharp[Trin_VstcoreWordAutomation#5](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#5)]  
  
### <a name="to-open-a-document-as-read-only"></a>若要打开的文档以只读方式  
  
-   调用<xref:Microsoft.Office.Interop.Word.Documents.Open%2A>方法，提供到该文档中的路径，并设置*ReadOnly*参数**True**方法调用中。  
  
     [!code-vb[Trin_VstcoreWordAutomation#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#6)]
     [!code-csharp[Trin_VstcoreWordAutomation#6](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#6)]  
  
## <a name="compiling-the-code"></a>编译代码  
 此代码示例要求满足以下条件：  
  
-   名为 NewDocument.doc 的文档必须存在于名为驱动器 C 上的测试的目录  
  
## <a name="see-also"></a>另请参阅  
 [如何： 以编程方式创建新的文档](../vsto/how-to-programmatically-create-new-documents.md)   
 [如何： 以编程方式关闭文档](../vsto/how-to-programmatically-close-documents.md)   
 [Office 解决方案中的可选参数](../vsto/optional-parameters-in-office-solutions.md)  
  
  