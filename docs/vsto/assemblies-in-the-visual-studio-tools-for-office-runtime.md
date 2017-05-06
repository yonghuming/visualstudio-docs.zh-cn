---
title: "Visual Studio Tools for Office Runtime 中的程序集"
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
  - "Visual Studio Tools for Office Runtime，程序集"
ms.assetid: d2b7f8f4-0f41-4943-bca5-48c520748b7e
caps.latest.revision: 29
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 28
---
# Visual Studio Tools for Office Runtime 中的程序集
  在创建新的 Office 项目时，Visual Studio 会自动添加对项目类型和项目的目标 .NET Framework 使用的 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 程序集的引用。 在 .NET Framework 3.5、[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 和 [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] 的 Office 扩展中存在不同的程序集。 有关 Office 扩展的详细信息，请参阅 [Visual Studio Tools for Office Runtime 概述](../vsto/visual-studio-tools-for-office-runtime-overview.md)。  
  
## .NET Framework 4 和 [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] 的 Office 扩展中的程序集  
 下表列出了包含在 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 和 [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] 的 Office 扩展中的程序集。 有关这些程序集中的命名空间和类型的文档，请参阅 [托管参考（Visual Studio 中的 Office 开发）](../vsto/managed-reference-office-development-in-visual-studio.md)。  
  
|程序集名称|描述|  
|-----------|--------|  
|Microsoft.Office.Tools.Common.dll|提供以下类型：<br /><br /> -   用于创建功能区自定义和智能标记的类型。 **Note:**      在 [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)] 和 [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)] 中弃用了智能标记。<br />-   用于在文档级自定义项中创建操作窗格以及在 VSTO 外接程序中创建自定义任务窗格的类型。|  
|Microsoft.Office.Tools.Excel.dll|提供表示 Excel 项目的主机项和主机控件以及支持类型的接口。 有关详细信息，请参阅[使用扩展对象实现 Excel 自动化](../vsto/automating-excel-by-using-extended-objects.md)。|  
|Microsoft.Office.Tools.Outlook.dll|提供可用于在 Outlook VSTO 外接程序中创建自定义窗体区域的类型。|  
|Microsoft.Office.Tools.Word.dll|提供表示 Word 项目的主机项和主机控件及支持类型的接口。 有关详细信息，请参阅[使用扩展对象实现 Word 自动化](../vsto/automating-word-by-using-extended-objects.md)。|  
|Microsoft.Office.Tools.v4.0.Framework.dll|提供以下类型：<br /><br /> -   由 Visual Studio Tools for Office Runtime 引发的异常。<br />-   创建 Outlook 窗体区域时可使用的特性。|  
|Microsoft.Office.Tools.dll|提供作为 Visual Studio Tools for Office Runtime 基础结构一部分，并且不应在代码中直接使用的类型。|  
|Microsoft.VisualStudio.Tools.Applications.Runtime.dll|提供以下类型：<br /><br /> -   <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> 特性和 <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType> 接口，可用于在文档级自定义项中缓存数据对象。 有关更多信息，请参见[缓存数据](../vsto/caching-data.md)。<br />-   <xref:Microsoft.VisualStudio.Tools.Applications.Deployment.IAddInPostDeploymentAction> 接口，可实现该接口以将其他安装步骤作为 Office 解决方案的 ClickOnce 安装程序的最后一步进行运行。 有关详细信息，请参阅[使用 ClickOnce 部署 Office 解决方案](../vsto/deploying-an-office-solution-by-using-clickonce.md)。<br />-   由 Visual Studio Tools for Office Runtime 引发的异常。<br />-   其他类型，是 Visual Studio Tools for Office runtime 基础结构一部分，并且不应在代码中直接使用。|  
|Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll|提供以下类型：<br /><br /> -   <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> 类，可使用此类将自定义程序集附加到文档并访问文档中缓存的数据。 有关详细信息，请参阅[使用 ServerDocument 类管理服务器上的文档](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)。<br />-   多个类，它们表示文档级自定义项中已缓存数据的层次结构。 有关详细信息，请参阅[访问服务器上的文档数据](../vsto/accessing-data-in-documents-on-the-server.md)。|  
  
 以 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或 [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] 为目标的项目还引用以下程序集。 这些程序集不属于 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 可再发行组件。 相反，它们是必须与解决方案一起部署的依赖程序集。 默认情况下，它们复制到项目的生成输出文件夹（这些程序集的**“本地属性”**属性设置为**“True”**）。 如果使用 ClickOnce 部署项目，这些程序集包含在生成的包中。  
  
