---
title: "如何： 以编程方式向 Visio 文档添加形状 |Microsoft 文档"
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
- Visio [Office development in Visual Studio], adding Visio shapes
- shapes [Office development in Visual Studio], adding Visio shapes
ms.assetid: 29613237-88f5-41a7-9e13-cfa177f41221
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 39843950cb592aa40b11e098f62018a4dc6e2983
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-programmatically-add-shapes-to-a-visio-document"></a>如何：以编程方式向 Visio 文档中添加形状
  可以通过从模具中检索主控形状并将形状放置在活动页面上，向 Microsoft Office Visio 文档添加形状。  
  
 有关详细信息，请参阅 [Microsoft.Office.Interop.Visio.Documents.Add](http://msdn.microsoft.com/library/office/ff766868.aspx) 方法、 [Microsoft.Office.Interop.Visio.Application.ActivePage](http://msdn.microsoft.com/library/office/ff765484.aspx) 属性和 [Microsoft.Office.Interop.Visio.Page.Drop](http://msdn.microsoft.com/library/office/ff765054.aspx) 方法的 VBA 参考文档。  
  
## <a name="adding-shapes-to-a-visio-document"></a>向 Visio 文档添加形状  
  
#### <a name="to-add-shapes-to-a-visio-document"></a>若要向 Visio 文档添加形状  
  
-   在文档处于活动状态的情况下，从 Documents.Masters 集合中检索主控形状并将形状放置在活动文档上。 可以使用索引或主控形状名称来检索主控形状。  
  
     下面的代码示例创建一个空白 Visio 文档，然后在“基本形状”  模具停靠的情况下打开它。 该代码随后检索多个形状并将它们放置在活动页面上。  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#13](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#13)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#13](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#13)]  
  
## <a name="see-also"></a>另请参阅  
 [Visio 解决方案](../vsto/visio-solutions.md)   
 [Visio 对象模型概述](../vsto/visio-object-model-overview.md)   
 [使用 Visio 形状](../vsto/working-with-visio-shapes.md)   
 [如何：以编程方式在 Visio 文档中复制和粘贴形状](../vsto/how-to-programmatically-copy-and-paste-shapes-in-a-visio-document.md)  
  
  