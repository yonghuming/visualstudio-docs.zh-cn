---
title: "命令可用性 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "命令中上下文"
  - "菜单项，可见性上下文"
ms.assetid: c74e3ccf-d771-48c8-a2f9-df323b166784
caps.latest.revision: 34
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 34
---
# 命令可用性
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Visual Studio 上下文确定有哪些命令。 上下文可能会更改取决于当前项目、 当前编辑器、 加载、 Vspackage 和集成的开发环境 \(IDE\) 的其他方面。  
  
## 命令的上下文  
 下列命令的上下文中是最常见。  
  
-   **IDE** IDE 所提供的命令始终是可用的。  
  
-   **VSPackage** Vspackage 可以定义显示或隐藏命令的时间。  
  
-   **项目** 项目命令仅出现在当前选定的项目。  
  
-   **编辑器** 一次只能有一个编辑器可以处于活动状态。 提供了从活动的编辑器的命令。 编辑器与语言服务紧密合作。 语言服务必须处理其关联的编辑器的上下文中的命令。  
  
-   **文件类型** 编辑器可以加载多个文件的类型。 可用的命令可以根据文件类型更改。  
  
-   **活动窗口** 的最后一个活动文档窗口的键绑定设置的用户界面 \(UI\) 上下文。 但是，该工具窗口具有类似于内部的 Web 浏览器的键绑定表还可以设置 UI 上下文。 对于多选项卡式文档窗口 HTML 编辑器等编辑器，每个选项卡具有不同的命令上下文 GUID。 注册一个工具窗口后，将始终上可用 **视图** 菜单。  
  
-   **UI 上下文** UI 上下文的值由标识 <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT> 类，例如， <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_SolutionBuilding> 生成解决方案后，或 <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_Debugging> 调试器处于活动状态时。 多个 UI 上下文可以同时处于活动状态。  
  
## 定义自定义上下文 Guid  
 如果尚未定义 GUID 不适当的命令上下文中，您可以在你的 VSPackage 中定义，然后编写其成为活动状态还是处于非活动状态所需控制命令的可见性。  
  
1.  通过调用注册的上下文 Guid <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A> 方法。  
  
2.  通过调用获取状态的上下文 GUID <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> 方法。  
  
3.  将通过调用上下文 Guid 打开和关闭 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A> 方法。  
  
    > [!CAUTION]
    >  请确保你的 VSPackage 不因为其他 Vspackage 可能依赖这些影响任何现有上下文中的 Guid。  
  
## 请参阅  
 [选择上下文对象](../../extensibility/internals/selection-context-objects.md)   
 [Vspackage 如何添加用户界面元素](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)