---
title: "扩展工具窗口 | Microsoft Docs"
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
  - "窗口 [Visual Studio SDK], 工具"
  - "文档窗口"
  - "工具窗口"
  - "窗口 [Visual Studio SDK], 文档"
ms.assetid: 252f7b99-b44a-4a63-88d9-3a0ca48ac4f1
caps.latest.revision: 37
caps.handback.revision: 37
manager: "douge"
---
# 扩展工具窗口
一般情况下，Visual Studio 工具窗口是不基于文件的只读窗口。 在这方面，它们不同于文档窗口，文档窗口在读写模式下显示文件。 工具窗口的示例包括“工具箱”、“解决方案资源管理器”、“属性”窗口和“Web 浏览器”。  
  
 Visual Studio 2010 和更高版本中的所有工具窗口都是基于 WPF 的。 在 Visual Studio 2010 之前的 Visual Studio 版本中，工具窗口都是基于 Windows 窗体的。 仍可显示基于 Windows 窗体的窗口，但新工具窗口必须基于 WPF。  
  
## 工具窗口基本知识  
 若要提供工具窗口，必须向 Visual Studio 进行注册，并指定工具窗口的默认大小和位置。 有关详细信息，请参阅[在注册表中的工具窗口](../extensibility/tool-windows-in-the-registry.md)。  
  
 工具窗口通常可以通过单击菜单命令创建或打开。 若要以编程方式创建工具窗口，请参阅[以编程方式打开工具窗口](../misc/opening-a-tool-window-programmatically.md)。  
  
 工具窗口默认情况下是单实例，这意味着一次只能打开一个工具窗口的实例。 打开单实例工具窗口后，它保持打开状态直到关闭 IDE。 当你单击单实例工具窗口上的关闭按钮时，仅更改其可见性。 你还可以创建多实例工具窗口，以便可以同时打开窗口中的多个实例。 有关更多信息，请参见[创建多实例工具窗口](../extensibility/creating-a-multi-instance-tool-window.md)。  
  
 工具窗口可以在文档框架中停靠、浮动或呈选项卡式。 工具窗口框架由 IDE 提供，用于控制大小、位置、停靠状态和其他持久性属性。 工具窗口窗格用于显示内容。 仅当首次打开工具窗口时才应用默认大小和位置；在此之后将保留工具窗口状态。  
  
 工具窗口窗格可以承载 WPF 用户控件，并支持工具栏。 你可以重写 <xref:Microsoft.VisualStudio.Shell.WindowPane.Window%2A> 属性以返回所承载的控件的句柄。  
  
 工具窗口可以为*“动态”*（也称为*“自动可见”*）。 只要应用其相关的 UI 上下文，动态工具窗口就可见。 使用自动可见性可以减少 IDE 中的窗口的混乱。 有关更多信息，请参见[打开动态工具窗口](../extensibility/opening-a-dynamic-tool-window.md)。  
  
 Vspackage 不是创建工具窗口的唯一方法。 外接程序可以通过使用 Visual Studio 自动化模型创建工具窗口。 有关详细信息，请参阅[如何：创建和控制工具窗口](../Topic/How%20to:%20Create%20and%20Control%20Tool%20Windows.md)。  
  
## 请参阅  
 [Tool Windows](../misc/extending-tool-windows.md)   
 [文档窗口](../extensibility/internals/document-windows.md)   
 [添加到工具窗口搜索](../extensibility/adding-search-to-a-tool-window.md)