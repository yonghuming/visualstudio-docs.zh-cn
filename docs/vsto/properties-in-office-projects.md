---
title: "Office 项目中的属性 |Microsoft 文档"
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
- Trust Assemblies Location property
- Cache in Document property
- properties [Office development in Visual Studio]
- Namespace for Host Item property
- Office projects [Office development in Visual Studio], properties
- projects [Office development in Visual Studio], properties
- Value2 property
ms.assetid: 1284d6c3-8200-4151-88ce-0b5c7765af25
caps.latest.revision: "34"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 8c5832388db7e70791193024b263da275cdf5eaa
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="properties-in-office-projects"></a>Office 项目中的属性
  有几个重要属性可用于 Visual Studio 中的 Office 项目。 可在 **“属性”** 窗口中访问这些属性。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="namespace-for-host-item"></a>宿主项的命名空间  
 在 Visual C# 项目中，使用 **“主机项的命名空间”** 属性可以更改主机项类（例如 `ThisAddIn`、 `ThisWorkbook`或 `ThisDocument` 类）的命名空间。 在“解决方案资源管理器”  中选择文档级项目（如 ExcelWorkbook1.xlsx 或 WordDocument1.docx）中的文档节点或 VSTO 外接程序项目（如 Excel 或 Word）中的应用程序节点时，此属性将出现在“属性” 窗口中。  
  
 创建 Visual C# Office 项目时，将根据项目名称为主机项指定命名空间。 建议使用 **“主机项的命名空间”** 属性来更改命名空间，而不要直接编辑代码文件。 使用此属性时，将在生成的（隐藏）代码文件中和可见代码文件中更改命名空间。  
  
## <a name="cacheindocument"></a>CacheInDocument  
 在 Visual Studio 设计器中选择 **的实例时，文档级项目的** “属性” **窗口中将显示** “CacheInDocument” <xref:System.Data.DataSet> 属性。 仅可缓存公共成员；如果要缓存 **，请确保将** “修饰符” **属性设置为** “公共” <xref:System.Data.DataSet>。  
  
 此属性采用布尔值：  
  
-   选择 **true** 可将数据集缓存到文档中。  
  
-   如果不希望将数据集缓存到文档中，请选择 **false** 。  
  
 有关缓存数据的详细信息，请参阅 [Cached Data in Document-Level Customizations](../vsto/cached-data-in-document-level-customizations.md)。  
  
## <a name="value2"></a>Value2  
 **“Value2”** 属性仅可用于 Excel 工作簿或模板项目。 在工作表设计器中选择 **控件时，该属性将显示在** “属性” **窗口中的** “数据绑定” <xref:Microsoft.Office.Tools.Excel.NamedRange> 属性节点之下。  
  
 使用 **“属性”** 窗口中的 **“Value2”** 属性将 <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> 的 <xref:Microsoft.Office.Tools.Excel.NamedRange> 属性绑定到数据源中的字段。  
  
## <a name="see-also"></a>另请参阅  
 [设计和创建 Office 解决方案](../vsto/designing-and-creating-office-solutions.md)   
 [Office 项目模板概述](../vsto/office-project-templates-overview.md)   
 [Office 项目中的事件](../vsto/events-in-office-projects.md)  
  
  