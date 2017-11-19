---
title: "如何： 添加标准文本标记 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - standard text markers
ms.assetid: a39fca69-0014-474c-933f-51f0e9b9617e
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1fb92185dd2efee7f42ce1ba4d97435e0b2e8a68
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-add-standard-text-markers"></a>如何： 添加标准文本标记
使用以下过程创建一个与提供的默认文本标记类型[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]核心编辑器。  
  
### <a name="to-create-a-text-marker"></a>创建文本标记  
  
1.  根据你使用的一个或两个-维坐标系，调用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A>方法或<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A>方法来创建新的文本标记。  
  
     在此方法调用中，指定标记类型，要通过，创建标记的文本范围和<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>接口。 然后，此方法将指针返回到新创建的文本标记。 标记类型，将从<xref:Microsoft.VisualStudio.TextManager.Interop.MARKERTYPE>枚举。 指定<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>接口如果你想要将标记事件的通知。  
  
    > [!NOTE]
    >  主 UI 线程上创建文本标记。 核心编辑器依赖于要创建文本标记的文本缓冲区的内容和文本缓冲区不是线程安全。  
  
## <a name="adding-a-custom-command"></a>添加自定义命令  
 实现`IVsTextMarkerClient`接口，并向它提供一个指针，从一个标记增强了以下几种方式的标记行为。 首先，这允许你为你的标记中提供提示，还可以执行命令。 这还允许您以接收单个标记的事件通知，并通过标记创建自定义上下文菜单。 使用以下过程将自定义命令添加到标记上下文菜单。  
  
#### <a name="to-add-a-custom-command-to-the-context-menu"></a>若要将自定义命令添加到上下文菜单  
  
1.  会显示上下文菜单之前，则环境将调用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.GetMarkerCommandInfo%2A>方法和传递对您指向文本标记的指针的影响以及上下文菜单中的命令项的数量。  
  
     例如，上下文菜单上的特定于断点的命令包括**删除断点**通过**新断点**，如下面的屏幕截图中显示。  
  
     ![标记上下文菜单](../extensibility/media/vsmarkercontextmenu.gif "vsMarkercontextmenu")  
  
2.  传递回标识自定义命令的名称的一些文本。 例如，**删除断点**如果环境未已提供它可能是自定义命令。 你还将传递回该命令是受支持，可用并且已启用，并且/或者打开-关闭切换。 环境使用此信息来正确的方式在上下文菜单中显示的自定义的命令。  
  
3.  若要执行该命令，环境调用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.ExecMarkerCommand%2A>方法，你将指针传递到文本标记和上下文菜单中选择的命令数。  
  
     使用来自此调用的此信息来执行任何操作文本标记的自定义命令指示。  
  
## <a name="see-also"></a>另请参阅  
 [使用文本标记用于旧 API](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [如何： 实现错误标记](../extensibility/how-to-implement-error-markers.md)   
 [如何： 创建自定义文本标记](../extensibility/how-to-create-custom-text-markers.md)   
 [如何： 使用文本标记](../extensibility/how-to-use-text-markers.md)