---
title: "如何：向文档级自定义项中添加自定义 XML 部件 | Microsoft Docs"
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
  - "文档级自定义项 [Visual Studio 中的 Office 开发]，自定义 XML 部件"
  - "Office 文档 [Visual Studio 中的 Office 开发，自定义 XML 部件"
  - "Word [Visual Studio 中的 Office 开发]，自定义 XML 部件"
  - "Excel [Visual Studio 中的 Office 开发]，自定义 XML 部件"
  - "自定义 XML 部件 [Visual Studio 中的 Office 开发]，添加"
  - "文档 [Visual Studio 中的 Office 开发]，自定义 XML 部件"
ms.assetid: e305a3d6-3a0e-4e72-ab8c-6a87a3590068
caps.latest.revision: 27
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 26
---
# 如何：向文档级自定义项中添加自定义 XML 部件
  你可以通过在文档级自定义中创建自定义 XML 部件将 XML 数据存储在 Microsoft Office Excel 工作表或 Microsoft Office Word 文档中。 有关详细信息，请参阅[自定义 XML 部件概述](../vsto/custom-xml-parts-overview.md)。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
> [!NOTE]  
>  Visual Studio 不提供 Microsoft Office PowerPoint 的文档级项目。 关于使用 VSTO 外接程序向 PowerPoint 演示文稿添加自定义 XML 部件的信息，请参阅 [如何：使用 VSTO 外接程序将自定义 XML 部件添加到文档](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md)。  
  
### 向 Excel 工作簿添加自定义 XML 部件  
  
1.  向工作簿中的 <xref:Microsoft.Office.Core.CustomXMLParts> 集合添加新 <xref:Microsoft.Office.Core.CustomXMLPart> 对象。<xref:Microsoft.Office.Core.CustomXMLPart> 包含你希望存储在工作簿中的 XML 字符串。  
  
     [!code-csharp[Trin_AddCustomXmlPartExcelDocLevel#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_AddCustomXmlPartExcelDocLevel/CS/ThisWorkbook.cs#1)]
     [!code-vb[Trin_AddCustomXmlPartExcelDocLevel#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_AddCustomXmlPartExcelDocLevel/VB/ThisWorkbook.vb#1)]  
  
2.  将 `AddCustomXmlPartToWorkbook` 方法添加到 Excel 文档级项目中的 `ThisWorkbook` 类。  
  
3.  从项目中的其他代码调用该方法。 例如，若要在用户打开工作簿时创建自定义 XML 部件，则从 `ThisWorkbook_Startup` 事件处理程序调用该方法。  
  
### 向 Word 文档添加自定义 XML 部件  
  
1.  向文档中的 <xref:Microsoft.Office.Core.CustomXMLParts> 集合添加新的 <xref:Microsoft.Office.Core.CustomXMLPart> 对象。<xref:Microsoft.Office.Core.CustomXMLPart> 包含你希望存储在文档中的 XML 字符串。  
  
     [!code-csharp[Trin_AddCustomXmlPartWordDocLevel#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_AddCustomXmlPartWordDocLevel/CS/ThisDocument.cs#1)]
     [!code-vb[Trin_AddCustomXmlPartWordDocLevel#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_AddCustomXmlPartWordDocLevel/VB/ThisDocument.vb#1)]  
  
2.  将 `AddCustomXmlPartToDocument` 方法添加到 Word 文档级项目中的 `ThisDocument` 类。  
  
3.  从项目中的其他代码调用该方法。 例如，若要在用户打开文档时创建自定义 XML 部件，则从 `ThisDocument_Startup` 事件处理程序调用该方法。  
  
## 可靠编程  
 为简单起见，此示例使用在方法中定义为局部变量的 XML 字符串。 通常，应从外部源（如文件或数据库）获取 XML。  
  
## 请参阅  
 [自定义 XML 部件概述](../vsto/custom-xml-parts-overview.md)   
 [如何：使用 VSTO 外接程序将自定义 XML 部件添加到文档](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md)  
  
  