---
title: "如何： 以编程方式打开 Visio 文档 |Microsoft 文档"
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
- documents [Office development in Visual Studio], opening Visio documents
- Visio [Office development in Visual Studio], opening Visio documents
ms.assetid: bddb820c-bde7-4d21-a0b3-6d1968baccab
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4aa949d1ff2a8d9954c29314a85363d04d09b1a8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-programmatically-open-visio-documents"></a>如何：以编程方式打开 Visio 文档
  用于打开现有的 Microsoft Office Visio 文档的两种方法： 打开和 OpenEx。 方法是打开的方法中，相同的但它提供调用方可以在其中指定文档打开方式的自变量。  
  
 有关对象模型的详细信息，请参阅 [Microsoft.Office.Interop.Visio.Documents.Open](https://msdn.microsoft.com/library/office/ff765240.aspx) 方法和 [Microsoft.Office.Interop.Visio.Documents.OpenEx](https://msdn.microsoft.com/library/office/ff767229.aspx) 方法的 VBA 参考文档。  
  
## <a name="opening-a-visio-document"></a>打开 Visio 文档  
  
#### <a name="to-open-a-visio-document"></a>若要打开 Visio 文档  
  
-   调用 Microsoft.Office.Interop.Visio.Documents.Open 方法并提供 Visio 文档的完全限定的路径。  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#5](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#5)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#5](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#5)]  
  
## <a name="opening-a-visio-document-with-specified-arguments"></a>使用指定参数打开 Visio 文档  
  
#### <a name="to-open-a-visio-document-as-read-only-and-docked"></a>如要以只读和停靠方式打开 Visio 文档  
  
-   调用 Microsoft.Office.Interop.Visio.Documents.OpenEx 方法，提供 Visio 文档的完全限定的路径，并包括想要使用的参数-在此案例中为 Docked 和只读的。  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#6](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#6)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#6](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#6)]  
  
## <a name="compiling-the-code"></a>编译代码  
 此代码示例要求满足以下条件：  
  
-   必须有一个名为 `myDrawing.vsd` 的 Visio 文档位于 My Documents 文件夹（对于 Windows XP 及更低版本）或 Documents 文件夹（对于 Windows Vista）中名为 `Test` 的目录中。  
  
## <a name="see-also"></a>另请参阅  
 [Visio 解决方案](../vsto/visio-solutions.md)   
 [Visio 对象模型概述](../vsto/visio-object-model-overview.md)   
 [如何： 以编程方式创建新的 Visio 文档](../vsto/how-to-programmatically-create-new-visio-documents.md)   
 [如何： 以编程方式关闭 Visio 文档](../vsto/how-to-programmatically-close-visio-documents.md)   
 [如何： 以编程方式保存 Visio 文档](../vsto/how-to-programmatically-save-visio-documents.md)   
 [如何：以编程方式打印 Visio 文档](../vsto/how-to-programmatically-print-visio-documents.md)  
  
  