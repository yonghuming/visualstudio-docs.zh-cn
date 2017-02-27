---
title: "如何︰ 隐藏的文本，在提供支持传统语言服务 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "隐藏文本，支持"
  - "编辑器 [Visual Studio SDK]，隐藏文本"
  - "语言服务，实现隐藏的文本区域"
ms.assetid: 1c1dce9f-bbe2-4fc3-a736-5f78a237f4cc
caps.latest.revision: 21
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 21
---
# 如何︰ 隐藏的文本，在提供支持传统语言服务
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

除了大纲区域外，可以创建隐藏文本区域。  隐藏文本区域可以是客户端控件或编辑控件和使用完全隐藏文本区域。  编辑器将显示一个隐藏区域作为水平线。  此示例是在 HTML 编辑器中仅脚本视图。  
  
## 过程  
  
#### 实现一个隐藏文本区域  
  
1.  调用 <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>的 `QueryService` 。  
  
     这将返回指向 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>。  
  
2.  调用 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>，通过在给定文本缓冲区的指针。  这将确定一个隐藏文本会话是否用于缓冲区已经存在。  
  
3.  如果的已存在，则您不需要创建一个，并对现有 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> 对象的指针返回。  使用此指针枚举和创建隐藏文本区域。  否则，调用 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> 创建缓冲区的隐藏文本会话。  
  
     为 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> 对象的指针返回。  
  
    > [!NOTE]
    >  当您调用 `CreateHiddenTextSession`时，可以指定一个隐藏的文本客户端 \(即 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient>\)。  ，在隐藏的文本或概述由用户时，展开或折叠隐藏文本客户端通知您。  
  
4.  调用 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A> 一次添加一个或多个新的大纲区域，指定以下信息。 `reHidReg` \(<xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion>\) 参数:  
  
    1.  指定 `hrtConcealed` 的值。 <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> 结构的 `iType` 成员指示您创建一个隐藏的区域，而不是大纲区域。  
  
        > [!NOTE]
        >  当隐藏的区域隐藏时，编辑器将在隐藏的区域周围自动显示行指示它们是否存在。  
  
    2.  指定该区域是客户端控件或编辑控件在 <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> 结构的 `dwBehavior` 成员。  这次智能概述的实现可以包含编辑和客户端控件轮廓和隐藏文本区域的组合。