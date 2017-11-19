---
title: "使用 ServerDocument 类管理服务器上的文档 |Microsoft 文档"
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
- documents [Office development in Visual Studio], managing on server
- Office documents [Office development in Visual Studio, managing on server
- ServerDocument class, managing documents on server
ms.assetid: 1ac90e89-d07d-4874-9d24-6741d6679a21
caps.latest.revision: "40"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: bd24d18df965535ee1315ae7807ac23723dc51d2
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="managing-documents-on-a-server-by-using-the-serverdocument-class"></a>Managing Documents on a Server by Using the ServerDocument Class
  你可以使用 ServerDocument 类中的[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]管理几个方面的文档级自定义项，即使未安装 Microsoft Office Word 和 Microsoft Office Excel。 你可以执行以下任务：  
  
-   访问和修改文档或工作簿的数据缓存中的数据。 有关详细信息，请参阅[处理文档中的缓存数据](#CachedData)。  
  
-   管理与文档相关联的自定义项程序集。 有关详细信息，请参阅[管理文档自定义项](#CustomizationInfo)。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## <a name="understanding-the-serverdocument-class"></a>了解 ServerDocument 类  
 ServerDocument 类用于在没有安装 Office 的计算机上使用。 因此，你通常使用此类应用程序执行不会与集成 Office，如控制台项目或 Windows 窗体项目，而不是 Office 项目中。 使用<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll 程序集中的类。  
  
 可以使用 ServerDocument 类上使用已创建的文档级自定义项进行操作[!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)]。  
  
 有关详细信息 Visual Studio 2010 Tools for Office Runtime 和 Office 扩展的.NET framework，请参阅[Visual Studio Tools for Office Runtime 概述](../vsto/visual-studio-tools-for-office-runtime-overview.md)。  
  
> [!NOTE]  
>  如果你有 Office system 中使用 Visual Studio 工具使用 ServerDocument 类的旧版应用程序 (3.0 版运行时)，Visual Studio Tools for Office system (3.0 版运行时) 必须安装在运行该应用程序的计算机上。 Visual Studio 2010 Tools for Office 运行时无法运行这些应用程序。  
  
##  <a name="CachedData"></a>使用文档中的缓存数据  
 ServerDocument 类提供了可用于处理与数据缓存在自定义文档中的成员。 有关缓存数据的详细信息，请参阅[缓存数据](../vsto/caching-data.md)和[访问的服务器上的文档数据](../vsto/accessing-data-in-documents-on-the-server.md)。  
  
 下表列出可用于处理与缓存的数据的成员。  
  
|任务|供使用的成员|  
|----------|-------------------|  
|若要确定文档是否有数据缓存。|<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.IsCacheEnabled%2A> 方法。|  
|若要访问文档中缓存的数据。<br /><br /> 有关详细信息，请参阅 [Accessing Data in Documents on the Server](../vsto/accessing-data-in-documents-on-the-server.md)。|<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> 属性。|  
  
##  <a name="CustomizationInfo"></a>管理文档自定义项  
 ServerDocument 类的成员可用于管理与文档相关联的自定义项程序集。 例如，你可以以编程方式删除自定义项从文档使该文档不再是一部分的自定义项。  
  
 下表列出可用于管理自定义程序集的成员。  
  
|任务|供使用的成员|  
|----------|-------------------|  
|若要确定文档是否是在文档级自定义项的一部分。|<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.GetCustomizationVersion%2A> 方法。|  
|若要在运行时以编程方式附加到文档的自定义项。<br /><br /> 有关详细信息，请参阅[如何： 附加到文档托管代码扩展](../vsto/how-to-attach-managed-code-extensions-to-documents.md)|之一<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A>方法。|  
|若要在运行时以编程方式删除文档中的自定义项。<br /><br /> 有关详细信息，请参阅[如何： 从文档中删除托管代码扩展](../vsto/how-to-remove-managed-code-extensions-from-documents.md)。|<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.RemoveCustomization%2A> 方法。|  
|若要获取的部署清单的与文档相关联的 URL。|<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.DeploymentManifestUrl%2A> 属性。|  
  
## <a name="see-also"></a>另请参阅  
 [如何： 将托管的代码扩展附加到文档](../vsto/how-to-attach-managed-code-extensions-to-documents.md)   
 [如何： 从文档中删除托管的代码扩展](../vsto/how-to-remove-managed-code-extensions-from-documents.md)   
 [Visual Studio Tools for Office Runtime Overview](../vsto/visual-studio-tools-for-office-runtime-overview.md)   
 [缓存数据](../vsto/caching-data.md)  
  