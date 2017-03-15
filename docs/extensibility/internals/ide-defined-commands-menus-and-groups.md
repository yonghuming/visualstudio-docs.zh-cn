---
title: "IDE 定义的命令、 菜单和组 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "环境定义的命令"
  - ".vsct 文件，环境定义的常量"
  - "环境定义的命令组"
ms.assetid: 86b3af13-7163-48c6-986b-7beeedbc26cc
caps.latest.revision: 27
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 27
---
# IDE 定义的命令、 菜单和组
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

许多菜单、 命令和命令组已定义以供 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE。 在扩展时，可能也包括可供您使用这些命令 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
## 查找环境定义的命令  
 一套四个.vsct 文件中定义的环境的命令︰  
  
-   SharedCmdDef.vsct  
  
-   SharedCmdPlace.vsct  
  
-   ShellCmdDef.vsct  
  
-   ShellCmdPlace.vsct  
  
 这些文件位于 *\< Visual Studio SDK 安装路径 \>*\\VisualStudioIntegration\\Common\\Inc\\。 这些文件提供的定义和的菜单和组，您可以使用你的 VSPackage 的命令表配置 \(.vsct\) 文件中作为容器的您自己的菜单、 组和命令的 Guid。  
  
## 本节内容  
 [Guid 和 Id 的 Visual Studio 菜单](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)  
 提供的菜单栏上的 Visual Studio 菜单上，以及它们所包含的组的 GUID 和 ID 值。  
  
 [Guid 和 Id 的 Visual Studio 工具栏](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)  
 提供了在 Visual Studio IDE 中的工具栏和它们所包含的组的 GUID 和 ID 值。  
  
 [Guid 和 Id 的 Visual Studio 命令](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)  
 提供 Visual Studio IDE 所定义的命令的 GUID 和 ID 值。  
  
## 请参阅  
 [Visual Studio 命令表 \(。Vsct\) 文件](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [IDE 定义用于扩展项目系统的命令](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)   
 [Vspackage 如何添加用户界面元素](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)