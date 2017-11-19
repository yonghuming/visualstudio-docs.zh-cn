---
title: "通过使用互操作程序集确定命令状态 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- interop assemblies, determining command status
- command handling with interop assemblies, status
ms.assetid: 2f5104d1-7b4c-4ca0-a626-50530a8f7f5c
caps.latest.revision: "18"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3cde6ae841271622e0d538d679991288c111095e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="determining-command-status-by-using-interop-assemblies"></a>通过使用互操作程序集确定命令状态
VSPackage 必须跟踪的它可以处理的命令的状态。 在你的 VSPackage 内处理的命令将成为启用或禁用时，无法确定环境。 它负责你的 VSPackage 以通知有关命令状态的环境，例如，常规的状态的命令如**剪切**，**复制**，和**粘贴**。  
  
## <a name="status-notification-sources"></a>状态通知源  
 环境接收有关通过 Vspackage 的命令的信息<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>方法，即 VSPackage 的实现的一部分的<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>接口。 环境调用<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>下两个条件的 vspackage 的方法：  
  
-   当用户打开主菜单或上下文菜单 （通过右键单击） 时，环境都将执行<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>该菜单上的命令，以确定其状态的所有方法。  
  
-   当 VSPackage 请求环境更新当前的用户界面 (UI)。 作为命令的当前用户可见的如将发生这种情况**剪切**，**复制**，和**粘贴**标准工具栏上分组、 变为启用和禁用中响应上下文和用户操作。  
  
 由于命令行程序承载多个 Vspackage，shell 的性能如果它需要轮询每个 VSPackage 来确定命令状态将会令人无法接受降低。 相反，你的 VSPackage 应主动环境时通知其 UI 更改在更改的时间。 更新通知的详细信息，请参阅[更新用户界面](../../extensibility/updating-the-user-interface.md)。  
  
## <a name="status-notification-failure"></a>状态通知失败  
 你的 VSPackage 的失败通知命令状态更改的环境可以将 UI 放置处于不一致状态。 请记住，任何菜单或上下文菜单命令可以放置工具栏上的用户。 因此，仅当将打开一个菜单或上下文菜单时才更新 UI 是不够的。  
  
## <a name="see-also"></a>另请参阅  
 [Vspackage 如何添加用户界面元素](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [实现](../../extensibility/internals/command-implementation.md)