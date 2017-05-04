---
title: "运行迁移到 .NET Framework 4 或 .NET Framework 4.5 的 Office 项目所需的更改 | Microsoft Docs"
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
  - "Office 项目 [Visual Studio 中的 Office 开发], 迁移到 .NET Framework 4"
ms.assetid: e2cd35cc-7731-428e-9046-34fc57a02c48
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# 运行迁移到 .NET Framework 4 或 .NET Framework 4.5 的 Office 项目所需的更改
  如果将 Office 项目的目标框架更改为 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或更高版本（来自 .NET Framework 的早期版本），则必须执行以下任务以确保在开发计算机和最终用户计算机上，可以运行该解决方案：  
  
-   删除项目中的 <xref:System.Security.SecurityTransparentAttribute>如果从 Visual Studio 2008 升级它）。  
  
-   在 Visual Studio 中执行 **Clean** 命令从而运行或调试开发计算机上的项目。  
  
-   更新项目的 .NET Framework 必备组件。  
  
-   如果以前通过在更改目标框架之前使用 ClickOnce 部署解决方案，则最终用户还必须重新安装该解决方案。  
  
 有关上述每个任务的详细信息，请参阅以下相应章节。  
  
## 删除从 Visual Studio 2008 升级的项目中的 SecurityTransparent 属性  
 如果从 Visual Studio 2008 升级 Office project 项目，且项目的目标框架随后更改为 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或更高版本，则必须从项目中删除 <xref:System.Security.SecurityTransparentAttribute>。 Visual Studio 不会为你自动删除此属性。 如果不删除此属性，则编译项目时将收到一条错误消息。  
  
 有关 Visual Studio 可以将已升级项目的目标框架更改到 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或 [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] 的条件的详细信息，请参阅[升级和迁移 Office 解决方案](../vsto/upgrading-and-migrating-office-solutions.md)。  
  
#### 若要删除 SecurityTransparentAttribute  
  
1.  在 Visual Studio 中打开项目后，打开**“解决方案资源管理器”**。  
  
2.  在 C\# 的**“属性”**节点或在 Visual Basic 的**“我的项目”**节点下，双击 AssemblyInfo 代码文件以在代码编辑器中打开它。  
  
    > [!NOTE]  
    >  在 Visual Basic 项目中，必须单击**“解决方案资源管理器”**中的**“显示所有文件”**按钮，才能查看 AssemblyInfo 代码文件。  
  
3.  找到 <xref:System.Security.SecurityTransparentAttribute> 并且将其从文件中删除或注释掉。  
  
    ```vb  
    <Assembly: SecurityTransparent()>  
    ```  
  
    ```csharp  
    [assembly: SecurityTransparent()]  
    ```  
  
## 执行清理命令以便在开发计算机上调试或运行项目  
 如果 Office 项目是在该项目的目标框架更改为 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或更高版本之前生成的，则必须执行**“清理”**命令，然后在更改目标框架后重新生成项目。  如果不执行**“清理”**命令，当尝试调试或运行重定位目标的项目时，将收到 <xref:System.Runtime.InteropServices.COMException>。  
  
 有关**“清理”**命令的详细信息，请参阅 [生成 Office 解决方案](../vsto/building-office-solutions.md)。  
  
## 更新部署的必备组件  
 当重新定位 Office 项目到 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或更高版本时，还必须更新**“必备组件”**对话框中相应的 .NET Framework 必备组件。  否则，ClickOnce 部署或 InstallShield Limited Edition 项目将检查并安装 .NET Framework 的早期版本。  
  
 有关更新最终用户计算机部署必备组件的详细信息，请参阅[如何：在最终用户计算机上安装系统必备组件以便运行 Office 解决方案](http://msdn.microsoft.com/zh-cn/74dd2c52-838f-4abf-b2b4-4d7b0c2a0a98)。  
  
## 在最终用户计算机上重新安装解决方案  
 如果使用 ClickOnce 部署面向 .NET Framework 3.5 的 Office 解决方案，然后将项目重新定位到 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或更高版本，则最终用户必须卸载解决方案，然后在发布解决方案后进行重新安装。  如果重新发布重定目标的解决方案，并且最终用户计算机上已更新该解决方案，则最终用户在运行已更新解决方案时将收到 <xref:System.Runtime.InteropServices.COMException>。  
  
## 请参阅  
 [将 Office 解决方案迁移到 .NET Framework 4 或更高版本](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)  
  
  