|程序集名称|描述|  
|-----------|--------|  
|Microsoft.Office.Tools.Common.v4.0.Utilities.dll|提供 VSTO 外接程序项目中生成的 `ThisAddIn` 类和所有项目中生成的功能区类的基类。|  
|Microsoft.Office.Tools.Excel.v4.0.Utilities.dll|提供以下类型：<br /><br /> -   Excel 的文档级项目中生成的 `ThisWorkbook` 和 `Sheet` 类的基类。<br />-   可在 Excel 项目的工作表中使用的 Windows 窗体控件。|  
|Microsoft.Office.Tools.Outlook.v4.0.Utilities.dll|提供 Outlook 项目中生成的 `ThisAddIn` 和窗体区域类的基类。|  
|Microsoft.Office.Tools.Word.v4.0.Utilities.dll|提供以下类型：<br /><br /> -   Word 的文档级项目中生成的 `ThisDocument` 类的基类。<br />-   可在 Word 项目的文档中使用的 Windows 窗体控件。|  
  
## .NET Framework 3.5 的 Office 扩展中的程序集  
 下表列出了包含在 .NET Framework 3.5 的 Office 扩展中的程序集。 有关这些程序集中的命名空间和类的文档，请参阅 Visual Studio 2008 文档中的以下参考部分：[http:\/\/go.microsoft.com\/fwlink\/?LinkId\=160658](http://go.microsoft.com/fwlink/?LinkId=160658)。  
  
|程序集名称|描述|  
|-----------|--------|  
|Microsoft.Office.Tools.Common.v9.0.dll|提供以下类型：<br /><br /> -   VSTO 外接程序的 Microsoft.Office.Tools.AddIn 基类。<br />-   用于创建功能区自定义和智能标记的类。 **Note:**      在 [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)] 和 [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)] 中弃用了智能标记。<br />-   用于在文档级自定义项中创建操作窗格及在 VSTO 外接程序中创建自定义任务窗格的类。|  
|Microsoft.Office.Tools.Excel.v9.0.dll|提供 Excel 解决方案的主机项和主机控件。 有关详细信息，请参阅[使用扩展对象实现 Excel 自动化](../vsto/automating-excel-by-using-extended-objects.md)。|  
|Microsoft.Office.Tools.Outlook.v9.0.dll|提供可用于在 Outlook VSTO 外接程序中创建自定义窗体区域的类。|  
|Microsoft.Office.Tools.Word.v9.0.dll|提供 Word 解决方案的主机项和主机控件。 有关更多信息，请参见[使用扩展对象实现 Word 自动化](../vsto/automating-word-by-using-extended-objects.md)。|  
|Microsoft.Office.Tools.v9.0.dll|提供以下类型：<br /><br /> -   Microsoft.VisualStudio.Tools.Office.RemoteBindableComponent 类，该类提供文档级自定义项中的主机控件的数据绑定功能。<br />-   其他类型，是 Visual Studio Tools for Office runtime 基础结构一部分，并且不应在代码中直接使用。|  
|Microsoft.VisualStudio.Tools.Applications.Runtime.v9.0.dll|提供以下类型：<br /><br /> -   Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute 特性和 Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType 接口，可用于在文档级自定义项中缓存数据对象。 有关详细信息，请参阅[缓存数据](../vsto/caching-data.md)。<br />-   由 Visual Studio Tools for Office Runtime 引发的异常。<br />-   其他类型，是 Visual Studio Tools for Office runtime 基础结构一部分，并且不应在代码中直接使用。|  
|Microsoft.VisualStudio.Tools.Applications.Runtime.v10.0.dll|提供 Microsoft.VisualStudio.Tools.Applications.Deployment.IAddInPostDeploymentAction 接口，可实现该接口以将其他安装步骤作为 Office 解决方案的 ClickOnce 安装程序的最后一步进行运行。 有关详细信息，请参阅[高级 Office 解决方案部署](http://msdn.microsoft.com/zh-cn/9147b6f6-849f-4cb1-b2c5-e22658d74b02)。|  
|Microsoft.VisualStudio.Tools.Applications.ServerDocument.v10.0.dll|提供以下类型：<br /><br /> -   Microsoft.VisualStudio.Tools.Applications.ServerDocument 类，可以编程方式使用此类将自定义程序集附加到文档并访问文档中缓存的数据。 有关详细信息，请参阅[使用 ServerDocument 类管理服务器上的文档](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)。<br />-   多个类，它们表示文档级自定义项中已缓存数据的层次结构。 有关详细信息，请参阅[访问服务器上的文档数据](../vsto/accessing-data-in-documents-on-the-server.md)。|  
|Microsoft.VisualStudio.Tools.Office.Runtime.v10.0.dll|提供以下类型：<br /><br /> -   Microsoft.VisualStudio.Tools.Office.Runtime.Security.AddInSecurityEntry 和 Microsoft.VisualStudio.Tools.Office.Runtime.Security.UserInclusionList 类，可用来创建用户包含列表条目，以向面向 .NET Framework 3.5 的 Office 解决方案授予信任。<br />-   其他类型，是 Visual Studio Tools for Office Runtime 基础结构一部分，并且不应在代码中直接使用。|  
  
## 请参阅  
 [Visual Studio Tools for Office Runtime 概述](../vsto/visual-studio-tools-for-office-runtime-overview.md)   
 [Visual Studio Tools for Office Runtime 安装方案](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md)  
  
  