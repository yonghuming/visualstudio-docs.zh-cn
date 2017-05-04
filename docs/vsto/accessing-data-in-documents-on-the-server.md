---
title: "访问服务器上的文档数据 | Microsoft Docs"
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
  - "数据 [Visual Studio 中的 Office 开发], 在服务器上进行访问"
  - "数据访问 [Visual Studio 中的 Office 开发]"
ms.assetid: 14a42e96-ed2f-48a1-a0c0-e19f9eba4956
caps.latest.revision: 32
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 31
---
# 访问服务器上的文档数据
  您可以依据文档级自定义项中的数据进行编程，而不必使用 Microsoft Office Word 或 Microsoft Office Excel 的对象模型。  这意味着，您可以在未安装 Word 或 Excel 的服务器上访问包含在文档中的数据。  例如，服务器上的代码（例如，在 [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] 页中）可以自定义文档中的数据，并将自定义文档发送给最终用户。  当最终用户打开文档时，解决方案程序集中的数据绑定代码便会将自定义数据绑定到文档中。  这种做法之所以可行，是因为文档中的数据与用户界面是分离的。  有关更多信息，请参见[文档级自定义项中的缓存数据](../vsto/cached-data-in-document-level-customizations.md)。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## 缓存数据以便在服务器上使用  
 若要在文档中缓存数据对象，请在设计时使用 <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> 特性标记该数据对象，或在运行时使用宿主项的 `StartCaching` 方法。  当您将数据对象缓存在文档中时，[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]会将该对象序列化为存储在文档中的一个 XML 字符串。  对象必须符合一定的条件才能进行缓存。  有关更多信息，请参见[缓存数据](../vsto/caching-data.md)。  
  
 服务器端的代码可操作数据缓存中的任何数据对象。  绑定到已缓存的数据实例的控件与用户界面同步，因此，当在客户端打开文档时，在服务器端对数据所做的任何更改都会自动出现。  
  
## 访问缓存中的数据  
 可以从 Office 之外的应用程序访问缓存中的数据，例如，从控制台应用程序、Windows 窗体应用程序或网页进行访问。  访问缓存数据的应用程序必须具备完全信任；具备部分信任的 Web 应用程序不能插入、检索或更改 Office 文档中缓存的数据。  
  
 数据缓存可通过由 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> 类的 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> 属性所公开的集合的层次结构进行访问：  
  
-   <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> 属性返回 <xref:Microsoft.VisualStudio.Tools.Applications.CachedData>，它包含文档级自定义项中的所有缓存数据。  
  
-   每个 <xref:Microsoft.VisualStudio.Tools.Applications.CachedData> 包含一个或多个 <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem> 对象。  <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem> 包含单个类中定义的所有缓存数据对象。  
  
-   每个 <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem> 包含一个或多个 <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> 对象。  <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> 表示单个缓存数据对象。  
  
 下面的代码示例演示如何访问在 Excel 工作簿项目的 `Sheet1` 类中缓存的字符串。  此示例摘自一个为 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.Save%2A> 方法提供的更大的示例。  
  
 [!code-csharp[Trin_ServerDocument#12](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ServerDocument/CS/Form1.cs#12)]
 [!code-vb[Trin_ServerDocument#12](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ServerDocument/VB/Form1.vb#12)]  
  
## 修改缓存中的数据  
 若要修改缓存数据对象，通常可执行下列操作：  
  
1.  将缓存对象的 XML 表示形式反序列化为该对象的一个新实例。  通过使用表示该缓存数据对象的 <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> 的 <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.Xml%2A> 属性，可以访问与之相应的 XML。  
  
2.  对此副本进行更改。  
  
3.  使用下列选项之一，将更改后的对象重新序列化到数据缓存中：  
  
    -   如果要自动序列化所做的更改，请使用 <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.SerializeDataInstance%2A> 方法。  此方法使用 **DiffGram** 格式将 <xref:System.Data.DataSet>、<xref:System.Data.DataTable> 和类型化数据集对象序列化为数据缓存。  **DiffGram** 格式确保将对脱机文档中的数据缓存更改正确发送到服务器。  
  
    -   如果希望对缓存数据更改执行自己的序列化，可直接写入 <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.Xml%2A> 属性。  如果使用 <xref:System.Data.Common.DataAdapter> 更新对 <xref:System.Data.DataSet>、<xref:System.Data.DataTable> 或类型化数据集中的数据进行了更改的数据库，请指定 **DiffGram** 格式。  否则，<xref:System.Data.Common.DataAdapter> 将通过添加新行而不是修改现有行的方式来更新数据库。  
  
### 在不反序列化当前值的情况下修改数据  
 在某些情况下，可能需要直接修改缓存对象的值，而不是先对当前值进行反序列化。  例如，如果要更改具有简单类型（例如，字符串型或整型）的对象的值，或在服务器上初始化文档中缓存的 <xref:System.Data.DataSet>，就可以这样做。  在这些情况下，可以直接使用 <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.SerializeDataInstance%2A> 方法，而不用先反序列化缓存对象的当前值。  
  
 下面的代码示例演示如何更改在 Excel 工作簿项目的 `Sheet1` 类中缓存的字符串的值。  此示例摘自一个为 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.Save%2A> 方法提供的更大的示例。  
  
 [!code-csharp[Trin_ServerDocument#11](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ServerDocument/CS/Form1.cs#11)]
 [!code-vb[Trin_ServerDocument#11](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ServerDocument/VB/Form1.vb#11)]  
  
### 修改数据缓存中的 Null 值  
 在保存和关闭文档时，数据缓存不会存储值为 **null** 的对象。  此限制会对缓存数据的修改产生下列影响：  
  
-   在将数据缓存中的任意对象设置为 **null** 值后，数据缓存中的所有对象都将在文档打开时自动设置为 **null**，这样在保存和关闭文档时将清除整个数据缓存。  换言之，数据缓存中的所有缓存对象都将被移除，且 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> 集合将变为空。  
  
-   如果生成的解决方案在数据缓存中含有 **null** 对象，并且您希望在首次打开文档之前使用 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> 类初始化这些对象，则必须确保初始化该数据缓存中的所有对象。  如果只初始化其中的部分对象，则在打开文档时，所有对象都将设置为 **null**，这样在保存和关闭文档时将清除整个数据缓存。  
  
## 访问缓存中的类型化数据集  
 如果要访问来自 Office 解决方案和 Office 之外的应用程序（如 Windows 窗体应用程序或 [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] 项目）的类型化数据集中的数据，则必须在两个项目中均引用的单独的程序集中定义类型化数据集。  如果使用**“数据源配置向导”**或**“数据集设计器”**向每个项目添加类型化数据集，则 .NET Framework 将这两个项目中的类型化程序集视为不同的类型。  有关创建类型化数据集的更多信息，请参见[如何：创建类型化数据集](../Topic/Creating%20and%20configuring%20datasets%20in%20Visual%20Studio.md)。  
  
## 请参阅  
 [Accessing Data in Documents on the Server](../vsto/accessing-data-in-documents-on-the-server.md)   
 [文档级自定义项中的缓存数据](../vsto/cached-data-in-document-level-customizations.md)  
  
  