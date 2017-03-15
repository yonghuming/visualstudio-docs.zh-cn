---
title: "扩展的菜单和命令 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "菜单、 常见任务"
  - "Vspackage，菜单任务"
  - ".vsct 文件中，菜单上的常见任务"
ms.assetid: 7b2be4b9-e3fe-4412-874f-ae72ebc84c4b
caps.latest.revision: 49
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 49
---
# 扩展的菜单和命令
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

命令是将操作和进程添加到 Visual Studio 的方式。 在大多数情况下会在菜单或工具栏上显示命令。 VSPackage 项目模板演示如何实现一个非常基本的命令。 一种稍长，但仍基本实现，请参阅 [使用菜单命令创建扩展](../extensibility/creating-an-extension-with-a-menu-command.md)。  
  
 关于 Visual Studio 命令、 菜单和工具栏的详细信息，请参阅 [命令、 菜单和工具栏](../extensibility/internals/commands-menus-and-toolbars.md)。  
  
 是 VSPackage 项目的一部分.vsct 文件中定义命令、 菜单和工具栏。 您可以找到有关 Visual Studio IDE 和.vsct 文件中的信息 [Vspackage 如何添加用户界面元素](../extensibility/internals/how-vspackages-add-user-interface-elements.md)。  
  
 以下主题介绍如何添加不同类型的命令、 菜单和工具栏。  
  
## 本节内容  
 [添加到 Visual Studio 菜单栏的菜单](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)  
 说明如何将菜单添加到 Visual Studio 菜单栏的顶部。  
  
 [绑定的键盘快捷方式菜单项](../extensibility/binding-keyboard-shortcuts-to-menu-items.md)  
 说明如何将键盘快捷方式 \(如 CTRL \+ 3\) 添加到菜单项。  
  
 [将子菜单添加到菜单](../extensibility/adding-a-submenu-to-a-menu.md)  
 说明如何将子菜单添加到顶部的菜单。  
  
 [添加大多数最近使用过的子菜单上的列表](../extensibility/adding-a-most-recently-used-list-to-a-submenu.md)  
 说明如何添加最近使用过的列表。  
  
 [创建可重用的按钮的组](../extensibility/creating-reusable-groups-of-buttons.md)  
 介绍如何命令的项目进行分组，以便它们可以包含多个菜单上。  
  
 [将图标添加到菜单命令](../extensibility/adding-icons-to-menu-commands.md)  
 描述如何将图标添加到上一个工具栏和菜单命令。  
  
 [更改菜单命令的文本](../extensibility/changing-the-text-of-a-menu-command.md)  
 介绍如何使用 `TextChanges` 标志，用于启用菜单项，从而动态更改。  
  
 [更改命令的外观](../extensibility/changing-the-appearance-of-a-command.md)  
 介绍如何动态启用或禁用的命令。  
  
 [更新用户界面](../extensibility/updating-the-user-interface.md)  
 介绍如何强制执行更新用户界面以反映最新更改。  
  
 [本地化的菜单命令](../extensibility/localizing-menu-commands.md)  
 说明如何进行本地化菜单命令。  
  
## 相关章节