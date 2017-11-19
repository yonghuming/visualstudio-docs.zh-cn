---
title: "如何： 以编程方式缓存中的 Office 文档的数据源 |Microsoft 文档"
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
- Office applications [Office development in Visual Studio], data
- datasets [Office development in Visual Studio], caching
- StartCaching method
- data caching [Office development in Visual Studio], programmatically
- data [Office development in Visual Studio], caching
ms.assetid: 70b3fc06-7534-407e-898b-36f84e9a7516
caps.latest.revision: "43"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 2952ee6de3321300ad87053f0e5c385357fe0ba2
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-programmatically-cache-a-data-source-in-an-office-document"></a>如何：以编程方式在 Office 文档中缓存数据源
  你可以以编程方式添加数据对象到文档中的数据缓存通过调用`StartCaching`方法的主机项，如<xref:Microsoft.Office.Tools.Word.Document>， <xref:Microsoft.Office.Tools.Excel.Workbook>，或<xref:Microsoft.Office.Tools.Excel.Worksheet>。 从数据缓存中删除数据对象，通过调用`StopCaching`将主机项的方法。  
  
 `StartCaching`方法和`StopCaching`方法都私有的但它们会出现在 IntelliSense。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 当你使用`StartCaching`方法将数据对象添加到数据缓存中，数据对象不需要使用声明<xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute>属性。 但是，数据对象必须满足某些要求才能添加到数据缓存。 有关更多信息，请参见 [Caching Data](../vsto/caching-data.md)。  
  
### <a name="to-programmatically-cache-a-data-object"></a>若要以编程方式缓存数据对象  
  
1.  声明在类级别，而不是在方法的数据对象。 此示例假定你将声明<xref:System.Data.DataSet>名为`dataSet1`你想要以编程方式缓存。  
  
     [!code-csharp[Trin_VstcoreDataExcel#12](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#12)]
     [!code-vb[Trin_VstcoreDataExcel#12](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#12)]  
  
2.  实例化数据对象，然后调用`StartCaching`方法文档或工作表的实例并传入数据对象的名称。  
  
     [!code-csharp[Trin_VstcoreDataExcel#13](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#13)]
     [!code-vb[Trin_VstcoreDataExcel#13](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#13)]  
  
### <a name="to-stop-caching-a-data-object"></a>若要停止缓存数据对象  
  
1.  调用`StopCaching`方法文档或工作表的实例并传入数据对象的名称。 此示例假定你有<xref:System.Data.DataSet>名为`dataSet1`你想要停止缓存。  
  
     [!code-csharp[Trin_VstcoreDataExcel#14](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#14)]
     [!code-vb[Trin_VstcoreDataExcel#14](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#14)]  
  
    > [!NOTE]  
    >  不要调用`StopCaching`的事件处理程序从`Shutdown`的文档或工作表的事件。 按时间`Shutdown`引发事件，就太迟修改数据缓存。 有关详细信息`Shutdown`事件，请参阅[Office 项目中的事件](../vsto/events-in-office-projects.md)。  
  
## <a name="see-also"></a>另请参阅  
 [缓存数据](../vsto/caching-data.md)   
 [如何： 使用缓存数据，脱机或服务器上](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)   
 [如何： 在受密码保护的文档中缓存数据](../vsto/how-to-cache-data-in-a-password-protected-document.md)   
 [访问服务器上的文档中的数据](../vsto/accessing-data-in-documents-on-the-server.md)   
 [保存数据](/visualstudio/data-tools/saving-data)  
  
  