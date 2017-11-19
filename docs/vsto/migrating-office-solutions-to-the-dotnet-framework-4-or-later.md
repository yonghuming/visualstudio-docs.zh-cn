---
title: "将 Office 解决方案迁移到.NET Framework 4 或更高版本 |Microsoft 文档"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VST.Project.TargetFrameworkWarning
dev_langs:
- VB
- CSharp
helpviewer_keywords: Office projects [Office development in Visual Studio], migrating to .NET Framework 4
ms.assetid: 31f6c48b-c086-4362-8629-f644d6083a44
caps.latest.revision: "55"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c47c99f8d9a907d86461098f1f569fdbcac8841c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="migrating-office-solutions-to-the-net-framework-4-or-later"></a>将 Office 解决方案迁移到 .NET Framework 4 或更高版本
  如果将 Office 项目的目标框架从 .NET Framework 的早期版本更改为 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或更高版本，则可能需要执行一些其他步骤才能继续运行开发计算机和最终用户计算机上的解决方案。 有关详细信息，请参阅[迁移到.NET Framework 4 或.NET Framework 4.5 的 Office 运行项目所需的更改](../vsto/required-changes-to-run-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)。  
  
 此外，可能无法再编译该项目。 对于不同版本的 .NET Framework，Office 项目的一些功能具有不同的编程模型。 当 Office 项目的目标框架从 .NET Framework 的早期版本更改为 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或更高版本时，必须对项目进行以下代码更改：  
  
-   [更新 Excel 和 Word 项目迁移到.NET Framework 4 或.NET Framework 4.5](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)  
  
-   [更新迁移到.NET Framework 4 或.NET Framework 4.5 的 Office 项目中的功能区自定义项](../vsto/updating-ribbon-customizations-in-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)  
  
-   [更新迁移到.NET Framework 4 或.NET Framework 4.5 的 Outlook 项目中的窗体区域](../vsto/updating-form-regions-in-outlook-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)  
  
 当从 Visual Studio 的早期版本升级该项目时，Office 项目的目标框架将更改。 有关详细信息，请参阅 [Upgrading and Migrating Office Solutions](../vsto/upgrading-and-migrating-office-solutions.md)。  
  
 有关原因的详细信息中的 Office 项目的某些功能具有不同的编程模型，当你面向[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]或更高版本，请参阅[设计的 Office 项目的.NET Framework 4 或.NET Framework 4.5目标更改](../vsto/changes-to-the-design-of-office-projects-that-target-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)和[Visual Studio Tools for Office Runtime 概述](../vsto/visual-studio-tools-for-office-runtime-overview.md)。  
  
## <a name="see-also"></a>另请参阅  
 [设计和创建 Office 解决方案](../vsto/designing-and-creating-office-solutions.md)   
 [如何：面向某个版本的 .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md)   
 [在 Office 解决方案中的错误故障排除](../vsto/troubleshooting-errors-in-office-solutions.md)   
 [Office 解决方案错误的其他支持](../vsto/additional-support-for-errors-in-office-solutions.md)  
  
  