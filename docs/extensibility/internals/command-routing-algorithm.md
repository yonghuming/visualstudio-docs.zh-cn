---
title: "命令路由算法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "路由的命令"
  - "命令传送"
ms.assetid: 998b616b-bd08-45cb-845f-808efb8c33bc
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# 命令路由算法
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

在 Visual Studio 命令的处理由大量不同的组件。 命令将从最内部的上下文，基于当前所选内容路由到最外层的 （也称为全局） 上下文。 有关更多信息，请参见[可用性](../../extensibility/internals/command-availability.md)。  
  
## 命令解析顺序  
 命令将通过以下级别的命令行上下文︰  
  
1.  外接程序︰ 环境首先提供了到任何加载项中所出现的命令。  
  
2.  优先级命令︰ 这些命令使用注册的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterPriorityCommandTarget>。 它们为 Visual Studio 中的每个命令调用，并且在已注册的顺序中调用。  
  
3.  上下文菜单命令︰ 在上下文菜单上的命令首先提供给与典型的路由提供上下文菜单中，到之后, 的命令目标。  
  
4.  工具栏上设置命令目标︰ 调用时注册这些命令目标 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell4.SetupToolbar2%2A>。`pCmdTarget` 参数可以为 `null`。 如果不是 `null`, ，则此命令目标中，用于更新位于你要设置的工具栏上的任何命令。 如果外壳中设置您的工具栏，则将它传递作为该窗口框架 `pCmdTarget` ，以便对通过该窗口框架，您工具栏上的流中的命令的所有更新都即使它不在时焦点。  
  
5.  工具窗口︰ 工具窗口，通常情况下实现 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> 接口，还应实现 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 接口，因此，在工具窗口是活动窗口时，Visual Studio 可以获取命令目标。 但是，如果工具窗口具有焦点将 **项目** 窗口中，则该命令将被路由到 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> 是常见的选定项的父级的接口。 如果选择此选项跨多个项目，该命令路由到 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution> 层次结构。<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> 接口包含 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> 和 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A> 类似于上的相应命令的方法 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 接口。  
  
6.  文档窗口中︰ 如果该命令有其.vsct 文件中设置了 RouteToDocs 标志，Visual Studio 会查找对文档视图的对象可以是命令目标的一个实例 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> 接口或文档对象的实例 \(通常 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> 接口或 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> 接口\)。 如果文档视图对象不支持该命令，Visual Studio 将传递到命令 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 返回的接口。 （这是文档的数据对象的可选接口）。  
  
7.  当前层次结构︰ 当前层次结构可以是拥有活动文档窗口或层次结构中所选的项目 **解决方案资源管理器**。 Visual Studio 查找 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 在最新状态，或处于活动状态，层次结构实现的接口。 层次结构应支持层次结构中处于活动状态，即使项目项的文档窗口具有焦点时有效的命令。 但是，命令的可以应用时，才 **解决方案资源管理器** 具有焦点必须通过使用支持 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> 接口并将其 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> 和 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>方法。  
  
     **剪切**, ，**副本**, ，**粘贴**, ，**删除**, ，**重命名**, ，**Enter**, ，和 **DoubleClick** 命令需要进行特殊处理。 有关如何处理 **删除** 和 **删除** 命令在层次结构中，请参阅 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDeleteHandler> 接口。  
  
8.  Global︰ 如果命令未处理由前面提到的上下文中，Visual Studio 将尝试将其路由到拥有一个可实现的命令的 VSPackage <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 接口。 如果尚未已加载 VSPackage，它不会加载时 Visual Studio 会调用 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> 方法。 仅当加载 VSPackage <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> 调用方法。  
  
## 请参阅  
 [命令设计](../../extensibility/internals/command-design.md)