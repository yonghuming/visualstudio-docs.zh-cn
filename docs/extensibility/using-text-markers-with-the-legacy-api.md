---
title: "使用文本标记用于旧 API |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - text markers
ms.assetid: 937a0b19-1216-45d5-a7ad-4fe1d6f73097
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 64f4d7f7e4a71c1d304bfa5045175fd613bcb539
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="using-text-markers-with-the-legacy-api"></a>使用文本标记用于旧 API
文本标记是文本的一个浮点的缓冲区中，可能会影响显示范围和文本区域的行为。 标记包括断点、 书签、 波浪形下划线，和只读的区域。 文本标记存在基本上不同语法着色。 语法着色可快速，进行通信的文本区域与关联的语言语法。 Windows 屏幕上，可时重新绘制速度很重要时，通常被请求语法着色。 语法着色的文本颜色的更改。 文本标记可以更改许多其他文本属性。 文本标记可以"浮动"，应用特殊行为和着色。  
  
 由于与文本标记相关的性能开销，而不要创建多个标记文本缓冲区。 每个标记是用户编辑缓冲区内容每次更新。  
  
> [!NOTE]
>  用户可以更改可见标记类型，但其不形状和样式的颜色。 有关详细信息，请参阅[字体和颜色，环境中，选项对话框](../ide/reference/fonts-and-colors-environment-options-dialog-box.md)。  
  
## <a name="related-topics"></a>相关主题  
  
|标题|描述|  
|-----------|-----------------|  
|[如何： 添加标准文本标记](../extensibility/how-to-add-standard-text-markers.md)|描述如何添加标准文本标记类型提供的[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]核心编辑器到文本视图。|  
|[如何： 实现错误标记](../extensibility/how-to-implement-error-markers.md)|描述如何实现的实例[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]用于通过使用红色的波浪形下划线指示错误的标记。|  
|[如何： 创建自定义文本标记](../extensibility/how-to-create-custom-text-markers.md)|描述如何创建和自定义文本标记类型添加到文本视图。|  
|[如何： 使用文本标记](../extensibility/how-to-use-text-markers.md)|说明如何添加文本标记。|  
|[在核心编辑器](../extensibility/inside-the-core-editor.md)|描述的核心编辑器的功能，并提供有关如何自定义核心编辑器的详细信息。|  
|[编辑器功能](http://msdn.microsoft.com/en-us/bdac940d-1f14-4019-a01f-fd0bb3dc7198)|描述中提供的功能[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]核心编辑器。|  
  
## <a name="reference"></a>参考  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType>  
 提供预定义的由编辑器还是由 VSPackage 注册获取有关特定文本标记类型，信息的统一机制。  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLineMarker>  
 可以访问和使用二维坐标调整文本标记中的文本缓冲区的位置。  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker>  
 提供用于管理文本标记的方法。  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>  
 提供到回调[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]IDE 和其他进程，用于调整文本标记。  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientAdvanced>  
 扩展的功能通过提供<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>通过提供其他回调接口。  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientEx>  
 扩展的功能通过提供<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>通过提供其他回调接口。  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerColorSet>  
 使标记类型以确定其他标记类型是否共享相同的颜色集。  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider>  
 提供用于在核心编辑器中的文本标记上下文。 对于每个核心编辑器中的文本标记类型，IDE 将创建一个单独<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider>对象。  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerGlyphDropHandler>  
 提供有关其标志符号支持拖放编辑的标记处理程序。 标志符号是一个图标，指示一个标记的位置。  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider>  
 返回<xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType>接口从服务中提供到其他 Vspackage 的标记的文本。  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStreamMarker>  
 可以访问和使用一维坐标调整文本标记中的文本缓冲区的位置。 如果可能，则不要使用此接口。