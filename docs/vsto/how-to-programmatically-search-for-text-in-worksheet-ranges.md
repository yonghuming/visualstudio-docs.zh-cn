---
title: "如何： 以编程方式搜索中工作表范围内的文本 |Microsoft 文档"
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
- worksheets, searching
- text [Office development in Visual Studio], searching in worksheets
- text searches, worksheets
ms.assetid: a6902711-fefb-450a-a76b-b1446d11c423
caps.latest.revision: "48"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 031894a3307a40af981ad974898ae819ba68d24a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-programmatically-search-for-text-in-worksheet-ranges"></a>如何：以编程方式在工作表范围内搜索文本
  <xref:Microsoft.Office.Interop.Excel.Range.Find%2A>方法<xref:Microsoft.Office.Interop.Excel.Range>对象可用于搜索的范围内的文本。 此文本也可以是任何错误字符串，如出现在工作表单元格`#NULL!`或`#VALUE!`。 有关错误字符串的详细信息，请参阅[单元格错误值](http://msdn.microsoft.com/library/office/ff839168.aspx)。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 下面的示例搜索名为一系列`Fruits`和修改包含"对象"一词的单元格的字体。 此过程还使用<xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A>方法，它使用以前设置搜索设置重复搜索。 指定搜索，请在其后的单元格和<xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A>方法可处理的其余部分。  
  
> [!NOTE]  
>  <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A>方法的搜索将重新回到搜索范围的开始处后它已达到范围的末尾。 你的代码必须确保搜索不环绕在周围的无限循环。 示例过程演示一种方法来处理这使用<xref:Microsoft.Office.Interop.Excel.Range.Address%2A>属性。  
  
 ![视频链接](../vsto/media/playvideo.gif "视频链接")相关的视频演示，请参阅[如何： 使用 Find 方法在 Excel 外接程序中？](http://go.microsoft.com/fwlink/?LinkID=130294)。  
  
### <a name="to-search-for-text-in-a-worksheet-range"></a>若要在工作表范围中搜索文本  
  
1.  声明为跟踪的整个范围，找到的第一个范围和找到的当前范围的变量。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#58](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#58)]
     [!code-vb[Trin_VstcoreExcelAutomation#58](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#58)]  
  
2.  搜索第一个匹配项，指定要搜索后的单元格以外的所有参数。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#59](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#59)]
     [!code-vb[Trin_VstcoreExcelAutomation#59](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#59)]  
  
3.  继续搜索，只要有匹配项。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#60](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#60)]
     [!code-vb[Trin_VstcoreExcelAutomation#60](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#60)]  
  
4.  比较找到的第一个范围 (`firstFind`) 到**执行任何操作**。 如果`firstFind`不包含找到的范围的任何值，则代码将存储消失 (`currentFind`)。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#61](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#61)]
     [!code-vb[Trin_VstcoreExcelAutomation#61](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#61)]  
  
5.  如果找到范围的地址匹配的第一个找到的范围的地址，请退出循环。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#62](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#62)]
     [!code-vb[Trin_VstcoreExcelAutomation#62](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#62)]  
  
6.  设置找到的范围的外观。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#63](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#63)]
     [!code-vb[Trin_VstcoreExcelAutomation#63](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#63)]  
  
7.  再次执行搜索。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#64](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#64)]
     [!code-vb[Trin_VstcoreExcelAutomation#64](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#64)]  
  
 以下示例显示完整的方法。  
  
## <a name="example"></a>示例  
 [!code-csharp[Trin_VstcoreExcelAutomation#57](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#57)]
 [!code-vb[Trin_VstcoreExcelAutomation#57](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#57)]  
  
## <a name="see-also"></a>另请参阅  
 [使用范围](../vsto/working-with-ranges.md)   
 [如何： 以编程方式将样式应用于工作簿中的](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)   
 [如何： 以编程方式引用代码中的工作表范围](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)   
 [Office 解决方案中的可选参数](../vsto/optional-parameters-in-office-solutions.md)  
  
  