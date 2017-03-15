---
title: "使用旧 API 使用文本标记 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "编辑器 [Visual Studio SDK]，旧的文本标记"
ms.assetid: 937a0b19-1216-45d5-a7ad-4fe1d6f73097
caps.latest.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 16
---
# 使用旧 API 使用文本标记
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

文本标记是文本的一个浮动的大小会影响文本区域显示和行为的缓冲区。  标记包括断点、书签、波浪下划线和只读区域。  文本标记基本上是使用语法着色不同。  语法着色是一种快速传达与文本区域的语言语法。  语法着色请求通常，当窗口重绘屏幕时，时，速度至关重要时。  语法着色更改只选中文本的颜色。  文本标记可以更改许多其他文本属性。  text 标记可以浮动 “访问”并将特殊的行为和着色。  
  
 出于性能开销与文本标记，不要创建文本缓冲区的许多标记。  每个标记每次更新用户编辑缓冲区内容。  
  
> [!NOTE]
>  用户可以更改一个可视标记类型的颜色，而不删除其形状和样式。  有关更多信息，请参见 [“选项”对话框 \-\>“环境”\-\>“字体和颜色”](../ide/reference/fonts-and-colors-environment-options-dialog-box.md)。  
  
## 相关主题  
  
|标题|说明|  
|--------|--------|  
|[如何: 添加标准文本标记](../extensibility/how-to-add-standard-text-markers.md)|描述如何将 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 核心编辑器提供的标准文本标记类型到文本视图。|  
|[如何: 实现错误标记](../extensibility/how-to-implement-error-markers.md)|描述如何实现将使用红色波浪下划线，用于指示错误 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 标记的实例。|  
|[如何: 创建自定义文本标记](../extensibility/how-to-create-custom-text-markers.md)|描述如何创建和添加自定义文本标记类型到文本视图。|  
|[如何: 使用文本标记](../extensibility/how-to-use-text-markers.md)|解释如何添加文本标记。|  
|[在核心编辑器](../extensibility/inside-the-core-editor.md)|描述核心编辑器的功能并提供有关如何的详细信息自定义核心编辑器。|  
|[Editor Features](http://msdn.microsoft.com/zh-cn/bdac940d-1f14-4019-a01f-fd0bb3dc7198)|描述功能在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 核心编辑器。|  
  
## 引用  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType>  
 是否提供了统一框架有关特定文本标记类型的信息，预定义由编辑器或签入 VSPackage。  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLineMarker>  
 使用二维坐标，提供对和调整文本标记的位置在文本缓冲区。  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker>  
 用于管理文本标记的方法。  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>  
 提供回调。 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE，并用于调整文本标记的其他处理。  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientAdvanced>  
 扩展通过 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> 接口可通过提供附加的回调的函数。  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientEx>  
 扩展通过 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> 接口可通过提供附加的回调的函数。  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerColorSet>  
 使标记类型确定其他标记类型是否共享同一组颜色。  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider>  
 为核心编辑器中的文本标记提供上下文。  对核心编辑器的每个文本标记类型， IDE 会创建单独的 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> 对象。  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerGlyphDropHandler>  
 为标记提供标志符号支持拖放编辑的处理程序。  标志符号是指示标记位置的图标。  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider>  
 返回从提供文本标记为其他 Vspackage 的服务的一 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType> 接口。  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStreamMarker>  
 使用一维坐标，提供对和调整文本标记的位置在文本缓冲区。  如果可能，不要使用此接口。