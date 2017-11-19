---
title: "命令设计 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- commands
- commands, implementation
ms.assetid: 097108c3-f758-4b87-89d6-b32d12d9041a
caps.latest.revision: "34"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: cf6d0d7a9aa556aab454f90e4dcfc5dc4f236c03
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="command-design"></a>命令设计
当你将命令添加到 VSPackage 时，你必须指定它的位置显示、 时可用，和它是要处理。  
  
## <a name="defining-commands"></a>定义命令  
 若要定义新的命令，请在你 VSPackage 项目中包含的 Visual Studio 命令表 (.vsct) 文件。 如果已通过使用 Visual Studio 包模板创建 VSPackage，该项目将包含这些文件之一。 有关详细信息，请参阅[Visual Studio 命令表 (。Vsct) 文件](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)。  
  
 Visual Studio 会发现，以便它可以显示命令的所有.vsct 文件都合并。 因为这些文件从二进制 VSPackage 的不同，则不需要为了查找的命令将包加载 Visual Studio。 有关详细信息，请参阅[如何 Vspackage 添加用户界面元素](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)。  
  
 Visual Studio 将使用<xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute>注册属性来定义菜单资源和命令。 有关详细信息，请参阅[实现](../../extensibility/internals/command-implementation.md)。  
  
 在多种不同方式，可以在运行时更改命令。 它们可以显示或隐藏、 启用或禁用。 它们可以显示不同的文本或图标，或包含不同的值。 Visual Studio 加载你的 VSPackage 之前可能执行了大量的自定义项。 有关详细信息，请参阅[如何 Vspackage 添加用户界面元素](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)。  
  
## <a name="command-handlers"></a>命令处理程序  
 在创建命令时，你必须提供事件处理程序以执行该命令。 如果用户选择命令时，它必须将相应地路由。 路由命令意味着发送到正确的 VSPackage 可以启用或禁用它，隐藏或显示它，并执行它，如果用户选择这样做。 有关详细信息，请参阅[路由算法](../../extensibility/internals/command-routing-algorithm.md)。  
  
## <a name="the-visual-studio-command-environment"></a>Visual Studio 命令环境  
 Visual Studio 可以承载任意数量的 Vspackage，而每个可以自己命令集。 环境显示只有适合当前任务的命令。 有关详细信息，请参阅[可用性](../../extensibility/internals/command-availability.md)和[选择上下文对象](../../extensibility/internals/selection-context-objects.md)。  
  
 定义新的命令、 菜单、 工具栏或快捷菜单的 VSPackage 提供其命令信息到 Visual Studio 在通过引用本机或托管程序集中的资源的注册表项的安装时间。 然后，每个资源引用时编译 Visual Studio 命令表 (.vsct) 文件生成的二进制数据资源 (.cto) 文件。 这使 Visual Studio，而无需加载每个已安装的 VSPackage 提供合并的命令集、 菜单和工具栏。  
  
### <a name="command-organization"></a>命令组织  
 环境将置于按组、 优先级别和菜单命令。  
  
-   组是的相关命令的逻辑集合，例如，**剪切**，**复制**，和**粘贴**命令组。 组是在菜单显示的命令。  
  
-   优先级确定在组中的单个命令的菜单出现的顺序。  
  
-   菜单作为容器的组。  
  
 预定义了环境，某些命令、 组和菜单。 有关详细信息，请参阅[默认命令、 组和工具栏放置](../../extensibility/internals/default-command-group-and-toolbar-placement.md)。  
  
 命令可以分配给主要组。 主要组控制主菜单结构中并在该命令的位置**自定义**对话框。 命令可以出现在多个组;例如，命令可以是主菜单上，在快捷菜单，和工具栏。 有关详细信息，请参阅[如何 Vspackage 添加用户界面元素](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)。  
  
### <a name="command-routing"></a>命令传送  
 调用和 Vspackage 的路由命令的过程不同于在对象实例上调用方法的过程。  
  
 环境将路由到最外层的 （全局） 上下文命令按顺序从 （本地） 的最内层命令上下文中，基于当前所选内容。 无法执行该命令的第一个上下文是能够处理它。 有关详细信息，请参阅[路由算法](../../extensibility/internals/command-routing-algorithm.md)。  
  
 在大多数情况下，环境处理命令通过使用<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>接口。 命令路由方案支持许多不同的对象以处理命令，因为<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>可以实现任意数量的对象; 这些包括 Microsoft ActiveX 控件、 窗口视图实现，文档对象、 项目层次结构和 （对于全局命令） VSPackage 对象本身。 在某些特殊的情况下，例如，将路由在层次结构中，命令<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>必须实现接口。  
  
## <a name="related-topics"></a>相关主题  
  
|标题|描述|  
|-----------|-----------------|  
|[实现](../../extensibility/internals/command-implementation.md)|描述如何在 VSPackage 中实现命令。|  
|[可用性](../../extensibility/internals/command-availability.md)|描述如何 Visual Studio 上下文确定有哪些命令。|  
|[路由的算法](../../extensibility/internals/command-routing-algorithm.md)|介绍 Visual Studio 命令路由体系结构如何使命令均由不同的 Vspackage。|  
|[放置准则](../../extensibility/internals/command-placement-guidelines.md)|提供如何将命令放置在 Visual Studio 环境的建议。|  
|[VSPackage 如何添加用户界面元素](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)|描述如何 Vspackage 可以最大程度利用 Visual Studio 命令体系结构。|  
|[默认命令、组和工具栏位置](../../extensibility/internals/default-command-group-and-toolbar-placement.md)|描述如何 Vspackage 可以充分利用 Visual Studio 中包含的命令。|  
|[管理 VSPackages](../../extensibility/managing-vspackages.md)|介绍 Visual Studio 如何加载 Vspackage。|  
|[Visual Studio 命令表格 (.Vsct) 文件](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)|提供有关基于 XML 的.vsct 文件，用于描述的布局和外观的 Vspackage 中的命令的信息。|