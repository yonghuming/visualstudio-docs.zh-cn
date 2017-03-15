---
title: "命令、 菜单和工具栏 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "菜单 [Visual Studio SDK] 命令"
  - "命令 [Visual Studio]"
  - "工具栏 [Visual Studio] 命令"
ms.assetid: 07b4ed90-dbbd-40df-b6c9-8395fd6f2ab6
caps.latest.revision: 60
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 60
---
# 命令、 菜单和工具栏
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

菜单和工具栏是用户的方式访问你的 VSPackage 中的命令。 命令是完成任务，如打印文档、 刷新视图，或创建一个新的文件的函数。 菜单和工具栏是方便图形方式向用户呈现您的命令。 通常情况下，相关的命令聚集在一起的同一个菜单或工具栏上。  
  
-   菜单通常显示为一个单词聚集在集成的开发环境 \(IDE\) 或工具窗口的顶部行中的字符串。 菜单还可以显示一个用鼠标右键单击事件，因此，称为该上下文中的快捷菜单。 单击时，菜单将展开以显示一个或多个命令。 命令，请单击时，可以执行的任务，也可以启动包含其他命令的子菜单。 一些人所熟知的菜单名是文件、 编辑、 视图和窗口。 有关更多信息，请参见[扩展的菜单和命令](../../extensibility/extending-menus-and-commands.md)。  
  
-   工具栏通常是按钮和其他控件，如组合框、 列表框、 文本框、 文本框和菜单控制器的行。 工具栏上的所有控件都都与命令关联。 当您单击工具栏按钮时，将激活其关联的命令。 工具栏按钮通常具有建议的基础的命令，如打印命令的打印机的图标。 在下拉列表控件中，列表中的每个项都与不同的命令关联。 菜单控制器是其中一方的控件是一个工具栏按钮，另一端是显示其他命令时单击向下箭头的混合体。 有关详细信息，请参阅[将菜单控制器添加到工具栏](../../extensibility/adding-a-menu-controller-to-a-toolbar.md)。  
  
-   当您创建一个命令时，您还必须创建一个事件处理程序为其。 事件处理程序确定该命令时是可见的还是已启用，使您可以修改它的文本，并确保该命令做出相应的响应 \("路由"\) 时激活。 在大多数情况下，IDE 将处理命令使用 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 接口。 中的命令 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 路由以分层方式，从最内层命令上下文中，基于本地的选择，并且继续到最外层的上下文，基于全局的选择。 立即提供用于脚本编写了一些命令添加到主菜单。 有关详细信息，请参阅[MenuCommands 与 OleMenuCommands](../../misc/menucommands-vs-olemenucommands.md)和[选择上下文对象](../../extensibility/internals/selection-context-objects.md)。  
  
 若要定义新的菜单和工具栏，必须在 Visual Studio 命令表 \(.vsct\) 文件中对它们进行描述。 Visual Studio 包模板创建此文件，以及必需的元素以支持任何命令、 工具栏和模板中选定的编辑器。 此外，您可以编写您自己的.vsct 文件，使用此处所述的 xml 架构: [VSCT XML 架构参考](../../extensibility/vsct-xml-schema-reference.md)。  
  
 有关使用.vsct 文件的详细信息，请参阅 [Visual Studio 命令表 \(。Vsct\) 文件](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)。  
  
 本部分中的主题说明在 Vspackage 中如何工作的命令、 菜单和工具栏。  
  
## 本节内容  
 [Vspackage 如何添加用户界面元素](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)  
 命令表的格式规范详细说明。  
  
 [Visual Studio 命令表 \(。Vsct\) 文件](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)  
 描述基于 XML 的语法和编译器的命令表。  
  
 [默认的命令、 组和工具栏位置](../../extensibility/internals/default-command-group-and-toolbar-placement.md)  
 描述预定义的命令、 组、 菜单和工具栏。  
  
 [IDE 定义的命令、 菜单和组](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)  
 指定预定义的菜单、 命令和命令组可供使用 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE。  
  
 [命令设计](../../extensibility/internals/command-design.md)  
 介绍如何设计命令。  
  
 [优化菜单和工具栏命令](../../extensibility/internals/optimizing-menu-and-toolbar-commands.md)  
 为命令提供了指导。  
  
 [提供命令](../../extensibility/internals/making-commands-available.md)  
 说明如何向 Visual Studio 提供的命令。  
  
 [命令和使用互操作程序集的菜单](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)  
 说明如何实现使用互操作程序集的命令。  
  
## 相关章节  
 [Vspackage 中的命令传送](../../extensibility/internals/command-routing-in-vspackages.md)  
 说明在 Vspackage 中路由命令。