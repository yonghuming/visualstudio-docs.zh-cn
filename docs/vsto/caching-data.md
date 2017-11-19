---
title: "缓存数据 |Microsoft 文档"
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
- data caching [Office development in Visual Studio], about caching data
- data [Office development in Visual Studio], caching
- data caching [Office development in Visual Studio]
ms.assetid: 6f34251e-7d31-4f2b-ac17-42fd2837c626
caps.latest.revision: "36"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 0d5f044f1f1d0f36918939a67d9d2e5bb1899929
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="caching-data"></a>缓存数据
  你可以缓存文档级自定义项中的数据对象，以便脱机，或无需打开 Microsoft Office Word 或 Microsoft Office Excel 可以访问的数据。 若要缓存对象，该对象必须满足某些要求的数据类型。 .NET Framework 中的许多常见数据类型满足这些要求，包括<xref:System.String>， <xref:System.Data.DataSet>，和<xref:System.Data.DataTable>。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 有两种方法将对象添加到数据缓存：  
  
-   若要生成解决方案时，将对象添加到数据缓存，应用<xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute>到对象声明属性。 有关详细信息，请参阅[如何： 缓存数据以脱机使用，或在服务器上](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)。  
  
-   若要以编程方式添加的对象到数据缓存在运行时，使用`StartCaching`方法的主机项，如`ThisDocument`或`ThisWorkbook`类。 有关详细信息，请参阅[如何： 以编程方式缓存 Office 文档中的数据源](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)。  
  
 将对象添加到数据缓存后，你可以访问和修改而无需启动 Word 或 Excel 的缓存的数据。 有关详细信息，请参阅 [Accessing Data in Documents on the Server](../vsto/accessing-data-in-documents-on-the-server.md)。  
  
## <a name="requirements-for-data-objects-to-be-cached"></a>对于缓存的数据对象的要求  
 若要缓存解决方案中的数据对象，该对象必须满足以下要求：  
  
-   为读/写公共字段或属性的主机项，例如`ThisDocument`或`ThisWorkbook`类。  
  
-   不是一个索引器或其他参数化的属性。  
  
 此外，数据对象必须可由序列化<xref:System.Xml.Serialization.XmlSerializer>类，这意味着对象的类型必须具有以下特征：  
  
-   为公共类型。  
  
-   具有任何参数的公共构造函数。  
  
-   不执行需要额外的安全权限的代码。  
  
-   公开仅读/写公共属性 （将忽略其他属性）。  
  
-   不公开多维数组 （嵌套的数组已接受）。  
  
-   没有返回从属性和字段的接口。  
  
-   未实现<xref:System.Collections.IDictionary>如果集合。  
  
 当缓存数据对象，[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]对象序列化为的 XML 字符串存储在*自定义 XML 部件*文档中。 有关详细信息，请参阅 [Custom XML Parts Overview](../vsto/custom-xml-parts-overview.md)。  
  
## <a name="cached-data-size-limits"></a>缓存的数据大小限制  
 有一些限制到总可以将添加到的数据缓存中一个文档，以及数据缓存中任何单个对象的大小的数据量。 如果超过这些限制，当数据保存到数据缓存应用程序可能会意外关闭。  
  
 若要避免这些限制，请遵循以下准则：  
  
-   不将任何大于 10 MB 的对象添加到数据缓存。  
  
-   不要向单个文档中的数据缓存中添加超过 100 MB 总数据量。  
  
 这些是近似的值。 确切的限制取决于多种因素，包括可用 RAM 和正在运行的进程数。  
  
## <a name="controlling-the-behavior-of-cached-objects"></a>控制缓存对象的行为  
 若要获得更好地控制缓存对象的行为，可以实现<xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType>接口上的缓存对象的类型。 例如，如果你想要控制当对象已更改时用户的通知方式可以实现此接口。 有关代码示例演示如何实现<xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType>，请参阅`ControlCollection`类中的动态控件示例的 Excel 和 Word 中的动态控件示例[Office 开发示例和演练](../vsto/office-development-samples-and-walkthroughs.md)。  
  
## <a name="persisting-changes-to-cached-data-in-password-protected-documents"></a>到受密码保护的文档中缓存的数据持久保存更改  
 如果缓存中使用密码保护的文档数据对象时，将不保存对缓存数据的更改。 通过重写两种方法，可以将更改保存到缓存的数据。 重写这些方法时保存文档，暂时删除保护，然后重新应用在保存后的保护的操作已完成。  
  
 有关详细信息，请参阅[如何： 在 Password-Protected 文档中缓存数据](../vsto/how-to-cache-data-in-a-password-protected-document.md)。  
  
## <a name="preventing-data-loss-when-adding-null-values-to-the-data-cache"></a>防止数据丢失，当将 Null 值添加到数据缓存  
 在将对象添加到数据缓存中，所有缓存的对象必须初始化为非**null**值保存和关闭文档之前。 如果任何缓存的对象具有**null**值时保存文档并将其关闭，[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]自动将数据缓存中删除所有缓存的对象。  
  
 如果添加的对象与**null**数据缓存使用的值<xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute>属性在设计时，可以使用<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>类以初始化缓存的数据对象之前打开该文档。 这是你想要初始化未 Word 或 Excel 之前由最终用户打开该文档中安装的服务器上的缓存的数据的情况下很有用。 有关详细信息，请参阅 [Accessing Data in Documents on the Server](../vsto/accessing-data-in-documents-on-the-server.md)。  
  
## <a name="see-also"></a>另请参阅  
 [如何： 使用缓存数据，脱机或服务器上](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)   
 [如何： 以编程方式缓存中的 Office 文档的数据源](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)   
 [如何： 在受密码保护的文档中缓存数据](../vsto/how-to-cache-data-in-a-password-protected-document.md)   
 [演练：使用缓存的数据集创建主从关系](../vsto/walkthrough-creating-a-master-detail-relation-using-a-cached-dataset.md)  
  
  