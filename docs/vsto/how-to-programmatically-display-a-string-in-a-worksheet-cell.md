---
title: "如何： 以编程方式在工作表单元格中显示字符串 |Microsoft 文档"
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
- text [Office development in Visual Studio], adding to worksheets
- worksheets, displaying text in cells
ms.assetid: b19870ad-e132-49fd-994e-0a91710fa4c9
caps.latest.revision: "45"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3e297a2f6c1752053557dd7bcea5adab1c2184aa
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-programmatically-display-a-string-in-a-worksheet-cell"></a>如何：以编程方式在工作表单元格中显示字符串
  此示例演示如何以编程方式在单元格中显示文本。 若要在单元格中显示文本，请使用<xref:Microsoft.Office.Tools.Excel.NamedRange>控件或本机 Excel 范围对象。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="using-a-namedrange-control"></a>使用 NamedRange 控件  
 此示例使用<xref:Microsoft.Office.Tools.Excel.NamedRange>控件名为`message`。 该控件必须添加到设计时的文档级自定义项。 下面的代码必须将置于表类中，不在`ThisWorkbook`类。  
  
#### <a name="to-display-text-in-a-namedrange-control"></a>NamedRange 控件中显示文本  
  
1.  设置的值<xref:Microsoft.Office.Tools.Excel.NamedRange>控制转移到**Hello World**。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#68](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#68)]
     [!code-vb[Trin_VstcoreExcelAutomation#68](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#68)]  
  
## <a name="using-a-native-excel-range"></a>使用本机 Excel 范围  
 下面的代码以编程方式创建一个新范围，然后将值分配给它。  
  
#### <a name="to-display-text-in-an-excel-range"></a>在 Excel 范围中显示文本  
  
1.  检索在单元格范围**A1**上`Sheet1`并将值设置为**Hello World**。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#69](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#69)]
     [!code-vb[Trin_VstcoreExcelAutomation#69](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#69)]  
  
## <a name="see-also"></a>另请参阅  
 [演练： 使用 Windows 窗体收集数据](../vsto/walkthrough-collecting-data-using-a-windows-form.md)   
 [Office 解决方案的疑难解答](../vsto/troubleshooting-office-solutions.md)   
 [NamedRange 控件](../vsto/namedrange-control.md)   
 [对 Office 项目中对象的全局访问](../vsto/global-access-to-objects-in-office-projects.md)   
 [Office 解决方案中的可选参数](../vsto/optional-parameters-in-office-solutions.md)  
  
  