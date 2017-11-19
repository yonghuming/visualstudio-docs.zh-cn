---
title: "如何： 使用缓存数据，脱机或服务器上 |Microsoft 文档"
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
- data caching [Office development in Visual Studio], server use
- Office applications [Office development in Visual Studio], data
- datasets [Office development in Visual Studio], caching
- offline data [Office development in Visual Studio]
- data [Office development in Visual Studio], caching
- data caching [Office development in Visual Studio], offline use
ms.assetid: 6246b187-9413-4336-821d-2259b1adec5a
caps.latest.revision: "49"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7a8da60aa9d9dc3ab7becb56b3b4c7701494daef
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-cache-data-for-use-offline-or-on-a-server"></a>如何：缓存数据以便脱机使用或在服务器上使用
  你可以将标记在文档中，缓存的数据项，以便可脱机。 这还使其成为可能的数据中要文档存储在服务器上时，其他代码进行操作的文档。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 你可以将标记在代码中，声明的数据项时或者如果你使用缓存的数据项<xref:System.Data.DataSet>，通过设置属性**属性**窗口。 如果缓存不是数据项<xref:System.Data.DataSet>或<xref:System.Data.DataTable>，确保它达到缓存到文档中的条件。 有关更多信息，请参见 [Caching Data](../vsto/caching-data.md)。  
  
> [!NOTE]  
>  使用标记为 Visual Basic 创建的数据集**缓存**和**WithEvents** (包括从拖动的数据集**数据源**窗口或**工具箱**具有**CacheInDocument**属性设置为**True**) 作为其缓存中的名称的前缀是下划线。 例如，如果你创建数据集并将其命名**客户**、<xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem>名称将**_Customers**缓存中。 当你使用<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>若要访问此缓存的项目，必须指定**_Customers**而不是**客户**。  
  
### <a name="to-cache-data-in-the-document-using-code"></a>在使用代码的文档中缓存数据  
  
1.  作为在项目中，某个主机项类的成员中声明的公共字段或属性的数据项目将例如`ThisDocumen`Word 项目中的 t 类或`ThisWorkbook`Excel 项目中的类。  
  
2.  应用<xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute>给要将文档的数据缓存中存储的数据项标记的成员属性。 下面的示例将此特性应用于字段声明<xref:System.Data.DataSet>。  
  
     [!code-csharp[Trin_VstcoreDataExcel#11](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#11)]
     [!code-vb[Trin_VstcoreDataExcel#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#11)]  
  
3.  添加代码以创建数据项目的实例，如果适用，若要从数据库加载。  
  
     当首次创建; 仅加载数据项此后，缓存留与文档中，你必须编写其他代码以更新它。  
  
### <a name="to-cache-a-dataset-in-the-document-by-using-the-properties-window"></a>通过使用属性窗口中缓存文档中的数据集  
  
1.  将数据集添加到项目中，通过使用工具在 Visual Studio 设计器中，例如，通过将数据源添加到你的项目使用**数据源**窗口。  
  
2.  如果你尚未拥有一个，并不在设计器中选择的实例，请创建数据集的实例。  
  
3.  在**属性**窗口中，设置**CacheInDocument**属性**True**。  
  
     有关详细信息，请参阅[Office 项目中的属性](../vsto/properties-in-office-projects.md)。  
  
4.  在**属性**窗口中，设置**修饰符**属性**公共**(默认情况下它是**内部**)。  
  
## <a name="see-also"></a>另请参阅  
 [缓存数据](../vsto/caching-data.md)   
 [如何： 以编程方式缓存中的 Office 文档的数据源](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)   
 [如何： 在受密码保护的文档中缓存数据](../vsto/how-to-cache-data-in-a-password-protected-document.md)   
 [访问服务器上的文档中的数据](../vsto/accessing-data-in-documents-on-the-server.md)   
 [保存数据](/visualstudio/data-tools/saving-data)  
  
  