---
title: "针对用户界面元素的演练 | Microsoft Docs"
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
  - "演练 [Visual Studio SDK], 菜单和工具栏"
  - "工具栏 [Visual Studio], 演练"
  - "菜单 [Visual Studio SDK], 演练"
ms.assetid: 4cf2486a-fd73-48ac-ac76-5bd7233d5d95
caps.latest.revision: 15
caps.handback.revision: 15
manager: "douge"
---
# 针对用户界面元素的演练
可以将菜单和工具栏添加到 VSPackage 或 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 集成的开发环境 \(IDE\) 的许多不同用户界面 \(UI\) 元素中。 此部分中的演练将引导你完成最常见的方案。  
  
## 本节内容  
 [添加到 Visual Studio 菜单栏的菜单](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)  
 演示如何将菜单从 VSPackage 添加到与 IDE 顶级菜单项（如“文件”、“编辑”、“帮助”）相同的级别中。  
  
 [将子菜单添加到菜单](../extensibility/adding-a-submenu-to-a-menu.md)  
 演示如何将子菜单添加到现有菜单。  
  
 [添加大多数最近使用过的子菜单上的列表](../extensibility/adding-a-most-recently-used-list-to-a-submenu.md)  
 演示如何支持身为“最近使用的项\(MRU\)”菜单基础的子菜单中的动态菜单列表。  
  
 [将工具栏添加](../extensibility/adding-a-toolbar.md)  
 演示如何将工具栏添加到 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE。  
  
 [将工具栏添加到工具窗口](../extensibility/adding-a-toolbar-to-a-tool-window.md)  
 演示如何将工具栏添加到工具窗口。  
  
 [将菜单控制器添加到工具栏](../extensibility/adding-a-menu-controller-to-a-toolbar.md)  
 演示如何将菜单控制器添加到工具栏。 菜单控制器是包含默认命令和箭头的按钮，用于显示可从中选择其他命令的下拉列表菜单列表。  
  
 [动态添加菜单项](../extensibility/dynamically-adding-menu-items.md)  
 演示如何动态添加菜单项。  
  
 [在工具窗口中添加快捷菜单](../extensibility/adding-a-shortcut-menu-in-a-tool-window.md)  
 演示如何向工具窗口添加上下文（即鼠标右键单击时显示的）菜单。 在本例中即渐变服务工具窗口。  
  
## 相关章节  
 [Visual Studio 命令表 \(。Vsct\) 文件](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)  
 介绍如何为项目准备 Visual Studio 命令表。  
  
 [使用 VSPackage 自定义 Visual Studio 的演练](../misc/walkthroughs-for-customizing-visual-studio-by-using-vspackages.md)  
 关于向 Visual Studio 添加 UI 元素的介绍性演练。  
  
 [命令、 菜单和工具栏](../extensibility/internals/commands-menus-and-toolbars.md)  
 说明如何创建包含菜单、工具栏和命令组合框的 UI。