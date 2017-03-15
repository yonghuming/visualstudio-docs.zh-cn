---
title: "命令、菜单和工具栏概述 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "菜单要点 [Visual Studio SDK]"
  - "工具栏要点 [Visual Studio SDK]"
ms.assetid: cbdaceaa-7dd3-4a56-aea6-b759e48d83d6
caps.latest.revision: 19
caps.handback.revision: 19
manager: "douge"
---
# 命令、菜单和工具栏概述
菜单和工具栏提供了一种方便的图形方法，供用户访问 VSPackage 中的命令。 命令是完成任务（如打印文档、刷新视图或创建新文件）的函数。 菜单和工具栏是用于向用户呈现命令的方便图形方式。 通常，相关命令在相同菜单或工具栏上聚集在一起。  
  
-   菜单通常在集成开发环境 \(IDE\) 或工具窗口顶部显示为聚集在一行中的一个单词字符串。 菜单还可以显示为右键单击事件的结果，称为该上下文中的快捷菜单。 单击时，菜单会展开以显示一个或多个命令。 命令在单击时可以执行的任务或启动包含其他命令的子菜单。 一些常见的菜单名包括文件、编辑、视图和窗口。 有关详细信息，请参阅[扩展的菜单和命令](../extensibility/extending-menus-and-commands.md)。  
  
-   工具栏通常是按钮和其他控件（如组合框、列表框、文本框和菜单控制器）组成的行。 所有工具栏控件都与命令关联。 单击工具栏按钮时，会激活其关联命令。 工具栏按钮通常具有提示基础命令的图标，如用于打印命令的打印机。 在下拉列表控件中，列表中的每项都与不同命令关联。 菜单控制器是一种混合体，其中控件的一端是工具栏按钮，另一端是在单击时显示其他命令的向下箭头。 有关详细信息，请参阅 [如何：创建用于工具窗口的工具栏](../misc/how-to-create-toolbars-for-tool-windows.md) 和 [将图标添加到菜单命令](../extensibility/adding-icons-to-menu-commands.md)。  
  
-   创建命令时，还必须为它创建事件处理程序。 事件处理程序确定命令何时可见或启用、使你可以修改其文本并确保命令在激活时以合适方式进行响应（“路由”）。 在大多数情况下，IDE 使用 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 接口处理命令。[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中的命令以分层方式进行路由，基于本地选择从最内层命令上下文开始，然后基于全局选择继续执行到最外层上下文。 添加到主菜单的命令可立即用于脚本编写。 有关详细信息，请参阅[MenuCommands 与 OleMenuCommands](../misc/menucommands-vs-olemenucommands.md)和[选择上下文对象](../extensibility/internals/selection-context-objects.md)。  
  
 要定义新菜单和工具栏，必须在 Visual Studio 命令表 \(.vsct\) 文件中对它们进行描述。 Visual Studio 包模板会为你创建此文件，以及支持你在模板中选择的任何命令、工具栏和编辑器所需的元素。 此外，可以使用此处所述的 xml 架构编写自己的 .vsct 文件：[VSCT XML 架构参考](../extensibility/vsct-xml-schema-reference.md)。  
  
 有关使用 .vsct 文件的详细信息，请参见 [Visual Studio 命令表 \(。Vsct\) 文件](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)，或尝试任何[针对用户界面元素的演练](../misc/walkthroughs-for-user-interface-elements.md)。  
  
 有关菜单和工具栏的更详细概述，请参见[命令设计](../extensibility/internals/command-design.md)。  
  
## 请参阅  
 [扩展的菜单和命令](../extensibility/extending-menus-and-commands.md)   
 [命令、 菜单和工具栏](../extensibility/internals/commands-menus-and-toolbars.md)   
 [Vspackage](../extensibility/internals/vspackages.md)