---
title: "扩展和自定义工具窗口 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- user interfaces, essentials
- tool windows, standard
ms.assetid: 46b2892e-7b2b-4b3f-83a7-b884f1e114ee
caps.latest.revision: "20"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6488df3ec567051709f6464d49d891cdd8f995dd
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="extending-and-customizing-tool-windows"></a>扩展和自定义工具窗口
Visual Studio 提供了多种不同类型的 windows，例如工具窗口、 文档窗口和对话框窗口。 如属性窗口、 输出窗口和任务列表窗口中，其他 windows 是工具窗口的类型。  
  
## <a name="tool-windows"></a>工具窗口  
 Visual Studio 工具窗口是不基于文件的通常是只读的窗口。 在这方面，它们不同于文档窗口，文档窗口在读写模式下显示文件。 工具窗口的示例包括“工具箱” 、“解决方案资源管理器” 、“属性”  窗口和“Web 浏览器”  。  
  
 若要了解如何创建一个简单工具窗口，请参阅[添加工具窗口](../extensibility/adding-a-tool-window.md)。  
  
 若要注册 Visual Studio 工具窗口，请参阅[注册工具窗口](../extensibility/registering-a-tool-window.md)。  
  
 工具窗口默认情况下是单实例，这意味着一次只能打开一个工具窗口的实例。 打开单实例工具窗口后，它保持打开状态直到关闭 IDE。 当关闭单实例工具窗口时，仅其可见性更改。 你还可以创建多实例工具窗口，以便可以同时打开窗口中的多个实例。 请参阅[创建多实例工具窗口](../extensibility/creating-a-multi-instance-tool-window.md)有关详细信息。  
  
 工具窗口可以*动态*，这意味着它们都可见只要应用其相关的 UI 上下文。 使用自动可见性可以减少 IDE 中的窗口的混乱。 有关详细信息，请参阅[打开动态工具窗口](../extensibility/opening-a-dynamic-tool-window.md)。  
  
 工具窗口可以在文档框架中停靠、浮动或呈选项卡式。 工具窗口框架由 IDE 提供，用于控制大小、位置、停靠状态和其他持久性属性。 工具窗口窗格用于显示内容。 仅当首次打开工具窗口时才应用默认大小和位置；在此之后将保留工具窗口状态。  
  
 工具窗口窗格可以承载 WPF 用户控件，并支持工具栏。 您可以重写<xref:Microsoft.VisualStudio.Shell.WindowPane.Window%2A>属性以返回所承载的控件的句柄。  
  
 可以将许多不同的功能添加到工具窗口。 例如，你可以添加一个工具栏：[将工具栏添加到工具窗口](../extensibility/adding-a-toolbar-to-a-tool-window.md)或快捷菜单：[工具窗口中添加快捷菜单](../extensibility/adding-a-shortcut-menu-in-a-tool-window.md)。 你可以添加搜索控件，您可以搜索工具窗口内的项：[添加到工具窗口的搜索](../extensibility/adding-search-to-a-tool-window.md)。  
  
 你可以订阅工具窗口事件：[璹綷事件](../extensibility/subscribing-to-an-event.md)。  
  
## <a name="extending-existing-tool-windows"></a>扩展现有的工具窗口  
 可以将信息有关工具窗口添加到新**选项**页和上的新设置**属性**页上，将写入到**任务列表**和**输出** windows。 有关详细信息，请参阅[扩展属性、 任务列表、 输出和选项 Windows](../extensibility/extending-the-properties-task-list-output-and-options-windows.md)和[扩展属性、 任务列表、 输出和选项 Windows](../extensibility/extending-the-properties-task-list-output-and-options-windows.md)。  
  
## <a name="modal-dialog-boxes"></a>有模式对话框  
 在 Visual Studio 扩展中应创建模式对话框，通过从它们派生<xref:Microsoft.VisualStudio.PlatformUI.DialogWindow?displayProperty=fullName>，这样，您可以控制它们和用户界面的其余部分。 有关详细信息，请参阅。 [创建和管理有模式对话框](../extensibility/creating-and-managing-modal-dialog-boxes.md)。  
  
## <a name="see-also"></a>另请参阅  
 [使用工具窗口创建扩展](../extensibility/creating-an-extension-with-a-tool-window.md)