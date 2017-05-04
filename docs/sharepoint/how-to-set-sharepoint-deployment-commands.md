---
title: "如何：设置 SharePoint 部署命令 | Microsoft Docs"
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
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Visual Studio 中的 SharePoint 开发, 部署"
ms.assetid: 289c8c33-a603-434e-889f-a0d0a1736ecb
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# 如何：设置 SharePoint 部署命令
  可以通过设置预先部署命令和后期部署命令来自定义部署过程。  在从 Visual Studio 调试 SharePoint 解决方案时，这些命令会在其他部署操作前后运行。  
  
### 添加预先部署命令  
  
1.  在菜单栏上，依次选择**“项目\(Project\)”**、*ProjectName* **属性\(Properties\)**.  
  
2.  选择**“SharePoint”**选项卡。  
  
3.  在**“前期部署命令行”**文本框中，键入 MS\-DOS 或 MSBuild 命令以自定义此步骤。  
  
     例如，若要在部署完成之前列出目录内容，请键入 **dir**。  
  
### 添加后期部署命令  
  
1.  在菜单栏上，依次选择**“项目\(Project\)”**、*ProjectName* **属性\(Properties\)**.  
  
2.  选择**“SharePoint”**选项卡。  
  
3.  在**“后期部署命令行”**文本框中，键入 MS\-DOS 或 MSBuild 命令以自定义此步骤。  
  
     例如，若要在部署完成之后列出目录内容，请键入 **dir**。  若要使用 MSBuild 变量从生成目录复制程序集，请键入 **copy $\(TargetPath\) c:\\DeploymentDirectory**。  
  
## 请参阅  
 [打包和部署 SharePoint 解决方案](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  