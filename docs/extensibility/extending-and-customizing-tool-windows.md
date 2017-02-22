---
title: "扩展和自定义工具窗口 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "essentials 的用户界面"
  - "工具窗口标准"
ms.assetid: 46b2892e-7b2b-4b3f-83a7-b884f1e114ee
caps.latest.revision: 20
caps.handback.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
---
# 扩展和自定义工具窗口
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Visual Studio 提供了多种不同类型的窗口，例如工具窗口、 文档窗口和对话框窗口。 如属性窗口、 输出窗口和任务列表窗口中，其他窗口处于类型的工具窗口。  
  
## 工具窗口  
 Visual Studio 工具窗口是不是基于文件的通常是只读的窗口。 在此它们不同于在读写模式下显示的文件的文档窗口。**工具箱**, ，**解决方案资源管理器**, ，**属性** 窗口中，和 **Web 浏览器** 是工具窗口的示例。  
  
 若要了解如何创建一个简单的工具窗口，请参阅 [添加一个工具窗口](../extensibility/adding-a-tool-window.md)。  
  
 若要注册与 Visual Studio 工具窗口，请参阅 [注册一个工具窗口](../extensibility/registering-a-tool-window.md)。  
  
 工具窗口是单实例默认情况下，这意味着只有一个实例的工具窗口中可以打开一次。 单实例工具窗口打开后，它保持打开状态直到关闭 IDE。 单实例工具窗口关闭时，只有其可见性更改。 您还可以创建多实例工具窗口，以便窗口中的多个实例可以同时打开。 有关更多信息，请参见[创建多实例工具窗口](../extensibility/creating-a-multi-instance-tool-window.md)。  
  
 工具窗口可以 *动态*, ，这意味着它们都可见时应用其相关的 UI 上下文。 使用自动可见性可以减少在 IDE 中的 windows 的混乱。 有关更多信息，请参见[打开动态工具窗口](../extensibility/opening-a-dynamic-tool-window.md)。  
  
 工具窗口可以停靠、 浮动状态，或选项卡式文档框架中。 工具窗口框架提供的 IDE，以及用于控制大小、 位置、 插接状态和其他持久性属性。 工具窗口窗格中显示的内容。 默认大小和位置应用仅当工具窗口首次打开;在此之后保留工具窗口状态。  
  
 工具窗口窗格可以承载 WPF 用户控件，并支持工具栏。 您可以重写 <xref:Microsoft.VisualStudio.Shell.WindowPane.Window%2A> 属性以返回所承载的控件的句柄。  
  
 可以将许多不同的功能添加到工具窗口。 例如，可以添加工具栏: [将工具栏添加到工具窗口](../extensibility/adding-a-toolbar-to-a-tool-window.md) 或快捷菜单: [在工具窗口中添加快捷菜单](../extensibility/adding-a-shortcut-menu-in-a-tool-window.md)。 您可以添加一个允许您搜索工具窗口内的项的搜索控件: [添加到工具窗口搜索](../extensibility/adding-search-to-a-tool-window.md)。  
  
 您可以订阅事件的工具窗口: [订阅事件](../extensibility/subscribing-to-an-event.md)。  
  
## 扩展现有的工具窗口  
 将信息关于工具窗口添加到一个新 **选项** 页和上的新设置 **属性** 页上，将写入到 **任务列表** 和 **输出** windows。 有关详细信息，请参阅 [扩展属性、 任务列表、 输出和选项 Windows](../extensibility/extending-the-properties-task-list-output-and-options-windows.md) 和 [扩展属性、 任务列表、 输出和选项 Windows](../extensibility/extending-the-properties-task-list-output-and-options-windows.md)。  
  
## 有模式对话框  
 在 Visual Studio 扩展中应创建模式对话框，通过从它们派生 <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow?displayProperty=fullName>, ，这样，您可以控制它们和 UI 的其余部分。 有关详细信息，请参阅。[创建和管理有模式对话框](../extensibility/creating-and-managing-modal-dialog-boxes.md)。  
  
## 请参阅  
 [使用一个工具窗口创建扩展](../extensibility/creating-an-extension-with-a-tool-window.md)