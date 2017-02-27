---
title: "通过使用互操作程序集确定命令状态 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "互操作程序集，确定命令状态"
  - "处理用于互操作程序集，状态的命令"
ms.assetid: 2f5104d1-7b4c-4ca0-a626-50530a8f7f5c
caps.latest.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 18
---
# 通过使用互操作程序集确定命令状态
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

VSPackage 必须跟踪的它可以处理的命令的状态。 在你的 VSPackage 中处理的命令没有启用或禁用时，无法确定该环境。 它是你的 VSPackage 通知有关命令状态的环境的责任，例如，常规的状态命令如 **剪切**, ，**副本**, ，和 **粘贴**。  
  
## 状态通知源  
 环境接收有关命令传递 Vspackage <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> 方法，它是 VSPackage 的实现的一部分的 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 接口。 环境调用 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> 在两个条件下 VSPackage 的方法:  
  
-   当用户打开主菜单或上下文菜单 \(通过右键单击\) 时，将执行环境 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> 对所有使用该菜单上的命令，以确定其状态的方法。  
  
-   VSPackage 请求时，环境将更新当前的用户界面 \(UI\)。 作为命令的当前用户可见的如将发生这种情况 **剪切**, ，**副本**, ，和 **粘贴** 分组在标准工具栏上，成为启用和禁用对上下文和用户操作的响应中。  
  
 由于外壳中承载多个 Vspackage，shell 的会令人无法接受会降低性能如果它需要轮询每个 VSPackage 来确定命令状态。 相反，你的 VSPackage，应主动通知环境更改时更改其 UI 时。 更新通知的详细信息，请参阅 [更新用户界面](../../extensibility/updating-the-user-interface.md)。  
  
## 状态通知失败  
 你的 VSPackage 的失败通知命令状态已更改环境可以将 UI 放处于不一致状态。 请记住，任何菜单或上下文菜单命令可以放置在工具栏上的用户。 因此，仅当将打开一个菜单或上下文菜单时才更新 UI 是不够的。  
  
## 请参阅  
 [Vspackage 如何添加用户界面元素](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [实现](../../extensibility/internals/command-implementation.md)