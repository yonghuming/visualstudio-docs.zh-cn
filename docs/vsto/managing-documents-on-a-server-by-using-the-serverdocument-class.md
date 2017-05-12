---
title: "使用 ServerDocument 类管理服务器上的文档"
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
  - "文档 [Visual Studio 中的 Office 开发], 在服务器上管理"
  - "Office 文档 [Visual Studio 中的 Office 开发, 在服务器上管理"
  - "ServerDocument 类, 在服务器上管理文档"
ms.assetid: 1ac90e89-d07d-4874-9d24-6741d6679a21
caps.latest.revision: 40
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 39
---
# 使用 ServerDocument 类管理服务器上的文档
  即使未安装 Microsoft Office Word 和 Microsoft Office Excel，您也可以使用 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]中的 ServerDocument 类管理文档级自定义项的多个方面。  您可以执行以下任务：  
  
-   访问和修改文档或工作簿的数据缓存中的数据。  有关更多信息，请参见[处理文档中的缓存数据](#CachedData)。  
  
-   管理与文档相关联的自定义项程序集。  有关更多信息，请参见[管理文档自定义项](#CustomizationInfo)。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## 了解 ServerDocument 类  
 ServerDocument 类设计为在未安装 Office 的计算机上使用。  因此，您通常在未与 Office 集成的应用程序（如控制台项目或 Windows 窗体项目）中使用此类，而不会在 Office 项目中使用。  使用 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> 选件类在 Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll 程序集。  
  
 ServerDocument 选件类可用于对使用 [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)]，创建的文档级自定义项。  
  
 有关以下内容的详细信息 for Office runtime 的 Office 扩展和的 Visual Studio 2010 工具 .NET Framework 的，请参见 [Visual Studio Tools for Office Runtime 概述](../vsto/visual-studio-tools-for-office-runtime-overview.md)。  
  
> [!NOTE]  
>  如果在使用 ServerDocument 选件类 Visual Studio Tools for Office system 的传统应用程序 \(3.0 版运行时\)，Visual Studio Tools for Office system \(3.0 版运行时\) 在运行应用程序的计算机必须安装。  for Office runtime 的 Visual Studio 2010 工具无法运行这些应用程序。  
  
##  <a name="CachedData"></a> 处理文档中的缓存数据  
 ServerDocument 类提供可用于处理自定义文档中的数据缓存的成员。  有关缓存数据的更多信息，请参见[缓存数据](../vsto/caching-data.md)和[访问服务器上的文档数据](../vsto/accessing-data-in-documents-on-the-server.md)。  
  
 下表列出了可用于处理缓存数据的成员。  
  
|任务|使用的成员|  
|--------|-----------|  
|确定文档中是否具有数据缓存。|<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.IsCacheEnabled%2A> 方法。|  
|访问文档中的缓存数据。<br /><br /> 有关详细信息，请参阅 [访问服务器上的文档数据](../vsto/accessing-data-in-documents-on-the-server.md)。|<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> 属性。|  
  
##  <a name="CustomizationInfo"></a> 管理文档自定义项  
 您可以使用 ServerDocument 类的成员管理与文档相关联的自定义项程序集。  例如，您可以通过编程方式移除文档中的自定义项，使文档不再是自定义项的一部分。  
  
 下表列出了可用于管理自定义项程序集的成员。  
  
|任务|使用的成员|  
|--------|-----------|  
|确定文档是否是文档级自定义项的一部分。|<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.GetCustomizationVersion%2A> 方法。|  
|在运行时以编程方式将自定义项附加到文档。<br /><br /> 有关更多信息，请参阅[如何：将托管代码扩展附加到文档](../vsto/how-to-attach-managed-code-extensions-to-documents.md)。|<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> 方法之一。|  
|在运行时以编程方式从文档中移除一个自定义项。<br /><br /> 有关详细信息，请参阅 [如何：移除文档中的托管代码扩展](../vsto/how-to-remove-managed-code-extensions-from-documents.md)。|<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.RemoveCustomization%2A> 方法。|  
|获取与文档关联的部署清单的 URL。|<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.DeploymentManifestUrl%2A> 属性。|  
  
## 请参阅  
 [如何：将托管代码扩展附加到文档](../vsto/how-to-attach-managed-code-extensions-to-documents.md)   
 [如何：移除文档中的托管代码扩展](../vsto/how-to-remove-managed-code-extensions-from-documents.md)   
 [Visual Studio Tools for Office Runtime 概述](../vsto/visual-studio-tools-for-office-runtime-overview.md)   
 [缓存数据](../vsto/caching-data.md)  
  
  