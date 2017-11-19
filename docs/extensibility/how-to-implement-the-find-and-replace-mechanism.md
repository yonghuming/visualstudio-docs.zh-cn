---
title: "如何： 实现查找和替换机制 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - find and replace
ms.assetid: bbd348db-3d19-42eb-99a2-3e808528c0ca
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8c12e300a3537d1927710b0a4c3550ec3f5fd762
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-implement-the-find-and-replace-mechanism"></a>如何： 实现查找和替换机制
Visual Studio 提供两种方法来实现查找/替换。 一种方法是将文本图像传递给命令行界面，并让它处理搜索、 突出显示，以及替换文本。 这样用户就可以指定多个文本范围。 或者，你的 VSPackage 可以控制此功能本身。 在这两种情况下必须通知有关的当前目标和所有打开的文档的目标 shell。  
  
### <a name="to-implement-findreplace"></a>若要实现查找/替换  
  
1.  实现<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>框架属性返回的对象之一上的接口<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>或<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>。 如果要创建自定义编辑器，则应实现此接口作为自定义编辑器类的一部分。  
  
2.  使用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetCapabilities%2A>方法来指定你的编辑器支持的选项，还可以指示是否实现文本映像搜索。  
  
     如果你的编辑器支持文本映像搜索，实现<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetSearchImage%2A>。  
  
     否则，实现<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A>和<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>。  
  
3.  如果你实现<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A>和<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>方法，你可以通过调用来简化你搜索的任务<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindHelper>接口。  
  
## <a name="see-also"></a>另请参阅  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindHelper>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetSearchImage%2A>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>