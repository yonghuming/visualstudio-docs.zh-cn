---
title: "如何: 添加标准文本标记 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "编辑器 [Visual Studio SDK]，旧的标准文本标记"
ms.assetid: a39fca69-0014-474c-933f-51f0e9b9617e
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# 如何: 添加标准文本标记
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

使用以下过程创建一个默认文本标记类型提供 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 核心编辑器。  
  
### 创建文本标记  
  
1.  取决于您是使用一个或二维坐标系，请调用 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> 方法或 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A> 方法创建一个新的文本标记。  
  
     此方法调用中，指定标记类型、文本范围创建标记和 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> 接口。  则此方法返回指向新创建的文本标记。  标记类型从 <xref:Microsoft.VisualStudio.TextManager.Interop.MARKERTYPE> 枚举中采用。  ，如果要通知标记操作，请指定 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> 接口。  
  
    > [!NOTE]
    >  创建仅在主 UI 线程的文本标记。  核心编辑器依赖于文本缓冲区的内容创建文本标记，并文本缓冲区不是线程安全的。  
  
## 添加自定义命令  
 实现 `IVsTextMarkerClient` 接口并提供指向其从标记将引发标记行为通过多种方式。  首先，这允许您为标记提供提示和执行命令。  这还使得收到单个标记的事件通知和创建标记中的自定义上下文菜单。  使用以下过程添加自定义命令。标记上下文菜单。  
  
#### 添加自定义上下文菜单命令。  
  
1.  在上下文菜单中显示之前，环境 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.GetMarkerCommandInfo%2A> 调用方法并向其传递指向受影响的文本标记和命令项目的数字在上下文菜单中。  
  
     例如，在上下文菜单中的断点特定命令通过 **新断点**包括 **移除断点** ，显示在下面的屏幕快照。  
  
     ![标记上下文菜单](~/extensibility/media/vsmarkercontextmenu.gif "vsMarkercontextmenu")  
  
2.  通过一个自定义命令的名称一些文本。  例如，在中，如果环境已未提供它， **移除断点** 可能是自定义命令。  还通过命令是否支持，可用和启用，和\/或一个打开 \- 关闭触发器。  此环境使用此信息显示在上下文菜单中自定义命令的正确方式。  
  
3.  若要执行该命令时，该环境 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.ExecMarkerCommand%2A> 调用方法，向其传递指向文本标记并从上下文菜单中的命令数。  
  
     使用此的此信息称为执行文本标记的任何事件自定义命令指定。  
  
## 请参阅  
 [使用旧 API 使用文本标记](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [如何: 实现错误标记](../extensibility/how-to-implement-error-markers.md)   
 [如何: 创建自定义文本标记](../extensibility/how-to-create-custom-text-markers.md)   
 [如何: 使用文本标记](../extensibility/how-to-use-text-markers.md)