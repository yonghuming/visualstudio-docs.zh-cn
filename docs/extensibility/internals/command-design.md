---
title: "命令设计 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "命令"
  - "命令中实现"
ms.assetid: 097108c3-f758-4b87-89d6-b32d12d9041a
caps.latest.revision: 34
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 34
---
# 命令设计
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

将命令添加到 VSPackage 时，必须指定该文件夹的位置出现，那么，当它可用时，，以及如何将处理。  
  
## 定义命令  
 若要定义新的说明，请包括一个 Visual Studio 命令表 \(.vsct\) 文件在 VSPackage 项目。  使用 Visual Studio 包模板，如果创建了 VSPackage，该项目包含这些文件之一。  有关更多信息，请参见 [Visual Studio 命令表 \(。Vsct\) 文件](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)。  
  
 找到的 Visual Studio 将所有 .vsct 文件，以便可以显示命令。  由于这些文件从 VSPackage 二进制文件是不同的， Visual Studio 不需要加载包 " 查找 " 命令。  有关更多信息，请参见 [Vspackage 如何添加用户界面元素](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)。  
  
 Visual Studio 使用 <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> 注册属性定义菜单资源和命令。  有关更多信息，请参见 [实现](../../extensibility/internals/command-implementation.md)。  
  
 命令可以在运行时更改多种不同的方式。  可显示或隐藏，启用或禁用。  它们可以显示不同的文本或图标，或者包含不同的值。  大量自定义项可能在 Visual Studio 加载之前执行 VSPackage。  有关更多信息，请参见 [Vspackage 如何添加用户界面元素](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)。  
  
## 命令处理程序  
 如果您创建一个命令时，必须提供事件处理程序执行命令。  如果用户选择命令，必须正确路由它。  ，如果用户选择这样，执行路由命令意味着将其发送到正确的 VSPackage 启用或禁用它，隐藏或显示该数据，并执行。  有关更多信息，请参见 [路由算法](../../extensibility/internals/command-routing-algorithm.md)。  
  
## Visual Studio 命令环境  
 Visual Studio 可以承载任意数量的 Vspackage，因此，每个都可提供其设置自己的命令。  该环境将显示适用于当前任务只的命令。  有关更多信息，请参见[可用性](../../extensibility/internals/command-availability.md)和 [选择上下文对象](../../extensibility/internals/selection-context-objects.md)。  
  
 定义新的命令的 VSPackage，菜单、工具栏、快捷菜单提供其命令信息。 Visual Studio 在安装时通过引用在本机或托管程序集中的资源的注册表项。  每个资源随后引用二进制数据资源 \(.cto\) 文件，这样，当您编译 Visual Studio 命令表 \(.vsct\) 文件。  这使 Visual Studio 提供了合并的命令设置，菜单和工具栏，而不必加载的所有安装的 VSPackage。  
  
### 命令组织  
 该环境由组、优先级别和菜单确定命令。  
  
-   组相关命令，例如， **剪辑**、 **复制**和 **粘贴** 命令组的逻辑集合。  组是出现在菜单的命令。  
  
-   优先级确定各指令在组中显示菜单上的命令。  
  
-   菜单作为组的容器。  
  
 环境预定义的某些命令、组和菜单。  有关更多信息，请参见 [默认的命令、 组和工具栏位置](../../extensibility/internals/default-command-group-and-toolbar-placement.md)。  
  
 命令可分配到主机组。  主要组控件命令的位置位于主菜单结构和在 **自定义** 对话框。  命令可以在多个组中显示;例如，命令可以在主菜单，在快捷菜单和工具栏中的。  有关更多信息，请参见 [Vspackage 如何添加用户界面元素](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)。  
  
### 命令传送  
 调用和路由 Vspackage 的命令处理具有对对象实例的方法处理不同。  
  
 该环境从最里边的 \(本地\) 命令上下文按顺序路由命令，根据当前选择，向最外面的 \(全局\) 上下文。  可以执行命令的第一个上下文是用于处理它。  有关更多信息，请参见 [路由算法](../../extensibility/internals/command-routing-algorithm.md)。  
  
 使用 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 接口，在大多数实例，环境处理顺序。  由于命令传送模式可处理命令的许多不同的对象， <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 可由任意数量的对象实现;其中包括 Microsoft Activex 控件，窗口视图实现，文档对象、项目层次结构和 VSPackage 对象 \(对于全局顺序\)。  在某些专用用例，例如，路由层次结构中的顺序，必须实现 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 接口。  
  
## 相关主题  
  
|标题|说明|  
|--------|--------|  
|[实现](../../extensibility/internals/command-implementation.md)|描述如何在 VSPackage 的命令。|  
|[可用性](../../extensibility/internals/command-availability.md)|描述 Visual Studio 上下文如何确定哪些命令可用。|  
|[路由算法](../../extensibility/internals/command-routing-algorithm.md)|描述 Visual Studio 命令传送体系结构如何启用指令由其他 Vspackage 处理。|  
|[放置指导原则](../../extensibility/internals/command-placement-guidelines.md)|在 Visual Studio 环境中建议如何确定命令。|  
|[Vspackage 如何添加用户界面元素](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)|描述 Vspackage 如何在使用 Visual Studio 命令体系结构。|  
|[默认的命令、 组和工具栏位置](../../extensibility/internals/default-command-group-and-toolbar-placement.md)|描述 Vspackage 如何以最佳方式使用在 Visual Studio 中包含的命令。|  
|[管理 Vspackage](../../extensibility/managing-vspackages.md)|描述 Visual Studio 如何加载 Vspackage。|  
|[Visual Studio 命令表 \(。Vsct\) 文件](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)|提供有关基于 XML 的 .vsct 文件的信息，在 Vspackage 描述命令布局和外观。|