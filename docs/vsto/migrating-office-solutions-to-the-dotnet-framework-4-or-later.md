---
title: "将 Office 解决方案迁移到 .NET Framework 4 或更高版本 | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VST.Project.TargetFrameworkWarning"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Office 项目 [Visual Studio 中的 Office 开发]，迁移到 .NET Framework 4"
ms.assetid: 31f6c48b-c086-4362-8629-f644d6083a44
caps.latest.revision: 55
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 54
---
# 将 Office 解决方案迁移到 .NET Framework 4 或更高版本
  如果将 Office 项目的目标框架从 .NET Framework 的早期版本更改为 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或更高版本，则可能需要执行一些其他步骤才能继续运行开发计算机和最终用户计算机上的解决方案。 有关详细信息，请参阅[运行迁移到 .NET Framework 4 或 .NET Framework 4.5 的 Office 项目所需的更改](../vsto/required-changes-to-run-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)。  
  
 此外，可能无法再编译该项目。 对于不同版本的 .NET Framework，Office 项目的一些功能具有不同的编程模型。 当 Office 项目的目标框架从 .NET Framework 的早期版本更改为 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或更高版本时，必须对项目进行以下代码更改：  
  
-   [更新您迁移到 .NET Framework 4 或 .NET Framework 4.5 的 Excel 和 Word 项目](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)  
  
-   [更新迁移到 .NET Framework 4 或 .NET Framework 4.5 的 Office 项目中的功能区自定义项](../vsto/updating-ribbon-customizations-in-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)  
  
-   [更新迁移到 .NET Framework 4 或 .NET Framework 4.5 的 Outlook 项目中的窗体区域](../vsto/updating-form-regions-in-outlook-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)  
  
 当从 Visual Studio 的早期版本升级该项目时，Office 项目的目标框架将更改。 有关更多信息，请参见[升级和迁移 Office 解决方案](../vsto/upgrading-and-migrating-office-solutions.md)。  
  
 当你的目标为 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或更高版本时，Office 项目中的一些功能会有不同的编程模型，有关这种情况的原因的详细信息，请参阅[面向 .NET Framework 4 或 .NET Framework 4.5 的 Office 项目设计的更改](../vsto/changes-to-the-design-of-office-projects-that-target-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)和 [Visual Studio Tools for Office Runtime 概述](../vsto/visual-studio-tools-for-office-runtime-overview.md)。  
  
## 请参阅  
 [设计和创建 Office 解决方案](../vsto/designing-and-creating-office-solutions.md)   
 [如何：面向 .NET Framework 的某个版本](~/ide/how-to-target-a-version-of-the-dotnet-framework.md)   
 [Office 解决方案中错误的疑难解答](../vsto/troubleshooting-errors-in-office-solutions.md)   
 [Office 解决方案错误的其他支持](../vsto/additional-support-for-errors-in-office-solutions.md)  
  
  