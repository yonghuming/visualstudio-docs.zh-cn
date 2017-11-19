---
title: "命令可用性 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- commands, context
- menu items, visibility contexts
ms.assetid: c74e3ccf-d771-48c8-a2f9-df323b166784
caps.latest.revision: "34"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ecdbdc3074ad6dc80a8bd713c46303ba3cca628c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="command-availability"></a>命令可用性
Visual Studio 上下文确定哪些命令可。 具体取决于当前项目、 当前编辑器、 已加载，Vspackage 和集成的开发环境 (IDE) 的其他方面，可以更改上下文。  
  
## <a name="command-contexts"></a>命令上下文  
 下面的命令上下文是最常见的。  
  
-   **IDE**客始终可使用由 IDE 提供的命令。  
  
-   **VSPackage** Vspackage 可以定义可显示或隐藏命令的时间。  
  
-   **项目**项目命令显示仅为当前所选项目。  
  
-   **编辑器**一次只有一个编辑器可以处于活动状态。 提供了从活动编辑器中的命令。 与语言服务紧密编辑器。 语言服务必须处理其关联的编辑器的上下文中的命令。  
  
-   **文件类型**编辑器可以加载多个文件的类型。 可用的命令可以更改根据文件类型。  
  
-   **活动窗口**的最后一个活动文档窗口设置的用户界面 (UI) 上下文键绑定。 但是，该工具窗口具有类似于内部的 Web 浏览器的键绑定表还可以设置的 UI 上下文。 对于多选项卡式文档窗口 （如 HTML 编辑器），每个选项卡具有不同的命令上下文 GUID。 注册工具窗口后，将始终上可用**视图**菜单。  
  
-   **UI 上下文**UI 上下文的值由标识<xref:Microsoft.VisualStudio.VSConstants.UICONTEXT>类，例如，<xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_SolutionBuilding>时正在生成解决方案，或<xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_Debugging>调试器处于活动状态时。 多个 UI 上下文可以同时处于活动状态。  
  
## <a name="defining-custom-context-guids"></a>定义自定义上下文 Guid  
 如果不合适的命令上下文中尚未定义的 GUID，你可以定义一个在你的 VSPackage，然后程序其成为活动或非活动所需控制你的命令的可见性。  
  
1.  通过调用注册上下文 Guid<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A>方法。  
  
2.  通过调用获取的 GUID 的上下文状态<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A>方法。  
  
3.  将通过调用上下文 Guid 打开和关闭<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A>方法。  
  
    > [!CAUTION]
    >  请确保你的 VSPackage 不影响任何现有上下文 Guid，因为其他 Vspackage 可能依赖于它们。  
  
## <a name="see-also"></a>另请参阅  
 [选择上下文对象](../../extensibility/internals/selection-context-objects.md)   
 [VSPackage 如何添加用户界面元素](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)