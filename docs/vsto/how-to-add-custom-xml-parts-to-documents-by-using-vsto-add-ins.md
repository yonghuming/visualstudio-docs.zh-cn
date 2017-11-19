---
title: "如何： 使用 VSTO 外接程序将自定义 XML 部件添加到文档 |Microsoft 文档"
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
- add-ins [Office development in Visual Studio], custom XML parts
- Office documents [Office development in Visual Studio, custom XML parts
- Word [Office development in Visual Studio], custom XML parts
- PowerPoint [Office development in Visual Studio], custom XML parts
- Excel [Office development in Visual Studio], custom XML parts
- custom XML parts [Office development in Visual Studio], adding
- documents [Office development in Visual Studio], custom XML parts
- application-level add-ins [Office development in Visual Studio], custom XML parts
ms.assetid: 872d2beb-193b-49f9-9a7b-dcebab91a73b
caps.latest.revision: "27"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e851c0dcdbb3ed86dcf4a303cc1ad26b65035bc8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins"></a>如何：使用 VSTO 外接程序将自定义 XML 部件添加到文档
  通过在 VSTO 外接程序中创建自定义 XML 部件，可以将 XML 数据存储在以下类型的文档中：  
  
-   Microsoft Office Excel 工作簿。  
  
-   Microsoft Office Word 文档。  
  
-   Microsoft Office PowerPoint 演示文稿。  
  
 有关详细信息，请参阅 [Custom XML Parts Overview](../vsto/custom-xml-parts-overview.md)。  
  
 **适用于：** 本主题中的信息适用于 Excel、PowerPoint 和 Word 的应用程序级项目。 有关详细信息，请参阅 [Features Available by Office Application and Project Type](../vsto/features-available-by-office-application-and-project-type.md)。  
  
### <a name="to-add-a-custom-xml-part-to-an-excel-workbook"></a>向 Excel 工作簿添加自定义 XML 部件  
  
1.  向工作簿中的 <xref:Microsoft.Office.Core.CustomXMLPart> 集合添加新 <xref:Microsoft.Office.Interop.Excel._Workbook.CustomXMLParts%2A> 对象。 <xref:Microsoft.Office.Core.CustomXMLPart> 包含你希望存储在工作簿中的 XML 字符串。  
  
     下面的代码示例向指定工作簿添加自定义 XML 部件。  
  
     [!code-vb[Trin_AddCustomXmlPartExcelAppLevel#1](../vsto/codesnippet/VisualBasic/trin_addcustomxmlpartexcelapplevel/ThisAddIn.vb#1)]
     [!code-csharp[Trin_AddCustomXmlPartExcelAppLevel#1](../vsto/codesnippet/CSharp/Trin_AddCustomXmlPartExcelAppLevel/ThisAddIn.cs#1)]  
  
2.  将 `AddCustomXmlPartToWorkbook` 方法添加到 Excel 的 VSTO 外接程序项目中的 `ThisAddIn` 类。  
  
3.  从项目中的其他代码调用该方法。 例如，若要在用户打开工作簿时创建自定义 XML 部件，可从 <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookOpen> 事件的事件处理程序调用该方法。  
  
### <a name="to-add-a-custom-xml-part-to-a-word-document"></a>向 Word 文档添加自定义 XML 部件  
  
1.  向文档中的 <xref:Microsoft.Office.Core.CustomXMLPart> 集合添加新的 <xref:Microsoft.Office.Interop.Word._Document.CustomXMLParts%2A> 对象。 <xref:Microsoft.Office.Core.CustomXMLPart> 包含你希望存储在文档中的 XML 字符串。  
  
     下面的代码示例向指定文档添加自定义 XML 部件。  
  
     [!code-vb[Trin_AddCustomXmlPartWordAppLevel#1](../vsto/codesnippet/VisualBasic/Trin_AddCustomXmlPartWordAppLevel/ThisAddIn.vb#1)]
     [!code-csharp[Trin_AddCustomXmlPartWordAppLevel#1](../vsto/codesnippet/CSharp/Trin_AddCustomXmlPartWordAppLevel/ThisAddIn.cs#1)]  
  
2.  将 `AddCustomXmlPartToDocument` 方法添加到 Word 的 VSTO 外接程序项目中的 `ThisAddIn` 类。  
  
3.  从项目中的其他代码调用该方法。 例如，若要在用户打开文档时创建自定义 XML 部件，可从 <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen> 事件的事件处理程序调用该方法。  
  
### <a name="to-add-a-custom-xml-part-to-a-powerpoint-presentation"></a>向 PowerPoint 演示文稿添加自定义 XML 部件  
  
1.  向演示文稿中的 <xref:Microsoft.Office.Core.CustomXMLPart> 集合添加新的 <xref:Microsoft.Office.Interop.PowerPoint._Presentation.CustomXMLParts%2A> 对象。 <xref:Microsoft.Office.Core.CustomXMLPart> 包含你希望存储在演示文稿中的 XML 字符串。  
  
     下面的代码示例向指定演示文稿添加自定义 XML 部件。  
  
     [!code-csharp[Trin_AddCustomXmlPartPowerPointAppLevel#1](../vsto/codesnippet/CSharp/Trin_AddCustomXmlPartPowerPointAppLevel/ThisAddIn.cs#1)]
     [!code-vb[Trin_AddCustomXmlPartPowerPointAppLevel#1](../vsto/codesnippet/VisualBasic/Trin_AddCustomXmlPartPowerPointAppLevel/ThisAddIn.vb#1)]  
  
2.  将 `AddCustomXmlPartToPresentation` 方法添加到 PowerPoint 的 VSTO 外接程序项目中的 `ThisAddIn` 类。  
  
3.  从项目中的其他代码调用该方法。 例如，若要在用户打开演示文稿时创建自定义 XML 部件，可从 <xref:Microsoft.Office.Interop.PowerPoint.EApplication_Event.AfterPresentationOpen> 事件的事件处理程序调用该方法。  
  
## <a name="robust-programming"></a>可靠编程  
 为简单起见，此示例使用在方法中定义为局部变量的 XML 字符串。 通常，应从外部源（如文件或数据库）获取 XML。  
  
## <a name="see-also"></a>另请参阅  
 [Custom XML Parts Overview](../vsto/custom-xml-parts-overview.md)   
 [如何：将自定义 XML 部件添加到文档级自定义项](../vsto/how-to-add-custom-xml-parts-to-document-level-customizations.md)  
  
  