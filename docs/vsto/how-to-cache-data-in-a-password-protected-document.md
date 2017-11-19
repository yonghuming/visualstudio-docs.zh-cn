---
title: "如何： 在受密码保护的文档中缓存数据 |Microsoft 文档"
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
- data caching [Office development in Visual Studio], protected documents
- datasets [Office development in Visual Studio], caching
- data [Office development in Visual Studio], caching
ms.assetid: 91b865fc-bd01-438f-ac63-2fe3175bc2e8
caps.latest.revision: "23"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: eb1dd096b08525cd03f65ed46def81979bfaf272
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-cache-data-in-a-password-protected-document"></a>如何：在受密码保护的文档中缓存数据
  如果数据添加到的数据缓存中的文档或使用密码保护的工作簿时，将不会自动保存对缓存数据的更改。 通过重写你的项目中的两种方法，可以将更改保存到缓存的数据。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## <a name="caching-in-word-documents"></a>在 Word 文档中缓存  
  
#### <a name="to-cache-data-in-a-word-document-that-is-protected-with-a-password"></a>在使用密码保护的 Word 文档中缓存数据  
  
1.  在`ThisDocument`类中，标记的公共字段或属性将缓存。 有关更多信息，请参见 [Caching Data](../vsto/caching-data.md)。  
  
2.  重写<xref:Microsoft.Office.Tools.Word.DocumentBase.UnprotectDocument%2A>中的方法`ThisDocument`类，并从文档中删除保护。  
  
     保存文档后，[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]调用此方法来为你提供取消保护文档的机会。 这使对缓存的数据要保存更改。  
  
3.  重写<xref:Microsoft.Office.Tools.Word.DocumentBase.ProtectDocument%2A>中的方法`ThisDocument`类并重新应用到文档的保护。  
  
     保存文档后，[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]调用此方法来为你提供机会重新应用到文档的保护。  
  
### <a name="example"></a>示例  
 下面的代码示例演示如何在使用密码保护的 Word 文档中缓存数据。 代码移除中的保护之前<xref:Microsoft.Office.Tools.Word.DocumentBase.UnprotectDocument%2A>方法，它将保存当前<xref:Microsoft.Office.Tools.Word.Document.ProtectionType%2A>值，以便可以在中重新应用相同类型的保护<xref:Microsoft.Office.Tools.Word.DocumentBase.ProtectDocument%2A>方法。  
  
 [!code-csharp[Trin_CachedDataProtectedDocument#1](../vsto/codesnippet/CSharp/Trin_CachedDataProtectedDocument/ThisDocument.cs#1)]
 [!code-vb[Trin_CachedDataProtectedDocument#1](../vsto/codesnippet/VisualBasic/Trin_CachedDataProtectedDocument/ThisDocument.vb#1)]  
  
### <a name="compiling-the-code"></a>编译代码  
 添加此代码与`ThisDocument`项目中的类。 此代码假定该密码存储在名为的字段中`securelyStoredPassword`。  
  
## <a name="caching-in-excel-workbooks"></a>在 Excel 工作簿中缓存  
 在 Excel 项目中，则需要此过程仅当你通过使用保护整个工作簿使用的密码时<xref:Microsoft.Office.Tools.Excel.Workbook.Protect%2A>方法。 此过程不是必需的如果你通过使用保护仅密码的特定工作表<xref:Microsoft.Office.Tools.Excel.Worksheet.Protect%2A>方法。  
  
#### <a name="to-cache-data-in-an-excel-workbook-that-is-protected-with-a-password"></a>在使用密码保护的 Excel 工作簿中缓存数据  
  
1.  在`ThisWorkbook`类或之一`Sheet`  *n* 类中，标记的公共字段或属性将缓存。 有关更多信息，请参见 [Caching Data](../vsto/caching-data.md)。  
  
2.  重写<xref:Microsoft.Office.Tools.Excel.WorkbookBase.UnprotectDocument%2A>中的方法`ThisWorkbook`类，并从该工作簿中删除保护。  
  
     保存工作簿后，[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]调用此方法来为你提供机会取消保护工作簿。 这使对缓存的数据要保存更改。  
  
3.  重写<xref:Microsoft.Office.Tools.Excel.WorkbookBase.ProtectDocument%2A>中的方法`ThisWorkbook`类并重新应用到文档的保护。  
  
     保存工作簿后，[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]调用此方法来为你提供机会对工作簿重新应用保护。  
  
### <a name="example"></a>示例  
 下面的代码示例演示如何在使用密码保护的 Excel 工作簿中缓存数据。 代码移除中的保护之前<xref:Microsoft.Office.Tools.Excel.WorkbookBase.UnprotectDocument%2A>方法，它将保存当前<xref:Microsoft.Office.Tools.Excel.Workbook.ProtectStructure%2A>和<xref:Microsoft.Office.Tools.Excel.Workbook.ProtectWindows%2A>值，以便可以在中重新应用相同类型的保护<xref:Microsoft.Office.Tools.Excel.WorkbookBase.ProtectDocument%2A>方法。  
  
 [!code-vb[Trin_CachedDataProtectedWorkbook#1](../vsto/codesnippet/VisualBasic/Trin_CachedDataProtectedWorkbook/ThisWorkbook.vb#1)]
 [!code-csharp[Trin_CachedDataProtectedWorkbook#1](../vsto/codesnippet/CSharp/Trin_CachedDataProtectedWorkbook/ThisWorkbook.cs#1)]  
  
### <a name="compiling-the-code"></a>编译代码  
 添加此代码与`ThisWorkbook`项目中的类。 此代码假定该密码存储在名为的字段中`securelyStoredPassword`。  
  
## <a name="see-also"></a>另请参阅  
 [缓存数据](../vsto/caching-data.md)   
 [如何： 使用缓存数据，脱机或服务器上](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)   
 [如何：以编程方式在 Office 文档中缓存数据源](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)  
  
  