---
title: "使用旧版 API 自定义代码 Windows |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - code windows
ms.assetid: 5328ab2f-55cb-4680-9744-ec79f55acd1b
caps.latest.revision: "19"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4a958e6f6aa815b7d5726c2c441876331fba56b8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="customizing-code-windows-by-using-the-legacy-api"></a>通过使用旧版 API 的自定义代码窗口
代码窗口是支持一个或多个文本视图的文档窗口对象。 代码窗口的确切功能取决于关联的语言服务。 在多文档界面 (MDI) 模式下，代码窗口是 MDI 子框架。  
  
 由语言服务控制的代码窗口，每个语言服务可以提供其自己的代码窗口管理器。 这样，语言服务将其自己修饰添加到代码窗口中，如波形曲线、 着色、 和的详细信息。 有关如何创建核心窗口的详细信息，请参阅[实例化核心通过编辑器使用旧版 API](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)。  
  
 代码窗口是<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>具有文本视图和对象中放置任何修饰的对象。 语言服务在创建时代码窗口在核心您实例化期间编辑器，可以将附加<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>到代码窗口中，作为显示在下图中。  
  
 ![CodeWindow 图](../extensibility/media/vscodewindow.gif "vscodewindow")  
“代码”窗口  
  
 语言服务实现代码窗口管理器，并负责管理修饰，如下拉栏。 在代码窗口调用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A>在代码窗口初始化过程中的方法。 语言服务时进行此调用时，可以添加一个下拉栏或按钮栏 (<xref:Microsoft.VisualStudio.TextManager.Interop.IVsButtonBarClient>) 到代码窗口。  
  
## <a name="in-this-section"></a>本节内容  
 `Customizing Code Windows by Using the Legacy API`  
 介绍如何自定义代码窗口使用旧的 API。  
  
 [如何： 承载在其他编辑器中的编辑器](../extensibility/how-to-host-an-editor-in-another-editor.md)  
 说明如何托管在编辑器窗口内的第二个编辑器。  
  
 [如何： 触发事件; 当编辑器失去焦点](../extensibility/how-to-fire-events-when-the-editor-loses-focus.md)  
 说明如何将文档视图附加到文档数据对象。  
  
## <a name="see-also"></a>另请参阅  
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>   
 [使用旧版 API 实例化核心编辑器](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)   
 [通过使用旧版 API 访问文本视图](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)