---
title: "命令路由算法 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- commands, routing
- command routing
ms.assetid: 998b616b-bd08-45cb-845f-808efb8c33bc
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e85ad4c4027a27b33f2f96284df80f852ffe3b85
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="command-routing-algorithm"></a>命令路由算法
在 Visual Studio 中的许多不同组件的处理命令。 命令将从最内部的上下文，基于当前所选内容，路由到最外层的 （也称为全局） 上下文。 有关详细信息，请参阅[可用性](../../extensibility/internals/command-availability.md)。  
  
## <a name="order-of-command-resolution"></a>命令解析顺序  
 命令将通过以下命令上下文的级别：  
  
1.  外接程序： 环境首先提供了到任何的外接程序存在的命令。  
  
2.  优先级命令： 使用注册这些命令<xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterPriorityCommandTarget>。 它们为在 Visual Studio 中，每个命令调用，并且中已注册的顺序调用。  
  
3.  上下文菜单命令： 在上下文菜单上的命令首先提供给为典型的路由提供上下文菜单中，到之后, 对命令目标。  
  
4.  工具栏设置命令目标： 调用时注册这些命令目标<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell4.SetupToolbar2%2A>。 `pCmdTarget`参数可以为`null`。 如果不是`null`，则此命令目标将使用更新位于你要设置的工具栏上的任何命令。 如果 shell 设置您的工具栏上，则它将传递作为该窗口框架`pCmdTarget`以便流经窗口框架，你工具栏上的命令的所有更新都即使它不在焦点时。  
  
5.  工具窗口： 工具窗口，通常实现<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>接口，还应实现<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>接口，以便在工具窗口是活动窗口时，Visual Studio 可以获取命令目标。 但是，如果该工具窗口具有焦点是**项目**窗口中，则该命令路由到<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>接口即选定项的公共父级。 如果此选择跨多个项目，该命令路由到<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution>层次结构。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>接口包含<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A>和<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>类似于上的相应命令的方法<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>接口。  
  
6.  文档窗口： 如果该命令已在其.vsct 文件中设置的 RouteToDocs 标志，Visual Studio 会查找在文档视图对象，它可以是命令目标的实例<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>接口或文档对象的实例 (通常<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>接口或<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>接口)。 如果文档视图对象不支持该命令，Visual Studio 将路由到命令<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>返回的接口。 （这是用于文档数据对象的可选接口）。  
  
7.  当前层次结构： 当前层次结构可以是拥有活动文档窗口或层次结构中选定的项目**解决方案资源管理器**。 Visual Studio 将查找<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>在最新状态，或处于活动状态，层次结构中实现的接口。 层次结构应支持层次结构处于活动状态，即使项目项的文档窗口具有焦点时有效的命令。 但是，命令应用时，才**解决方案资源管理器**具有焦点必须通过使用支持<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>接口并将其<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A>和<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>方法。  
  
     **剪切**，**复制**，**粘贴**，**删除**，**重命名**，**输入**，和**DoubleClick**命令需要特殊处理。 有关如何处理**删除**和**删除**命令在层次结构中，请参阅<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDeleteHandler>接口。  
  
8.  全局： 如果尚未由前面所述的上下文处理命令，Visual Studio 尝试将它路由到拥有命令实现的 VSPackage<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>接口。 如果 VSPackage 未已加载，它时不会加载 Visual Studio 会调用<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>方法。 VSPackage 加载时，才<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A>调用方法。  
  
## <a name="see-also"></a>另请参阅  
 [命令设计](../../extensibility/internals/command-design.md)