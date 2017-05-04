---
title: "如何：缓存数据以便脱机使用或在服务器上使用 | Microsoft Docs"
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
  - "数据缓存 [Visual Studio 中的 Office 开发], 脱机使用"
  - "数据缓存 [Visual Studio 中的 Office 开发], 服务器使用"
  - "数据集 [Visual Studio 中的 Office 开发], 缓存"
  - "Office 应用程序 [Visual Studio 中的 Office 开发], 数据"
  - "脱机数据 [Visual Studio 中的 Office 开发]"
ms.assetid: 6246b187-9413-4336-821d-2259b1adec5a
caps.latest.revision: 49
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 48
---
# 如何：缓存数据以便脱机使用或在服务器上使用
  可以在文档中将某个数据项标记为要进行缓存，以便脱机使用该数据项。  这样，当文档存储在服务器中时，其他代码也可以对文档中的相应数据进行操作。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 在代码中声明某个数据项时，可以将该数据项标记为要进行缓存；如果正在使用 <xref:System.Data.DataSet>，可以在**“属性”**窗口中设置相应属性来完成这一操作。  如果要缓存的数据项不是 <xref:System.Data.DataSet> 或 <xref:System.Data.DataTable>，请确保该数据项满足在文档中缓存的条件。  有关更多信息，请参见[缓存数据](../vsto/caching-data.md)。  
  
> [!NOTE]  
>  在缓存中，以下数据集的名称前有一个下划线前缀：使用 Visual Basic 创建的且标记为 **Cached** 和 **WithEvents** 的数据集，包括从**“数据源”**窗口或**“工具箱”**中拖动的且**“CacheInDocument”**属性被设置为**“True”**的数据集。  例如，如果创建了一个数据集并将其命名为“Customers”，则 <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> 在缓存中的名称将是“\_Customers”。  当使用 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> 访问此缓存项时，必须指定 \_Customers 而不是 Customers。  
  
### 使用代码在文档中缓存数据  
  
1.  将数据项的某个公共字段或属性声明为项目中的宿主项类的成员，例如 Word 项目中的 `ThisDocumen`t 类或 Excel 项目中的 `ThisWorkbook` 类。  
  
2.  将 <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> 特性应用于成员，以标记要存储到文档的数据缓存中的数据项。  下面的示例将此特性应用于 <xref:System.Data.DataSet> 的字段声明。  
  
     [!code-csharp[Trin_VstcoreDataExcel#11](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet1.cs#11)]
     [!code-vb[Trin_VstcoreDataExcel#11](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet1.vb#11)]  
  
3.  添加代码以创建该数据项的一个实例，并从数据库加载该实例（如果适用）。  
  
     仅在首次创建数据项时加载该数据项，此后，缓存将与文档一同存储，您必须另外编写代码来更新该数据项。  
  
### 使用“属性”窗口在文档中缓存数据集  
  
1.  使用 Visual Studio 设计器中的工具将数据集添加到项目中，例如，使用**“数据源”**窗口将数据源添加到项目中。  
  
2.  如果还没有数据集的实例，可以创建一个数据集实例，然后在设计器中选择该实例。  
  
3.  在**“属性”**窗口中，将**“CacheInDocument”**属性设置为**“True”**。  
  
     有关更多信息，请参见[Office 项目中的属性](../vsto/properties-in-office-projects.md)。  
  
4.  在**“属性”**窗口中，将**“Modifiers”**属性设置为**“Public”**（默认情况下为**“Internal”**）。  
  
## 请参阅  
 [缓存数据](../vsto/caching-data.md)   
 [如何：以编程方式在 Office 文档中缓存数据源](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)   
 [如何：在受密码保护的文档中缓存数据](../vsto/how-to-cache-data-in-a-password-protected-document.md)   
 [访问服务器上的文档数据](../vsto/accessing-data-in-documents-on-the-server.md)   
 [保存数据](../data-tools/saving-data.md)  
  
  