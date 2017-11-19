---
title: "命令和使用互操作程序集的菜单 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- menus, using interop assemblies
- interop assemblies, using in commands and menus
- commands, handling using interop assemblies
- command handling with interop assemblies
ms.assetid: 8f4af525-39e5-4e69-92c8-d3efabe80bb2
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ee9fa1faa52afb2ea6d8154b4767fcab2cee0981
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="commands-and-menus-that-use-interop-assemblies"></a>命令和使用互操作程序集的菜单
实现菜单和工具栏命令的方法是使用互操作程序集的 VSPackage 必须：  
  
-   通知[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]有关所支持的命令和是否它们当前已启用的集成的开发环境 (IDE)。  
  
-   遵守的规则 （合同条款） 处理的命令。  
  
-   显式实现通过使用的命令处理<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>或<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>接口。  
  
 下面描述如何执行这些任务。  
  
## <a name="in-this-section"></a>本节内容  
 [使用互操作程序集确定命令状态](../../extensibility/internals/determining-command-status-by-using-interop-assemblies.md)  
 介绍 VSPackage 通知 IDE 的方式有关哪些命令中，它将支持并将它们当前是否启用。  
  
 [互操作程序集中的命令协定](../../extensibility/internals/command-contracts-in-interop-assemblies.md)  
 提供了使用所有 Vspackage 实现命令使用互操作程序集的基本命令协定的定义  
  
 [实现](../../extensibility/internals/command-implementation.md)  
 概述如何 VSPackage 实现命令。  
  
 [注册互操作程序集命令处理程序](../../extensibility/internals/registering-interop-assembly-command-handlers.md)  
 描述通知 IDE VSPackage 提供命令处理程序所需的注册表项。  
  
## <a name="related-sections"></a>相关章节  
 [可用性](../../extensibility/internals/command-availability.md)  
 描述了 IDE 用于确定有哪些 VSPackage 命令和哪些对象处理它们的条件。  
  
 [VSPackage 如何添加用户界面元素](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)  
 提供有关如何创建使用 UI 的详细信息[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]命令支持。  
  
 [VSPackage 中的命令传送](../../extensibility/internals/command-routing-in-vspackages.md)  
 用于相关具有正确的命令和请求的对象的过程概述。