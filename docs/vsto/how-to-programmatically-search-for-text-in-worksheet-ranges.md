---
title: "如何：以编程方式在工作表范围内搜索文本"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "文本 [Visual Studio 中的 Office 开发], 在工作表中搜索"
  - "文本搜索, 工作表"
  - "工作表, 搜索"
ms.assetid: a6902711-fefb-450a-a76b-b1446d11c423
caps.latest.revision: 48
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 47
---
# 如何：以编程方式在工作表范围内搜索文本
  通过 <xref:Microsoft.Office.Interop.Excel.Range> 对象的 <xref:Microsoft.Office.Interop.Excel.Range.Find%2A> 方法，可以在范围中搜索文本。  此文本还可以是工作表单元格中显示的任何错误字符串，例如 `#NULL!` 或 `#VALUE!`。  有关错误字符串的更多信息，请参见[单元格错误值](HV10038459)。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 下面的示例在名为 `Fruits` 的范围内进行搜索，并修改包含单词“apples”的单元格的字体。  此过程还使用 <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A> 方法，该方法使用前面设定的搜索设置重复搜索。  您需要指定要从哪个单元格后开始搜索，<xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A> 方法将处理其余操作。  
  
> [!NOTE]  
>  <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A> 方法在到达搜索范围末尾后将重新回到范围开始处进行搜索。  您的代码必须确保搜索不会进入死循环。  该示例过程演示了一种使用 <xref:Microsoft.Office.Interop.Excel.Range.Address%2A> 属性处理这种情况的方法。  
  
 ![链接到视频](~/data-tools/media/playvideo.gif "链接到视频") 有关相关视频演示，请参见 [How Do I: Use the Find Method in an Excel Add\-in?](http://go.microsoft.com/fwlink/?LinkID=130294)（如何实现：在 Excel 外接程序中使用查找方法？）。  
  
### 在工作表范围内搜索文本  
  
1.  声明若干变量，分别用于跟踪整个范围、找到的第一个范围和当前找到的范围。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#58](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#58)]
     [!code-vb[Trin_VstcoreExcelAutomation#58](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#58)]  
  
2.  搜索第一个匹配项，指定从其后开始搜索的单元格以外的所有参数。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#59](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#59)]
     [!code-vb[Trin_VstcoreExcelAutomation#59](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#59)]  
  
3.  继续搜索，直到没有匹配项。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#60](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#60)]
     [!code-vb[Trin_VstcoreExcelAutomation#60](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#60)]  
  
4.  将找到的第一个范围 \(`firstFind`\) 和 **Nothing** 进行比较。  如果 `firstFind` 不包含任何值，则代码将存储查找范围 \(`currentFind`\)。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#61](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#61)]
     [!code-vb[Trin_VstcoreExcelAutomation#61](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#61)]  
  
5.  如果查找范围的地址与第一个查找范围的地址匹配，则退出循环。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#62](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#62)]
     [!code-vb[Trin_VstcoreExcelAutomation#62](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#62)]  
  
6.  设置找到的范围的外观。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#63](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#63)]
     [!code-vb[Trin_VstcoreExcelAutomation#63](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#63)]  
  
7.  再次执行搜索。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#64](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#64)]
     [!code-vb[Trin_VstcoreExcelAutomation#64](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#64)]  
  
 下面的示例演示完整的方法。  
  
## 示例  
 [!code-csharp[Trin_VstcoreExcelAutomation#57](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#57)]
 [!code-vb[Trin_VstcoreExcelAutomation#57](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#57)]  
  
## 请参阅  
 [使用范围](../vsto/working-with-ranges.md)   
 [如何：以编程方式将样式应用于工作簿中的所选区域](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)   
 [如何：以编程方式使用代码引用工作表范围](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)   
 [Office 解决方案中的可选参数](../vsto/optional-parameters-in-office-solutions.md)  
  
  