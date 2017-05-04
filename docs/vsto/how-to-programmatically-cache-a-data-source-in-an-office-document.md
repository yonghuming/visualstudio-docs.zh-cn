---
title: "如何：以编程方式在 Office 文档中缓存数据源 | Microsoft Docs"
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
  - "数据 [Visual Studio 中的 Office 开发], 缓存"
  - "数据缓存 [Visual Studio 中的 Office 开发], 以编程方式"
  - "数据集 [Visual Studio 中的 Office 开发], 缓存"
  - "Office 应用程序 [Visual Studio 中的 Office 开发], 数据"
  - "StartCaching 方法"
ms.assetid: 70b3fc06-7534-407e-898b-36f84e9a7516
caps.latest.revision: 43
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 43
---
# 如何：以编程方式在 Office 文档中缓存数据源
  可以通过调用宿主项（如 <xref:Microsoft.Office.Tools.Word.Document>、<xref:Microsoft.Office.Tools.Excel.Workbook> 或 <xref:Microsoft.Office.Tools.Excel.Worksheet>）的 `StartCaching` 方法，以编程方式将数据对象添加到文档的数据缓存中。  通过调用宿主项的 `StopCaching` 方法来移除数据缓存中的数据对象。  
  
 `StartCaching` 方法和 `StopCaching` 方法都是私有方法，但它们出现在 IntelliSense 中。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 使用 `StartCaching` 方法向数据缓存添加数据对象时，不需要使用 <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> 特性声明数据对象。  但是，数据对象必须满足某些要求才能添加到数据缓存中。  有关更多信息，请参见[缓存数据](../vsto/caching-data.md)。  
  
### 以编程方式缓存数据对象  
  
1.  在类级别而不要在方法内部声明数据对象。  本示例假定您要声明一个名为 `dataSet1` 的 <xref:System.Data.DataSet>，您要以编程方式缓存该数据集。  
  
     [!code-csharp[Trin_VstcoreDataExcel#12](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet1.cs#12)]
     [!code-vb[Trin_VstcoreDataExcel#12](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet1.vb#12)]  
  
2.  实例化数据对象，然后调用文档或工作表实例的 `StartCaching` 方法并传入数据对象的名称。  
  
     [!code-csharp[Trin_VstcoreDataExcel#13](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet1.cs#13)]
     [!code-vb[Trin_VstcoreDataExcel#13](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet1.vb#13)]  
  
### 停止缓存数据对象  
  
1.  调用文档或工作表实例的 `StopCaching` 方法并传入数据对象的名称。  此示例假定您具有一个名为 `dataSet1` 的要停止缓存的 <xref:System.Data.DataSet>。  
  
     [!code-csharp[Trin_VstcoreDataExcel#14](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet1.cs#14)]
     [!code-vb[Trin_VstcoreDataExcel#14](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet1.vb#14)]  
  
    > [!NOTE]  
    >  不要从文档或工作表的 `Shutdown` 事件的事件处理程序调用 `StopCaching`。  当引发了 `Shutdown` 事件时，就来不及修改数据缓存了。  有关 `Shutdown` 事件的更多信息，请参见[Office 项目中的事件](../vsto/events-in-office-projects.md)。  
  
## 请参阅  
 [缓存数据](../vsto/caching-data.md)   
 [如何：缓存数据以便脱机使用或在服务器上使用](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)   
 [如何：在受密码保护的文档中缓存数据](../vsto/how-to-cache-data-in-a-password-protected-document.md)   
 [访问服务器上的文档数据](../vsto/accessing-data-in-documents-on-the-server.md)   
 [保存数据](../data-tools/saving-data.md)  
  
  