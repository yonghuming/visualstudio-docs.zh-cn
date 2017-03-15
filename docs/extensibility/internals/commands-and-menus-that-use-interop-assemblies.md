---
title: "命令和使用互操作程序集的菜单 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- menus, using interop assemblies
- interop assemblies, using in commands and menus
- commands, handling using interop assemblies
- command handling with interop assemblies
ms.assetid: 8f4af525-39e5-4e69-92c8-d3efabe80bb2
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: c0d2cf9218743ec21121d849482e5a3086b36ab2
ms.lasthandoff: 02/22/2017

---
# <a name="commands-and-menus-that-use-interop-assemblies"></a>命令和使用互操作程序集的菜单
通过使用互操作程序集实现菜单和工具栏命令的 VSPackage 必须︰  
  
-   通知[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]集成的开发环境 (IDE) 有关所支持的命令和是否当前启用它们。  
  
-   遵循的规则 （合同条款） 处理的命令。  
  
-   显式实现使用的命令处理<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>或<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>接口。</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> </xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>  
  
 以下介绍如何执行这些任务。  
  
## <a name="in-this-section"></a>本节内容  
 [通过使用互操作程序集确定命令状态](../../extensibility/internals/determining-command-status-by-using-interop-assemblies.md)  
 描述如何 VSPackage 通知 IDE 有关哪些命令它支持并将它们当前是否启用。  
  
 [在互操作程序集的命令协定](../../extensibility/internals/command-contracts-in-interop-assemblies.md)  
 提供了所使用的所有实现使用互操作程序集的命令的 Vspackage 的基本命令协定的定义  
  
 [实现](../../extensibility/internals/command-implementation.md)  
 提供如何 VSPackage 实施命令的概述。  
  
 [注册互操作程序集的命令处理程序](../../extensibility/internals/registering-interop-assembly-command-handlers.md)  
 描述通知 IDE VSPackage 提供命令处理程序所需的注册表条目。  
  
## <a name="related-sections"></a>相关章节  
 [可用性](../../extensibility/internals/command-availability.md)  
 描述了 IDE 用于确定哪些 VSPackage 命令可供，哪些对象如何处理它们的条件。  
  
 [Vspackage 如何添加用户界面元素](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)  
 提供有关如何创建使用的用户界面的详细信息[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]命令的支持。  
  
 [Vspackage 中的命令传送](../../extensibility/internals/command-routing-in-vspackages.md)  
 用于将具有正确的命令请求的对象的关联过程的概述。
