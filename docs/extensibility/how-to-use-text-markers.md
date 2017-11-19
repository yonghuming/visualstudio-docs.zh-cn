---
title: "如何： 使用文本标记 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - using text markers
ms.assetid: 76eed51c-eecb-4579-823e-13df2f0526b9
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1070a88f1bae27b9ff10fedbf6a383ec30c1ed0e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-use-text-markers"></a>如何： 使用文本标记
文本标记可以用于编辑<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>对象。  
  
## <a name="procedures"></a>过程  
  
#### <a name="to-apply-text-markers"></a>将文本标记  
  
1.  获取实例<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager>类。  
  
    > [!NOTE]
    >  核心编辑器时自动适用于任何它正在编辑的文档使用标准文本标记和不应需要显式应用标准文本标记。  
  
2.  获取你感兴趣通过调用标记的标记类型 ID<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager.GetRegisteredMarkerTypeID%2A>方法替换`GUID`你想要使用的文本标记。  
  
    > [!NOTE]
    >  不要使用`GUID`VSPackage 或提供文本标记的服务。  
  
3.  使用通过调用获取的标记类型 ID<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager.GetRegisteredMarkerTypeID%2A>方法作为参数，以调用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A>方法或<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A>方法将文本标记应用到给定的文本区域。  
  
#### <a name="to-add-features-to-text-markers"></a>若要将功能添加到文本标记  
  
1.  可能需要将其他功能添加到文本标记，如工具提示、 特殊的上下文菜单上或处理程序的特殊情况。 若要这样做：  
  
2.  创建一个对象，实现<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>接口。  
  
3.  如果需要其他功能，请实现<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientEx>，和<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientAdvanced>实现对同一对象的接口<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>接口。  
  
4.  传递<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>创建，对调用的接口<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A>方法或<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A>方法用于将文本标记应用到给定的文本区域。  
  
5.  添加到文本标记区域的上下文菜单支持时，必须创建菜单。  
  
     有关详细信息如何创建上下文菜单，请参阅[上下文菜单](../extensibility/context-menus.md)。  
  
6.  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]环境调用的方法提供的接口，如<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.GetTipText%2A>方法，或<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.ExecMarkerCommand%2A>方法根据需要。  
  
## <a name="see-also"></a>另请参阅  
 [使用文本标记用于旧 API](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [如何： 添加标准文本标记](../extensibility/how-to-add-standard-text-markers.md)   
 [如何： 创建自定义文本标记](../extensibility/how-to-create-custom-text-markers.md)   
 [如何： 实现错误标记](../extensibility/how-to-implement-error-markers.md)