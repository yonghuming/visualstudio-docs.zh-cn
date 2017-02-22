---
title: "显示属性网格 | Microsoft Docs"
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
  - "[Visual Studio SDK]，属性网格"
ms.assetid: 318e41b0-acf5-4842-b85e-421c9d5927c5
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# 显示属性网格
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

网格中的 **属性** 窗口显示字段。  左列包含属性名称;右列中包含属性值。  
  
## 与网格一起使用  
 两列列表可以在设计时更改及其当前设置的显示独立于配置的属性。  请注意所有属性可能不显示。  ，例如，属性设置为隐藏通过执行 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A> 方法。  具体而言，隐藏具有子属性以查看的属性， [隐藏具有子属性的属性](../../misc/hiding-properties-that-have-child-properties.md)。  
  
 若要驱动器信息。 **属性** 窗口， IDE 使用 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>。  <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> 由包含在 **属性** 窗口中显示的相关属性的可选对象的每个窗口的 Vspackage 调用。  <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> 的解决方案资源管理器的实现调用 `GetProperty` 使用在项目层次结构的 <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> 获取在层次结构中 browseable 对象。  
  
 如果 VSPackage 不支持 <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>，则 IDE 将尝试使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> 将该值用于层次结构项目或项目提供的 <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> 。  
  
 该项目 VSPackage 不需要创建 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> 例如，因为实现它的由 IDE 提供的 windows 包 \(， **解决方案资源管理器**\) 构造代表它的 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> 。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> 包括由 IDE 调用的三种方法:  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.CountObjects%2A> 在 **属性** 窗口包含选定对象的数量显示。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> 返回在 **属性** 窗口中选择显示的 `IDispatch` 对象。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A> 可以为 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> 返回的对象将选择用户。  这允许 VSPackage 直观地更新选定内容中显示的 UI 的用户。  
  
 **属性** 窗口 `IDispatch` 从对象提取信息检索浏览的属性。  属性浏览器使用 `IDispatch` 询问对象的特性它由查询的 `ITypeInfo`支持，从 `IDispatch::GetTypeInfo`获取。  浏览器然后使用这些值填充 **属性** 窗口和更改网格中显示的各个属性的值。  属性信息在对象中维护  
  
 由于返回的对象支持 `IDispatch`，调用方可以通过调用 `IDispatch::Invoke` 或 `ITypeInfo::Invoke` 获取信息 \(如对象名称与表示所需信息的预定义的调度标识符 \(dispid\)。  声明的 Dispid 为负确保它们不冲突使用用户定义的标识符。  
  
 **属性** 于 windows 选定对象的特定属性的属性公开字段具有不同的类型。  这些字段包括编辑框，下拉列表，并链接到自定义编辑器对话框。  
  
-   在包含的值枚举列表通过对 `IDispatch`的一个 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> 查询检索。  从获取的值枚举在属性网格中列出可以更改中双击字段名，或者通过单击值并选择新值从下拉列表。  为预定义枚举设置的属性列表，双击该属性的属性名称通过可用的选择列表周期。  对于具有两个选项的预定义属性，例如真\/错误，只需双击属性名称添加到在选择之间切换。  
  
-   如果 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HasDefaultValue%2A> 是 `false`，指示更改了该值，该值将以粗体显示。  <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.CanResetPropertyValue%2A> 用于确定值是否可重置为原始值。  如果是这样，您可以更改回该默认值。右击该值并选择 **重置** 从显示的菜单。  否则，必须手动更改该值返回给默认值。  <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> 还允许本地化和隐藏属性的名称将显示在设计时，但是，不会影响在运行时显示的属性名称。  
  
-   单击省略号 \(...\) 按钮公开的属性值的列表用户可以选择 \(例如颜色选取器或字体的列表\)。  <xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder> 提供这些值。  
  
## 请参阅  
 [将属性扩展](../../extensibility/internals/extending-properties.md)