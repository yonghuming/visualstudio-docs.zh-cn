---
title: "属性显示网格 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: properties [Visual Studio SDK], grid
ms.assetid: 318e41b0-acf5-4842-b85e-421c9d5927c5
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 35b36c357c9b98d81627eea0d511b0b4fd49f693
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="properties-display-grid"></a>显示属性网格
**属性**窗口显示在网格中的字段。 左侧的列包含的属性名称;右侧列包含的属性值。  
  
## <a name="working-with-the-grid"></a>使用网格  
 两个列列表显示了可以在设计时和它们的当前设置更改的独立于配置的属性。 请注意，可能不会显示所有属性。 属性可以设置为隐藏，例如，通过实现<xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A>方法。 具体而言，以便隐藏具有子属性的属性：  
  
1.  设置`pfDisplay`中的参数<xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.DisplayChildProperties%2A>到`FALSE`。  
  
2.  设置`pfHide`中的参数<xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A>到`TRUE`。  
  
 信息推送到**属性**窗口中，IDE 使用<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>。 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>由每个窗口，其中包含与相关属性中显示的可选择对象 Vspackage**属性**窗口。 **解决方案资源管理器**的实现<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>调用`GetProperty`使用<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>项目层次结构获取层次结构中的可浏览对象中。  
  
 如果你的 VSPackage 不支持<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>，尝试使用 IDE<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>使用的值<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>或多个层次结构项目提供。  
  
 你不需要创建 VSPackage 的项目<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>因为 IDE 提供窗口包，将其实现 (例如，**解决方案资源管理器**) 构造<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>代表它。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>包含由 IDE 调用的三种方法：  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.CountObjects%2A>包含选择要在中显示的对象数**属性**窗口。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A>返回`IDispatch`中显示所选对象**属性**窗口。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A>使任何返回的对象<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A>供选择的用户。 这使 VSPackage 可以直观地更新 UI 中的用户显示所选内容。  
  
 **属性**窗口提取信息从`IDispatch`对象来检索要浏览的属性。 属性浏览器使用`IDispatch`询问哪些属性的对象它支持通过查询`ITypeInfo`，从中获取从`IDispatch::GetTypeInfo`。 浏览器然后使用这些值来填充**属性**窗口和单个属性的值显示在网格中的更改。 属性信息是对象本身中维护的。  
  
 因为返回的对象支持`IDispatch`，调用方可以通过调用获取信息，如对象的名称`IDispatch::Invoke`或`ITypeInfo::Invoke`具有的预定义的调度标识符 (DISPID) 的表示所需的信息。 声明的 Dispid 是负值以确保它们不会与用户定义的标识符发生冲突。  
  
 **属性**窗口显示不同类型的字段，具体取决于所选对象的特定属性的特性。 这些字段包括编辑框、 下拉列表和指向自定义编辑器对话框。  
  
-   枚举列表中包含的值检索<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A>查询到`IDispatch`。 可以在属性网格中更改枚举列表中获取值，通过双击字段名称，或通过单击值，并从下拉列表中选择新值。 对于具有预定义的枚举列表中的设置的属性，双击属性列表中的属性名称会循环访问可用的选项。 预定义的属性仅有两个选项，如 true/false，双击要选项之间切换的属性名称。  
  
-   如果<xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HasDefaultValue%2A>是`false`，值已更改，以粗体显示的值，该值指示。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.CanResetPropertyValue%2A>用于确定是否值可以重置为原始值。 因此，你可以改回为默认值通过右键单击值，然后选择如果**重置**从显示的菜单。 否则，你必须手动更改回默认值的值。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>此外可以本地化和隐藏在设计时显示的属性的名称，但不会影响在运行时显示的属性名称。  
  
-   单击省略号 （...） 按钮会显示用户可以从中选择 （如颜色选取器或字体列表） 的属性值的列表。 <xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder>提供这些值。  
  
## <a name="see-also"></a>另请参阅  
 [扩展属性](../../extensibility/internals/extending-properties.md)