---
title: "如何： 以编程方式引用代码中的工作表范围 |Microsoft 文档"
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
- ranges, referring to
- worksheets, referring to ranges
- referring to worksheet ranges
- Excel [Office development in Visual Studio], referring to worksheet ranges
ms.assetid: 113633b8-426a-4d02-b6b8-d459d1f110ea
caps.latest.revision: "46"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: fa76eff8719242d0fa3e059ad325dbdfb587f2bc
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-programmatically-refer-to-worksheet-ranges-in-code"></a>如何：以编程方式使用代码引用工作表范围
  你可以使用类似的过程来引用内容的<xref:Microsoft.Office.Tools.Excel.NamedRange>控件或本机 Excel 范围对象。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="using-a-namedrange-control"></a>使用 NamedRange 控件  
 下面的示例添加<xref:Microsoft.Office.Tools.Excel.NamedRange>到工作表，然后将文本添加到范围中的单元格。  
  
#### <a name="to-refer-to-a-namedrange-control"></a>来指代 NamedRange 控件  
  
1.  分配的字符串<xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A>属性<xref:Microsoft.Office.Tools.Excel.NamedRange>控件。 必须将此代码置于表类中，而不是在 `ThisWorkbook` 类中。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#46](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#46)]
     [!code-vb[Trin_VstcoreExcelAutomation#46](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#46)]  
  
## <a name="using-native-excel-ranges"></a>使用本机 Excel 范围  
 下面的示例将本机 Excel 区域添加到工作表，，然后到范围中的单元格添加文本。  
  
#### <a name="to-refer-to-a-native-range-object"></a>以引用本机范围对象  
  
1.  分配的字符串<xref:Microsoft.Office.Interop.Excel.Range.Value2%2A>的范围的属性。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#47](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#47)]
     [!code-vb[Trin_VstcoreExcelAutomation#47](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#47)]  
  
## <a name="see-also"></a>另请参阅  
 [使用范围](../vsto/working-with-ranges.md)   
 [如何： 以编程方式检查在工作表中的拼写是否正确](../vsto/how-to-programmatically-check-spelling-in-worksheets.md)   
 [如何： 以编程方式将样式应用于工作簿中的](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)   
 [如何： 以编程方式自动用递增变化的数据填充范围](../vsto/how-to-programmatically-automatically-fill-ranges-with-incrementally-changing-data.md)   
 [如何： 以编程方式搜索中工作表范围内的文本](../vsto/how-to-programmatically-search-for-text-in-worksheet-ranges.md)   
 [NamedRange 控件](../vsto/namedrange-control.md)   
 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)   
 [Programmatic Limitations of Host Items and Host Controls](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Office 解决方案中的可选参数](../vsto/optional-parameters-in-office-solutions.md)  
  
  