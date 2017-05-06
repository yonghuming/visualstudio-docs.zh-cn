---
title: "缓存数据"
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
  - "数据缓存 [Visual Studio 中的 Office 开发]"
  - "数据缓存 [Visual Studio 中的 Office 开发], 关于缓存数据"
ms.assetid: 6f34251e-7d31-4f2b-ac17-42fd2837c626
caps.latest.revision: 36
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 35
---
# 缓存数据
  可将数据对象缓存在文档级自定义项中，以便能够脱机访问数据，或在没有打开 Microsoft Office Word 或 Microsoft Office Excel 的情况下访问数据。  若要缓存对象，则对象必须具有满足特定要求的数据类型。  .NET Framework 中的许多常见数据类型都满足这些要求，包括 <xref:System.String>、<xref:System.Data.DataSet> 和 <xref:System.Data.DataTable>。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 可以通过两种方法将对象添加到数据缓存中：  
  
-   若要在生成解决方案时将对象添加到数据缓存中，应将 <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> 特性应用于对象声明。  有关更多信息，请参见[如何：缓存数据以便脱机使用或在服务器上使用](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)。  
  
-   若要以编程方式在运行时将对象添加到数据缓存中，应使用宿主项（如 `ThisDocument` 或 `ThisWorkbook` 类）的 `StartCaching` 方法。  有关更多信息，请参见[如何：以编程方式在 Office 文档中缓存数据源](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)。  
  
 在将对象添加到数据缓存后，您就可以访问和修改缓存的数据，而无需启动 Word 或 Excel。  有关更多信息，请参见[访问服务器上的文档数据](../vsto/accessing-data-in-documents-on-the-server.md)。  
  
## 要缓存的数据对象的要求  
 若要将数据对象缓存到解决方案中，该对象必须满足下列要求：  
  
-   是宿主项的读\/写公共字段或属性，比如 `ThisDocument` 或 `ThisWorkbook` 类。  
  
-   不是索引器或其他参数化属性。  
  
 此外，该数据对象必须可按 <xref:System.Xml.Serialization.XmlSerializer> 类序列化，这意味着该对象类型必须具有以下特性：  
  
-   是一个公共类型。  
  
-   有一个不带参数的公共构造函数。  
  
-   不执行需要其他安全特权的代码。  
  
-   只公开读\/写公共属性（其他属性将被忽略）。  
  
-   不公开多维数组（但接受嵌套数组）。  
  
-   不从属性和字段返回接口。  
  
-   不实现 <xref:System.Collections.IDictionary>（如果为集合）。  
  
 当您缓存数据对象时，[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]会将该对象序列化为存储在文档的自定义 XML 部分中的一个 XML 字符串。  有关更多信息，请参见[自定义 XML 部件概述](../vsto/custom-xml-parts-overview.md)。  
  
## 缓存数据的大小限制  
 对于可添加到文档中的数据缓存的总数据量以及数据缓存中任何单个对象的大小，有一些限制。  如果超出这些限制，则当数据保存到数据缓存中时应用程序可能意外关闭。  
  
 若要避免这些限制，请遵循下列准则：  
  
-   不要将任何大于 10 MB 的对象添加到数据缓存中。  
  
-   不要将总量大于 100 MB 的数据添加到单一文档中的数据缓存中。  
  
 存在大概值。  准确的限制取决于一些因素，包括可用 RAM 和正在运行的进程的数量。  
  
## 控制缓存对象的行为  
 若要更大程度地控制缓存对象的行为，可以对缓冲对象的类型实现 <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType> 接口。  例如，如果希望控制对象更改时通知用户的方式，就可以实现此接口。  有关说明如何实现 <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType> 的代码示例，请参见 [Office 开发示例和演练](../vsto/office-development-samples-and-walkthroughs.md)中的 Excel 动态控件示例和 Word 动态控件示例中的 `ControlCollection` 类。  
  
## 在密码保护文档中保持对缓存数据的更改  
 如果将数据对象缓存到受密码保护的文档中，则不保存对缓存数据的更改。  您可以通过重写两个方法来保存对缓存数据的更改。  重写这些方法可以在保存文档时临时取消保护，然后在保存操作完成后重新应用保护。  
  
 有关更多信息，请参见[如何：在受密码保护的文档中缓存数据](../vsto/how-to-cache-data-in-a-password-protected-document.md)。  
  
## 在将 Null 值添加到数据缓存时防止数据丢失  
 在将对象添加到数据缓存时，必须在保存和关闭文档之前，将所有缓存对象初始化为非 **null** 值。  在保存和关闭文档时，如果有任何缓存对象具有 **null** 值，则 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]会自动将所有缓存对象从数据缓存中移除。  
  
 如果在设计时使用 <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> 特性，将值为 **null** 的对象添加到数据缓存中，就可以在打开文档之前使用 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> 类来初始化缓存数据对象。  如果您要在最终用户打开文档之前，在未安装 Word 或 Excel 的服务器上初始化缓存数据，则此方法非常有用。  有关更多信息，请参见[访问服务器上的文档数据](../vsto/accessing-data-in-documents-on-the-server.md)。  
  
## 请参阅  
 [如何：缓存数据以便脱机使用或在服务器上使用](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)   
 [如何：以编程方式在 Office 文档中缓存数据源](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)   
 [如何：在受密码保护的文档中缓存数据](../vsto/how-to-cache-data-in-a-password-protected-document.md)   
 [演练：使用缓存的数据集创建主&#47;从关系](../vsto/walkthrough-creating-a-master-detail-relation-using-a-cached-dataset.md)  
  
  