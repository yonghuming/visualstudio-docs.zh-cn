---
title: "Visual Studio Shell | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "外壳程序中，Visual Studio"
  - "Visual Studio 中 shell"
ms.assetid: cb124ef4-1a6b-4bfe-bfbf-295ef9c07f36
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# Visual Studio Shell
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 外壳程序是在集成的主代理 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 外壳中提供了必要的功能以启用 VSPackages 共享公共服务。 因为的体系结构目标 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 在 Vspackage，背心的主要功能是外壳是一个框架，用于提供基本功能和支持 VSPackages 迁移其组件之间的跨通信。  
  
## 命令行程序责任  
 外壳程序具有以下主要职责︰  
  
-   支持 （通过 COM 接口） 的用户界面 \(UI\) 的基本元素。 其中包括默认菜单和工具栏、 文档窗口框架或多文档界面 \(MDI\) 子窗口和工具窗口框架，以及提供停靠支持。  
  
-   来协调持久性的文档，并保证在多个方面，或以不兼容的方式，无法打开该文档时，维护所有当前打开的文档中正在运行的 document 表 \(RDT\) 的运行列表。  
  
-   支持的命令路由和命令处理的接口， `IOleCommandTarget`。  
  
-   在适当时候加载 Vspackage。 延迟加载 VSPackage 是为了提高性能的命令行界面。  
  
-   管理某些共享服务，如 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>, ，该属性提供基本外壳程序功能和 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>, ，它提供基本的窗口化功能。  
  
-   管理解决方案 \(.sln\) 文件。 解决方案中包含相关项目，类似于在 Visual c \+ \+ 6.0 的工作区 \(.dsw\) 文件的组。  
  
-   跟踪外壳程序范围内所选内容、 上下文和货币。 外壳中跟踪以下类型的项︰  
  
    -   当前项目  
  
    -   当前项目项或 ItemID 当前 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>  
  
    -   为当前所选内容 **属性** 窗口或 `SelectionContainer`  
  
    -   UI 上下文 Id 或控制的可见性命令、 菜单和工具栏的 CmdUIGuids  
  
    -   当前处于活动状态的元素，如活动窗口、 文档和撤消管理器  
  
    -   用户上下文属性动态帮助该驱动器  
  
 命令行界面也担当中介 VSPackages 迁移已安装和当前服务之间的通信。 它支持外壳中的核心功能，并使数据库可用于所有 Vspackage 中集成了 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 这些核心功能包括以下各项︰  
  
-   **有关** 对话框框和初始屏幕  
  
-   **新添和添加现有项** 对话框  
  
-   **类视图** 窗口和 **对象浏览器**  
  
-   **引用** 对话框  
  
-   **文档大纲** 窗口  
  
-   **动态帮助** 窗口  
  
-   **查找** 和 **替换**  
  
-   **打开项目** 和 **打开的文件** 对话框上 **新建** 菜单  
  
-   **选项** 对话框在 **工具** 菜单  
  
-   **属性** 窗口  
  
-   **解决方案资源管理器**  
  
-   **任务列表** 窗口  
  
-   **工具箱**  
  
## 请参阅  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>   
 [Vspackage](../../extensibility/internals/vspackages.md)