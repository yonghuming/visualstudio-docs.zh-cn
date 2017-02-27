---
title: "如何: 使用文本标记 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "编辑器 [Visual Studio SDK]，旧-使用文本标记"
ms.assetid: 76eed51c-eecb-4579-823e-13df2f0526b9
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# 如何: 使用文本标记
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

可应用于的文本标记 edit <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> 对象。  
  
## 过程  
  
#### 应用文本标记  
  
1.  获取 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager> 类的实例。  
  
    > [!NOTE]
    >  核心编辑器会自动应用标准文本标记应用于任何文档进行编辑，并且，显式应用标准文本标记不应是必需的。  
  
2.  获取标记的标记类型通过调用与文本标记 `GUID` 的 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager.GetRegisteredMarkerTypeID%2A> 方法感兴趣要使用的 ID。  
  
    > [!NOTE]
    >  不要使用 VSPackage 中 `GUID` 提供文本标记的或服务。  
  
3.  使用调用 ID 获得的标记类型 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager.GetRegisteredMarkerTypeID%2A> 方法作为参数调用 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> 方法或 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A> 方法应用于的文本标记应用于文本的特定区域。  
  
#### 将功能添加到文本标记  
  
1.  添加附加功能到一个文本标记，例如工具提示、一个特定的上下文菜单或处理程序的特殊情况的可能需要的。  这样做:  
  
2.  创建实现 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> 接口的对象。  
  
3.  如果附加功能需要，请实现 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientEx>和 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientAdvanced> 接口在同一对象实现 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> 接口。  
  
4.  通过创建的 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> 接口，用于对 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> 方法或 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A> 使用的方法应用于的文本标记应用于文本的特定区域。  
  
5.  在添加上下文菜单时支持到的文本标记区域来创建菜单是必需的。  
  
     有关如何创建上下文菜单的更多信息，请参见 [上下文菜单](../extensibility/context-menus.md)。  
  
6.  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 环境调用所提供的接口的方法，如 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.GetTipText%2A> 方法或 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.ExecMarkerCommand%2A> 方法根据需要。  
  
## 请参阅  
 [使用旧 API 使用文本标记](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [如何: 添加标准文本标记](../extensibility/how-to-add-standard-text-markers.md)   
 [如何: 创建自定义文本标记](../extensibility/how-to-create-custom-text-markers.md)   
 [如何: 实现错误标记](../extensibility/how-to-implement-error-markers.md)