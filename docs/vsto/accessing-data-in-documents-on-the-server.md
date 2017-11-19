---
title: "访问服务器上的文档中的数据 |Microsoft 文档"
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
- data [Office development in Visual Studio], accessing on server
- data access [Office development in Visual Studio]
ms.assetid: 14a42e96-ed2f-48a1-a0c0-e19f9eba4956
caps.latest.revision: "32"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 8345f7d197f44455ae990c159550587bbc79de24
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="accessing-data-in-documents-on-the-server"></a>访问服务器上的文档数据
  可以编程的文档级自定义项中的数据而无需使用 Microsoft Office Word 或 Microsoft Office Excel 的对象模型。 这意味着你可以访问未安装 Word 的服务器上的文档中包含的数据或安装 Excel。 例如，在服务器上的代码 (例如，在[!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)]页) 可以自定义文档中的数据并将自定义的文档发送给最终用户。 当最终用户打开文档时，解决方案程序集中的数据绑定代码将自定义的数据绑定到文档中。 这可能是由于从用户界面分开的文档中的数据。 有关详细信息，请参阅[文档级自定义项中缓存数据](../vsto/cached-data-in-document-level-customizations.md)。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## <a name="caching-data-for-use-on-a-server"></a>在服务器上使用的缓存数据  
 若要缓存文档中的数据对象，将其与标记<xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute>属性在设计时，或使用`StartCaching`方法在运行时将主机项。 当缓存文档中的数据对象[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]对象序列化为文档中存储的 XML 字符串。 对象必须满足某些要求可进行缓存。 有关更多信息，请参见 [Caching Data](../vsto/caching-data.md)。  
  
 服务器端代码可以处理任何数据缓存中的数据对象。 控件绑定到缓存的数据实例同步与用户界面中，以便对数据所做的任何服务器端更改会自动显示在客户端上打开文档时。  
  
## <a name="accessing-data-in-the-cache"></a>访问缓存中的数据  
 你可以从外部 Office，例如从一个控制台应用程序、 Windows 窗体应用程序或网页上的应用程序访问缓存中的数据。 访问缓存的数据的应用程序必须具有完全信任;具有部分信任的 Web 应用程序不能插入、 检索，或更改在 Office 文档中缓存的数据。  
  
 数据缓存可公开的集合的层次结构进行<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A>属性<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>类：  
  
-   <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A>属性返回<xref:Microsoft.VisualStudio.Tools.Applications.CachedData>，其中包含所有的文档级自定义项中缓存的数据。  
  
-   每个<xref:Microsoft.VisualStudio.Tools.Applications.CachedData>包含一个或多个<xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem>对象。 A<xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem>包含所有缓存的数据对象在单个类中定义。  
  
-   每个<xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem>包含一个或多个<xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem>对象。 A<xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem>表示单个缓存的数据对象。  
  
 下面的代码示例演示如何访问中的缓存的字符串`Sheet1`的 Excel 工作簿项目的类。 此示例摘自更大的示例为提供<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.Save%2A>方法。  
  
 [!code-csharp[Trin_ServerDocument#12](../vsto/codesnippet/CSharp/Trin_ServerDocument/Form1.cs#12)]
 [!code-vb[Trin_ServerDocument#12](../vsto/codesnippet/VisualBasic/Trin_ServerDocument/Form1.vb#12)]  
  
## <a name="modifying-data-in-the-cache"></a>在缓存中修改数据  
 若要修改的缓存的数据对象，你通常会执行以下步骤：  
  
1.  反序列化的 XML 表示形式的缓存对象到对象的新实例。 你可以通过使用访问 XML<xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.Xml%2A>属性<xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem>表示缓存的数据对象。  
  
2.  对此副本进行更改。  
  
3.  将序列化已更改的对象返回到数据缓存通过使用以下选项之一：  
  
    -   如果你想要自动序列化所做的更改，使用<xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.SerializeDataInstance%2A>方法。 此方法使用**DiffGram**用于序列化格式<xref:System.Data.DataSet>， <xref:System.Data.DataTable>，并且数据缓存内键入数据集对象。 **DiffGram**格式可确保对数据缓存对脱机文档中的更改正确发送到服务器。  
  
    -   如果你想要对缓存的数据的更改执行你自己的序列化，你可以直接写入<xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.Xml%2A>属性。 指定**DiffGram**格式如果你使用<xref:System.Data.Common.DataAdapter>来更新数据库中的数据所做的更改<xref:System.Data.DataSet>， <xref:System.Data.DataTable>，或类型化数据集。 否则为<xref:System.Data.Common.DataAdapter>将通过添加新行，而不是修改现有的行更新数据库。  
  
### <a name="modifying-data-without-deserializing-the-current-value"></a>修改数据而无需反序列化的当前值  
 在某些情况下，你可能想要修改的缓存的对象的值，而不必先的反序列化的当前值。 例如，你可以执行此操作或如果您要更改的值的对象具有简单类型，如字符串或整数，如果要初始化缓存<xref:System.Data.DataSet>在服务器上的文档。 在这些情况下，你可以使用<xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.SerializeDataInstance%2A>方法，而第一个进行反序列化的缓存的对象的当前值。  
  
 下面的代码示例演示如何更改缓存中字符串值`Sheet1`的 Excel 工作簿项目的类。 此示例摘自更大的示例为提供<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.Save%2A>方法。  
  
 [!code-csharp[Trin_ServerDocument#11](../vsto/codesnippet/CSharp/Trin_ServerDocument/Form1.cs#11)]
 [!code-vb[Trin_ServerDocument#11](../vsto/codesnippet/VisualBasic/Trin_ServerDocument/Form1.vb#11)]  
  
### <a name="modifying-null-values-in-the-data-cache"></a>修改数据缓存中的 Null 值  
 数据缓存不会存储具有值的对象**null**保存并关闭文档时。 当你修改缓存的数据时，此限制将有几个结果：  
  
-   如果将任何对象设置为值数据缓存中**null**，所有数据缓存中的对象将自动设置为**null**时打开该文档，并且整个数据缓存将被清除时保存文档并将其关闭。 所有缓存的对象将从数据缓存中，删除的即与<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A>集合将为空。  
  
-   如果你要构建一个具有解决方案**null**中对象的数据缓存和你想要使用初始化这些对象<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>首次打开文档之前的类，必须确保你的所有对象初始化在数据缓存中。 如果只有某些对象初始化，所有对象将设置为**null**当打开文档，并保存并关闭文档时，将清除整个数据缓存。  
  
## <a name="accessing-typed-datasets-in-the-cache"></a>访问缓存中的类型化数据集  
 如果你想要访问中的类型化数据集的数据，从 Office 解决方案和从外部的应用程序 Office，如 Windows 窗体应用程序或[!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)]项目中，你必须在单独的程序集引用中都定义类型化数据集项目。 将类型化数据集到每个项目添加使用**数据源配置向导**或**数据集设计器**，.NET Framework 会为不同类型的两个项目中将类型化数据集. 有关创建类型化数据集的详细信息，请参阅[创建和配置 Visual Studio 中的数据集](/visualstudio/data-tools/create-and-configure-datasets-in-visual-studio)。  
  
## <a name="see-also"></a>另请参阅  
 [访问服务器上的文档中的数据](../vsto/accessing-data-in-documents-on-the-server.md)   
 [文档级自定义项中的缓存数据](../vsto/cached-data-in-document-level-customizations.md)  
  
  