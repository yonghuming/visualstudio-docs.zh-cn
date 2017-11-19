---
title: "如何： 以编程方式自动用递增变化的数据填充范围 |Microsoft 文档"
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
- Autofill method [Excel]
- filling ranges automatically
- ranges, automatically filling
- workbooks, filling ranges
ms.assetid: 27639d55-8ab5-483c-8907-2ea50dfd2188
caps.latest.revision: "40"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4fad536f7e9f0891f7630cd86d31cea279d5706f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-programmatically-automatically-fill-ranges-with-incrementally-changing-data"></a>如何：以编程方式自动用递增变化的数据填充范围
  <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A>方法<xref:Microsoft.Office.Interop.Excel.Range>对象可用于值自动填充工作表中的范围。 大多数情况下，<xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A>方法用于存储递增或递减的范围内的值。 你可以通过提供中的可选常数指定行为<xref:Microsoft.Office.Interop.Excel.XlAutoFillType>枚举。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 使用时，必须指定两个范围<xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A>:  
  
-   调用的范围<xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A>方法，它指定填充的起始点并包含一个初始的值。  
  
-   你希望填充，范围传递作为参数传递给<xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A>方法。 此目标范围必须包括包含的初始值的范围。  
  
    > [!NOTE]  
    >  不能将传递<xref:Microsoft.Office.Tools.Excel.NamedRange>控件来代替<xref:Microsoft.Office.Interop.Excel.Range>。 有关更多信息，请参见 [Programmatic Limitations of Host Items and Host Controls](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)。  
  
## <a name="example"></a>示例  
 [!code-csharp[Trin_VstcoreExcelAutomation#49](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#49)]
 [!code-vb[Trin_VstcoreExcelAutomation#49](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#49)]  
  
## <a name="compiling-the-code"></a>编译代码  
 你想要填充的范围的第一个单元必须包含的初始值。  
  
 该示例需要填充三个区域：  
  
-   列 B 是包含 5 个工作日。 对于初始的值中，键入**星期一**单元格 B1 中。  
  
-   列 C 是包含五个月。 对于初始的值中，键入**年 1 月**C1 单元格中。  
  
-   列 D 是包含一系列数字，每次递增两个用于每个行。 对于初始的值中，键入**4**单元格 D1 中和**6** D2 单元格中。  
  
## <a name="see-also"></a>另请参阅  
 [使用范围](../vsto/working-with-ranges.md)   
 [如何： 以编程方式引用代码中的工作表范围](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)   
 [如何： 以编程方式将样式应用于工作簿中的](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)   
 [如何： 以编程方式进行 Excel 计算](../vsto/how-to-programmatically-run-excel-calculations-programmatically.md)   
 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)   
 [Office 解决方案中的可选参数](../vsto/optional-parameters-in-office-solutions.md)  
  
  