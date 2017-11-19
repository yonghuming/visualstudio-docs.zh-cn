---
title: "更改为面向.NET Framework 4 或.NET Framework 4.5 的 Office 项目的设计 |Microsoft 文档"
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
- Office development in Visual Studio, what's new
- what's new [Office development in Visual Studio]
ms.assetid: 290f5cb4-e2ee-4ed8-987c-2f013405cee9
caps.latest.revision: "36"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: dbf93e29e9bde2029bfff262a953d5858f17d084
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="changes-to-the-design-of-office-projects-that-target-the-net-framework-4-or-the-net-framework-45"></a>面向 .NET Framework 4 或 .NET Framework 4.5 的 Office 项目设计的更改
  从 [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)]开始，Visual Studio 引入了对面向 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或更高版本的 Office 项目设计的一些更改。 如果你熟悉以前的 Visual Studio 版本中的 Office 项目，那么在开发面向 .NET Framework 4.0 或更高版本的 Office 项目之前，应了解这些更改。 默认情况下，使用 Visual Studio 2013 或更高版本创建的所有项目都面向 .NET Framework 4.0 或更高版本。  
  
 以下各节描述这些 Office 项目设计更改。  
  
## <a name="understanding-the-interface-based-design-of-the-visual-studio-2010-tools-for-office-runtime"></a>了解 Visual Studio 2010 Tools for Office Runtime 的基于接口的设计  
 开发面向 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或更高版本的 Office 项目时，在 Visual Studio 2010 Tools for Office Runtime 中使用的大多数类型都是接口。 这是对以前版本的 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]的一个重要更改，在以前的版本中这些类型是类。 例如，如果面向的是 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或更高版本，则 <xref:Microsoft.Office.Tools.Excel.Worksheet> 和 <xref:Microsoft.Office.Tools.Word.Document> 类型是接口而不是类。 有关详细信息，请参阅 [Visual Studio Tools for Office Runtime Overview](../vsto/visual-studio-tools-for-office-runtime-overview.md)。  
  
 你无法直接在以前版本的实例化任何类型[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]，现在使用 Globals.Factory 对象的方法来获取这些类型的实例。 例如，若要获取实现的对象<xref:Microsoft.Office.Tools.Excel.SmartTag>接口，请使用 Globals.Factory.CreateSmartTag 方法。 有关详细信息，请参阅下列主题：  
  
-   [更新 Excel 和 Word 项目迁移到.NET Framework 4 或.NET Framework 4.5](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)  
  
-   [更新迁移到.NET Framework 4 或.NET Framework 4.5 的 Office 项目中的功能区自定义项](../vsto/updating-ribbon-customizations-in-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)  
  
-   [更新迁移到.NET Framework 4 或.NET Framework 4.5 的 Outlook 项目中的窗体区域](../vsto/updating-form-regions-in-outlook-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)  
  
### <a name="new-base-classes-in-office-projects"></a>Office 项目中的新基类  
 Visual Studio 2010 Tools for Office Runtime 的基于接口的新设计会影响 Office 项目中生成的类，如 `ThisDocument`、 `ThisWorkbook`和 `ThisAddIn`。 在面向.NET Framework 3.5 和以前版本的 framework 的 Office 项目，这些生成的类派生自中类[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]Microsoft.Office.Tools.Word.Document，Microsoft.Office.Tools.Excel.Worksheet，例如和Microsoft.Office.Tools.AddIn。 在面向 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或更高版本的项目中，这些 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 类现在为接口。 因此，Office 项目中生成的类不再从这些类派生其实现。 相反，生成的类派生自诸如 <xref:Microsoft.Office.Tools.Word.DocumentBase>、 <xref:Microsoft.Office.Tools.Excel.WorksheetBase>和 <xref:Microsoft.Office.Tools.AddInBase>等新基类。 有关详细信息，请参阅 [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md) 和 [Programming Document-Level Customizations](../vsto/programming-document-level-customizations.md)。  
  
 基类不属于 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 可再发行组件。 相反，基类在 Visual Studio 附带的实用工具程序集中进行定义。 这些程序集在生成 Office 项目时复制到输出文件夹，并且必须随解决方案一起部署。 有关实用工具程序集的详细信息，请参阅 [Assemblies in the Visual Studio Tools for Office Runtime](../vsto/assemblies-in-the-visual-studio-tools-for-office-runtime.md)。  
  
