---
title: "如何： 以编程方式创建新的 Visio 文档 |Microsoft 文档"
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
- Visio [Office development in Visual Studio], creating Visio documents
- documents [Office development in Visual Studio], creating Visio documents
ms.assetid: a0294d4c-be49-4cd0-b22e-3ec7568f3ec7
caps.latest.revision: "22"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: fa4a4d021ee0610d4fdd80a1966df6a8280c9523
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-programmatically-create-new-visio-documents"></a>如何：以编程方式创建新的 Visio 文档
  在创建新的 Microsoft Office Visio 绘图文档时，你可以将其添加到 Microsoft.Office.Interop.Visio.Documents 打开 Visio 文档的集合。 因此，Microsoft.Office.Interop.Visio.Documents.Add 方法创建一个新的 Visio 绘图文档。 有关详细信息，请参阅 [Microsoft.Office.Interop.Visio.Documents.Add](http://msdn.microsoft.com/library/office/ff766868.aspx) 方法的 VBA 参考文档。  
  
## <a name="creating-new-blank-documents"></a>创建新的空白文档  
  
#### <a name="to-create-a-new-document"></a>创建新文档  
  
-   Microsoft.Office.Interop.Visio.Documents.Add 方法用于创建不基于模板的新空白文档。  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#1](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#1)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#1](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#1)]  
  
## <a name="creating-documents-copied-from-existing-documents"></a>创建从现有文档复制而来的文档  
 Microsoft.Office.Interop.Visio.Documents.Add 方法可以创建现有的 Visio 文档的副本的新文档。 你必须提供相应关系图的文件名和完全限定路径。  
  
#### <a name="to-create-a-new-document-that-is-copied-from-an-existing-document"></a>创建从现有文档复制而来的新文档  
  
-   调用 Microsoft.Office.Interop.Visio.Documents.Add 方法并指定 Visio 关系图的路径。  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#2](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#2)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#2](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#2)]  
  
## <a name="creating-stencils-copied-from-existing-stencils"></a>创建从现有模具复制而来的模具  
 [Microsoft.Office.Interop.Visio.Documents.Add](http://msdn.microsoft.com/library/office/ff766868.aspx) 方法可创建从现有 Visio 模具复制而来的新模具。 你必须提供相应模具的文件名和完全限定路径。  
  
#### <a name="to-create-a-new-stencil-that-is-copied-from-an-existing-stencil"></a>创建从现有模具复制而来的新模具  
  
-   调用 Microsoft.Office.Interop.Visio.Documents.Add 方法并指定相应模具的路径。  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#3](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#3)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#3](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#3)]  
  
## <a name="creating-documents-based-on-existing-templates"></a>创建基于现有模板的文档  
 Microsoft.Office.Interop.Visio.Documents.Add 方法可以创建基于现有 Visio 模板 （.vst 文件） 的新文档 （.vsd 文件）。 此方法会复制作为模板工作区一部分的模具、样式和设置。 你必须提供模板的文件名称和完全限定路径。  
  
#### <a name="to-create-a-new-document-that-is-based-on-an-existing-template"></a>创建基于现有模板的新文档  
  
-   调用 Microsoft.Office.Interop.Visio.Documents.Add 方法并指定模板的路径。  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#4](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#4)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#4](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#4)]  
  
## <a name="compiling-the-code"></a>编译代码  
 此代码示例要求满足以下条件：  
  
-   必须有一个名为 `myDrawing.vsd` 的 Visio 文档位于 My Documents 文件夹（对于 Windows XP 及更低版本）或 Documents 文件夹（对于 Windows Vista）中名为 `Test` 的目录中。  
  
-   必须有一个名为 `myStencil.vss` 的 Visio 文档位于 My Documents 文件夹（对于 Windows XP 及更低版本）或 Documents 文件夹（对于 Windows Vista）中名为 `Test` 的目录中。  
  
-   必须有一个名为 `myTemplate.vst` 的 Visio 文档位于 My Documents 文件夹（对于 Windows XP 及更低版本）或 Documents 文件夹（对于 Windows Vista）中名为 `Test` 的目录中。  
  
## <a name="see-also"></a>另请参阅  
 [Visio 解决方案](../vsto/visio-solutions.md)   
 [Visio 对象模型概述](../vsto/visio-object-model-overview.md)   
 [如何： 以编程方式打开 Visio 文档](../vsto/how-to-programmatically-open-visio-documents.md)   
 [如何： 以编程方式关闭 Visio 文档](../vsto/how-to-programmatically-close-visio-documents.md)   
 [如何： 以编程方式保存 Visio 文档](../vsto/how-to-programmatically-save-visio-documents.md)   
 [如何：以编程方式打印 Visio 文档](../vsto/how-to-programmatically-print-visio-documents.md)  
  
  