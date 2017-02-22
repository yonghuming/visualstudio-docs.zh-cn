---
title: "属性窗口字段和接口 | Microsoft Docs"
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
  - "属性窗口、 字段和接口"
ms.assetid: 0328f0e5-2380-4a7a-a872-b547cb775050
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# 属性窗口字段和接口
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

选择模型中确定信息。 **属性** 窗口中显示基于有焦点在 IDE 的窗口。  每个窗口和对象所选窗口中，可能有它的驱动器的选择上下文对象对全局选择上下文。  ，当该窗口具有焦点时，环境更新具有值的全局选择上下文从窗架。  当焦点更改时，这样做选择上下文。  
  
## 跟踪在 IDE 中选择  
 窗架或站点，拥有 IDE，名为 <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>中的服务。  下列步骤演示在选择更改，是由于用户更改的焦点切换到另一个打开或选择不同的项目项。 **解决方案资源管理器**，如何实现更改。 **属性** 窗口显示的内容。  
  
1.  在所选窗口站点的 VSPackage 创建的对象调用 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> 线 <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> 调用 <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>。  
  
2.  选择容器，，假定由所选窗口，创建自己的 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> 对象。  当所选内容更改时， VSPackage 环境中调用 <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> 通知所有侦听器，包括 **属性** 窗口中，更改。  它还提供对层次结构和项目信息与新选定相关。  
  
3.  调用 <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> 和将在 `VSHPROPID_BrowseObject` 参数的选定的层次结构项填充 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> 对象。  
  
4.  从 [IDispatch Interface](http://msdn.microsoft.com/zh-cn/ebbff4bc-36b2-4861-9efa-ffa45e013eb5) 派生的对象为请求的项的 <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> 返回，并且，该环境包装到 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> \(请参见下面的步骤\)。  如果调用失败，则环境进行第二次调用 `IVsHierarchy::GetProperty`，将层次结构项目或项目提供的选择容器 <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> 。  
  
     项目 VSPackage 不创建 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> 例如，因为实现它的由环境提供的 windows VSPackage \(， **解决方案资源管理器**\) 构造代表它的 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> 。  
  
5.  该环境调用的 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> get 方法对象基于 `IDispatch` 接口填充 **属性** 窗口。  
  
 当更改在 **属性** 窗口的值， Vspackage 实现报告对元素值的更改的 `IVsTrackSelectionEx::OnElementValueChangeEx` 和 `IVsTrackSelectionEx::OnSelectionChangeEx` 。  该环境中与属性值同步的 **属性** windows 然后调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> 或 <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> 保留显示此信息。  有关更多信息，请参见 [在“属性”窗口中更新属性值](../../misc/updating-property-values-in-the-properties-window.md)。  
  
 除了选择在 **解决方案资源管理器** 的不同项目项之外公开属性与该项目相关，还可以选择不同的对象从窗体的内部或文档窗口使用下拉列表中可用 **属性** 窗口。  有关更多信息，请参见 [属性窗口对象列表](../../extensibility/internals/properties-window-object-list.md)。  
  
 可以更改信息在从字母的 **属性** 窗口网格中显示为绝对方式，，此外，如果有，则可以通过单击适当的按钮来打开选定对象的属性页。 **属性** 窗口。  有关更多信息，请参见[属性窗口的按钮:](../../extensibility/internals/properties-window-buttons.md)和 [属性页](../../extensibility/internals/property-pages.md)。  
  
 最后， **属性** 窗口底部。 **属性** " 窗口网格还包含选定的字段的说明。  有关更多信息，请参见 [从属性窗口中获取字段说明](../../misc/getting-field-descriptions-from-the-properties-window.md)。  
  
## 请参阅  
 [将属性扩展](../../extensibility/internals/extending-properties.md)