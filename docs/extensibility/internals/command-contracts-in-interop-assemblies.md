---
title: "在互操作程序集的命令协定 | Microsoft Docs"
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
  - "处理用于互操作程序集，命令约定的命令"
  - "互操作程序集，命令协定"
ms.assetid: 57245708-f539-42dc-8963-2754a48f0189
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# 在互操作程序集的命令协定
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

处理命令传递的基本协定 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 接口是环境调用 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> 方法若要确定是否支持该命令，如果它受支持，以确定其状态和文本。 然后，环境调用 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> 方法来执行命令。  
  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> 方法所有命令的处理方式相同。 进一步通信，如果需要 \(例如，使用下拉列表\)，由调用 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> 使用适当的参数的方法。 这些参数的解释取决于指定的命令。  
  
 如果命令目标的输出参数中返回值，调用方负责始终释放所有已分配的资源。 由于此参数是一个变量，清除变体释放的资源。  
  
 在命令必须位置内的层次结构窗口中，进行操作的情况下 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> 必须使用接口。<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> 接口有一个具有类似的方法类似协定: <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> 和 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>。  
  
## 请参阅  
 [Vspackage 如何添加用户界面元素](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Vspackage 中的命令传送](../../extensibility/internals/command-routing-in-vspackages.md)   
 [实现](../../extensibility/internals/command-implementation.md)