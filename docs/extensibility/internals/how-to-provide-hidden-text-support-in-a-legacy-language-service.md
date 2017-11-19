---
title: "如何： 隐藏的文本在提供支持，旧语言服务 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- hidden text, supporting
- editors [Visual Studio SDK], hidden text
- language services, implementing hidden text regions
ms.assetid: 1c1dce9f-bbe2-4fc3-a736-5f78a237f4cc
caps.latest.revision: "21"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f7aab5978d2fc5f7bee82b097ed61a9603d7e198
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-provide-hidden-text-support-in-a-legacy-language-service"></a>如何： 隐藏的文本在提供支持，旧语言服务
你可以创建隐藏的文本区域除了大纲区域。 隐藏的文本区域可以是客户端控制或编辑器控制和用于完全隐藏的文本区域。 编辑器将显示为水平线条的隐藏的区域。 此示例是在 HTML 编辑器中的仅限脚本视图。  
  
## <a name="procedure"></a>过程  
  
#### <a name="to-implement-a-hidden-text-region"></a>若要实现的隐藏的文本区域  
  
1.  调用`QueryService`为<xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>。  
  
     这将返回一个指向<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>。  
  
2.  调用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>，并传入给定的文本缓冲区的指针。 这将确定是否隐藏的文本会话已存在缓冲区。  
  
3.  如果已存在，则不需要创建一个，到现有指针<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>返回对象。 此指针可用于枚举和创建隐藏的文本区域。 否则，调用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A>创建隐藏的文本会话缓冲区。  
  
     指向的指针<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>返回对象。  
  
    > [!NOTE]
    >  当调用`CreateHiddenTextSession`，你可以指定隐藏的文本客户端 (即， <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient>)。 隐藏的文本客户端会通知你时隐藏的文本或以大纲方式显示是展开还是折叠的用户。  
  
4.  调用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A>以添加一个或多新大纲区域一次，指定以下信息在`reHidReg`(<xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion>) 参数：  
  
    1.  指定的值`hrtConcealed`中`iType`的成员<xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion>结构以指示您要创建的隐藏的区域，而不是大纲区域。  
  
        > [!NOTE]
        >  隐藏隐匿的区域后，编辑器会自动显示为了指明其状态的隐藏区域周围的行。  
  
    2.  指定区域是客户端控制或在编辑器控制`dwBehavior`的成员<xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion>结构。 智能大纲显示实现可以包含多种编辑器和客户端控制大纲和隐藏的文本区域。