## <a name="breaking-changes-in-office-projects-that-are-retargeted-to-the-net-framework-4"></a>重定向到 .NET Framework 4 的 Office 项目中的重大更改  
 下表列出了在重定向到 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或更高版本的 Office 项目中可能会遇到的主要重大更改。 有关更多详细信息，请参阅 [Migrating Office Solutions to the .NET Framework 4 or later](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)。  
  
|重大更改|结果|  
|---------------------|-----------------|  
|Office 项目中不再使用或支持 <xref:System.Security.SecurityTransparentAttribute> 。|必须从更新自 Visual Studio 2008 的 Office 项目的 AssemblyInfo 代码文件中删除此属性。 有关详细信息，请参阅[迁移到.NET Framework 4 或.NET Framework 4.5 的 Office 运行项目所需的更改](../vsto/required-changes-to-run-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)。|  
|ExcelLocale1033Attribute 不再使用或在 Excel 项目中受支持。|必须从 Excel 项目中的 AssemblyInfo 代码文件中删除此属性。 有关详细信息，请参阅[更新 Excel 和 Word 项目迁移到.NET Framework 4 或.NET Framework 4.5](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)。|  
|**“功能区（可视化设计器）”** 项目项的编程模型已更改。|必须修改项目中任何功能区项的代码隐藏文件。 还必须修改在运行时实例化功能区控件、处理功能区事件或以编程方式设置功能区组件位置的任何代码。 有关详细信息，请参阅[办公室中更新功能区自定义项目迁移到.NET Framework 4 或.NET Framework 4.5](../vsto/updating-ribbon-customizations-in-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)。|  
|Outlook 窗体区域的编程模型已更改。|必须修改项目中任何窗体区域的代码隐藏文件，以及在运行时实例化某些窗体区域类的任何代码。 有关详细信息，请参阅[更新在 Outlook 中的窗体区域项目迁移到.NET Framework 4 或.NET Framework 4.5](../vsto/updating-form-regions-in-outlook-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)。|  
|Excel 和 Word 项目中的智能标记的编程模型已更改。 在 [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)] 和 [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)]中弃用了智能标记。|如果你的解决方案使用智能标记，则生成项目时将发生错误。 由于 [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)] 和 [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)]中已弃用智能标记，因此，在 [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] 或更高版本中，必须先删除这些标记才能测试和调试解决方案。|  
|GetVstoObject 和 HasVstoObject 方法的语法已更改|必须在从主互操作程序集 (Pia) 的本机对象上访问这些或可以访问由你的项目中的 Globals.Factory 属性返回的对象上的这些方法时的 Globals.Factory 对象传递给这些方法。 有关详细信息，请参阅[更新 Excel 和 Word 项目迁移到.NET Framework 4 或.NET Framework 4.5](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)。|  
|Word 内容控件的事件与新委托相关联。|必须将处理 Word 内容控件的事件的任何代码修改为指定新委托。 有关详细信息，请参阅[更新 Excel 和 Word 项目迁移到.NET Framework 4 或.NET Framework 4.5](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)。|  
|OLEObject 和 OLEControl 类已重命名。|必须将使用这些类的实例的任何代码改为使用 <xref:Microsoft.Office.Tools.Excel.ControlSite> 或 <xref:Microsoft.Office.Tools.Word.ControlSite> 对象。 有关详细信息，请参阅[更新 Excel 和 Word 项目迁移到.NET Framework 4 或.NET Framework 4.5](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)。|  
|主机项类，如`ThisWorkbook`， `Sheet`  *n* ， `ThisDocument`，和`ThisAddIn`，不再提供可以重写的 Dispose 方法。|你必须将移动任何代码中的 Dispose 方法重写到关闭事件处理程序在主机项类中，例如， `ThisAddIn_Shutdown`，并从主机项类删除 Dispose 方法重写。|  
  
## <a name="see-also"></a>另请参阅  
 [Migrating Office Solutions to the .NET Framework 4 or later](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)   
 [什么是中的 Office 开发的新增功能](http://msdn.microsoft.com/en-us/bf054af2-c896-4723-aa15-6381145b14bb)   
 [Visual Studio Tools for Office 运行时概述](../vsto/visual-studio-tools-for-office-runtime-overview.md)  
  
  