---
title: "文档级自定义项中已缓存数据 |Microsoft 文档"
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
- data islands [Office development in Visual Studio]
- view [Office development in Visual Studio]
- caching data [Office development in Visual Studio], about caching data
- data caching [Office development in Visual Studio], about data caching
- data [Office development in Visual Studio], cache
- data [Office development in Visual Studio], document-level solutions
- document-level customizations [Office development in Visual Studio], data model
ms.assetid: 84808462-2c5d-4dc8-ab69-491d492b4a51
caps.latest.revision: "27"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f90aeb03dd62d76064124e9870a5a4dbcd250621
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="cached-data-in-document-level-customizations"></a>文档级自定义项中的缓存数据
  文档级自定义项的主要目标是将数据从 Office 文档中的视图。 数据是指存储在文档中，包括数字和文本的信息。 视图是指用户界面和 Microsoft Office Word 和 Microsoft Office Excel 的对象模型。  
  
 Visual Studio 将数据从文档级自定义项中的视图分离通过启用要作为嵌入数据*数据岛*，也称为*数据缓存*。 您可以读取或修改直接而无需启动 Word 或 Excel 的数据。 当你需要在没有安装 Microsoft Office 的服务器上的文档中修改数据时，这非常有用。 Word 和 Excel 专门用于客户端环境;它们不被设计服务器上运行。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 有关文档级自定义项的详细信息，请参阅[Office 解决方案开发概述 &#40;VSTO &#41;](../vsto/office-solutions-development-overview-vsto.md)和[的文档级自定义项的体系结构](../vsto/architecture-of-document-level-customizations.md)。  
  
## <a name="understanding-the-cached-data-programming-model"></a>了解缓存的数据编程模型  
 数据岛可以包含满足某些要求的解决方案中的任何对象。 这些对象包括<xref:System.Data.DataSet>对象，<xref:System.Data.DataTable>对象，并可以通过序列化的任何其他对象<xref:System.Xml.Serialization.XmlSerializer>类。 有关详细信息，请参阅[缓存数据](../vsto/caching-data.md)。  
  
 若要提供缓存的数据的视图，你可以将绑定 Windows 窗体控件和*宿主控件*上到数据岛中的对象的文档。 数据岛和数据绑定控件之间的数据绑定将保持同步的两个。 你还可以将验证代码添加到独立于控件的数据。 有关详细信息，请参阅[将数据绑定到 Office 解决方案中的控件](../vsto/binding-data-to-controls-in-office-solutions.md)。  
  
 主机控件进行了扩展的 Excel 和 Word 对象模型中的本机对象的版本。 与本机对象中，主机控件可以绑定直接到托管的数据对象。 有关详细信息，请参阅 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md) 和 [Windows Forms Controls on Office Documents Overview](../vsto/windows-forms-controls-on-office-documents-overview.md)。  
  
## <a name="accessing-cached-data-on-the-server"></a>访问服务器上的缓存的数据  
 若要访问文档中缓存的数据，你可以使用<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>类。 此类属于[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]，且不能用在未正在运行的 Excel 或 Word 的服务器上。 当用户打开文档后修改的缓存的数据，任何控件绑定到数据将自动同步到所做的更改，并且用户会看到更新后的数据。 有关详细信息，请参阅 [Accessing Data in Documents on the Server](../vsto/accessing-data-in-documents-on-the-server.md)。  
  
 Excel 和 Word 不需要在服务器上，仅需查看客户端上将写入到数据。 Excel 和 Word 不甚至需要服务器上安装。 这提供改进的可伸缩性和执行包含数据岛的文档的快速的批处理操作的能力。  
  
## <a name="data-caching-for-offline-use"></a>缓存数据以便脱机使用  
 通过将数据存储在数据岛，脱机方案。 当用户首次打开文档，或者请求来自服务器的文档时，用最新的数据填充数据岛。 数据岛缓存到文档中，然后可以脱机。 用户 （和你的代码） 可以处理的数据，，即使实时连接不可用。 当用户重新连接时，对数据的更改可以传播回服务器数据源中。  
  
## <a name="cached-data-and-custom-xml-parts-compared"></a>缓存的数据和比较的自定义 XML 部件  
 作为一种方式在文档中存储的 XML 的任意段 2007 Microsoft Office system 中引入了自定义 XML 部件。 虽然自定义 XML 部件中作为数据缓存的同一方案的许多有用，但有一些差异的数据岛和自定义 XML 部件。 有关自定义 XML 部件的详细信息，请参阅[自定义 XML 部件概述](../vsto/custom-xml-parts-overview.md)。  
  
 下表列出的一些差异和相似之处。  
  
||数据缓存|自定义 XML 部件|  
|-|----------------|----------------------|  
|Office 应用程序可以使用它们？|以下应用程序的的文档级自定义：<br /><br /> Excel<br />单词|以下应用程序的的文档级和应用程序的级解决方案：<br /><br /> Excel<br />-PowerPoint<br />单词|  
|您可以存储的数据类型？|在满足某些要求你自定义项程序集中任何公共对象。 有关更多信息，请参见 [Caching Data](../vsto/caching-data.md)。|任何 XML 数据。|  
|是否可以访问数据而无需启动 Microsoft Office 应用程序？|是，通过使用<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>提供类[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]。|是，通过使用中的类<xref:System.IO.Packaging>命名空间，或通过使用 Open XML 格式 SDK。|  
  
## <a name="see-also"></a>另请参阅  
 [Office 解决方案中的数据](../vsto/data-in-office-solutions.md)   
 [Visual Studio 中 Office 解决方案的体系结构](../vsto/architecture-of-office-solutions-in-visual-studio.md)  
  
  