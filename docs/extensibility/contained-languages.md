---
title: "包含的语言 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "编辑器 [Visual Studio SDK]，旧的包含语言"
ms.assetid: b75bbb51-8e42-41b1-bece-09ab0b1f03cc
caps.latest.revision: 18
caps.handback.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
---
# 包含的语言
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

*包含的语言* 由其他语言包含的语言。  例如，在 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 页的 HTML 可以包含 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 或 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 脚本。  双语言结构对于 .aspx 文件编辑所需的为 HTML 和这种脚本语言提供 IntelliSense、着色以及其他编辑功能。  
  
## 实现  
 您需要为包含的语言实现的最重要的接口是 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> 接口。  此接口由可承载在 PRIMARY LANGUAGE 内的任何语言实现。  它允许访问语言服务的 colorizer、文本视图筛选器和 PRIMARY LANGUAGE 服务标识符的访问  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory> 可以创建 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> 接口。  下面的步骤演示如何实现一种包含的语言:  
  
1.  使用 `QueryService()` 获取语言服务 ID 和 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory>的接口 ID。  
  
2.  调用 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory.GetLanguage%2A> 方法创建 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> 接口。  通过 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 接口、项 ID \(一个或多 <xref:Microsoft.VisualStudio.VSConstants.VSITEMID_NIL>、 <xref:Microsoft.VisualStudio.VSConstants.VSITEMID_ROOT>或 <xref:Microsoft.VisualStudio.VSConstants.VSITEMID_SELECTION>\) 和 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator> 接口。  
  
3.  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator> 接口，必须是文本缓冲区协调员对象，提供需要映射一个主文档的位置添加到辅助语言的缓冲区的基本服务。  
  
     例如，在一个 .aspx 文件，主文档包含 ASP、 HTML 和包含的任何代码。  但是，辅助缓冲区，用任何类定义一起包括包含的代码，，使辅助缓冲区有效的代码文件。  工作协调从一个缓冲区编辑到其他的缓冲区协调员处理。  
  
4.  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.SetSpanMappings%2A> 方法，该方法是 PRIMARY LANGUAGE，调用缓冲区协调员在其缓冲区中的哪些文本映射到辅助缓冲区的相应文本。  
  
     该语言在 <xref:Microsoft.VisualStudio.TextManager.Interop.NewSpanMapping> 结构数组传递，仅当前包括主和一个辅助范围。  
  
5.  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.MapPrimaryToSecondarySpan%2A> 方法和 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.MapSecondaryToPrimarySpan%2A> 方法提供用于从主到辅助缓冲区反之亦然。