---
title: "使用 VSPackage 自定义 Visual Studio 的演练 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VSPackage"
  - "教程"
  - "自定义 Visual Studio"
  - "VS IDE"
  - "Visual Studio IDE"
ms.assetid: 7d10e376-74de-4402-9c10-ee9c9aa33c98
caps.latest.revision: 17
caps.handback.revision: 17
manager: "douge"
---
# 使用 VSPackage 自定义 Visual Studio 的演练
可通过创建 VSPackage 来扩展 Visual Studio。 这些是组成 Visual Studio 本身的软件模块。 工具窗口、编辑器、服务和项目类型均为 VSPackage。 Visual Studio SDK 可以让你创建自己的 Vspackage。  
  
 本节中的演练讲解如何创建 VSPackage、为其提供功能、将其集成到 Visual Studio 中，并将其分发给其他用户。 有关 VSPackage 及其功能的详细信息，请参阅 [在 Visual Studio SDK](../extensibility/internals/inside-the-visual-studio-sdk.md)。  
  
## 本节内容  
 [使用菜单命令创建扩展](../extensibility/creating-an-extension-with-a-menu-command.md)  
 演示如何创建用于将命令添加到 Visual Studio 中的菜单的 VSPackage，以及如何向命令添加键盘快捷方式。 并演示如何将有关包的信息添加到“关于”对话框和 Visual Studio 的初始屏幕中。  
  
 [添加一个工具窗口](../extensibility/adding-a-tool-window.md)  
 演示如何在 Visual Studio 中创建工具窗口，随后如何将控件嵌入其中，以及如何将命令栏添加到其中。 此外，还演示如何注册位置在 Visual Studio 中的工具窗口。  
  
 [扩展属性、 任务列表、 输出和选项 Windows](../extensibility/extending-the-properties-task-list-output-and-options-windows.md)  
 演示如何生成基本任务管理器，以便用户可以将任务添加到 Visual Studio 的“任务列表”和“输出”窗口中。 可以在 Visual Studio 的“属性”窗口中编辑添加的任务。 并演示如何将页面添加到“选项”对话框。  
  
## 相关章节  
 [Visual Studio 介绍](../Topic/Introducing%20the%20Visual%20Studio%20SDK.md)  
 概述 Visual Studio SDK 所包含的功能和工具，以及如何使用它们来扩展 Visual Studio。  
  
 [在 Visual Studio SDK](../extensibility/internals/inside-the-visual-studio-sdk.md)  
 描述如何自定义 Visual Studio IDE 的不同元素。