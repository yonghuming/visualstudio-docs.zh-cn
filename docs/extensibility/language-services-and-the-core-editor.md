---
title: "语言服务和核心编辑器 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - language services
ms.assetid: e03199a6-ad5f-4075-bfba-8d36865112b7
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1528bc685577082df997535a680c372620821de0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="language-services-and-the-core-editor"></a>语言服务和核心编辑器
Visual Studio 中的编辑器的经常与语言服务相关联。 除了别的之外语言服务提供了语法着色、 语句完成、 IntelliSense、 和文本格式设置。  
  
## <a name="core-editors-and-document-data-objects"></a>核心编辑器和文档数据对象  
 当访问核心编辑器时，你不要创建文档数据和文档视图对象。 IDE 创建和控制这两个对象，并通过在你的编辑器中工厂实现进行适当的调用中获取它们的句柄。  
  
 有关详细信息，请参阅[确定哪种编辑器在项目中打开文件](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md)。  
  
## <a name="language-services-and-the-core-editor"></a>语言服务和核心编辑器  
 通过实现语言服务时，可以控制如何在文档视图中显示的数据。 语言服务提供信息和特定于给定语言，如 Visual c + + 的行为。 当你创建文本缓冲区，并确定要打开的文档与文件扩展名时，文本缓冲区确定与从注册表项，HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Editors 此文件扩展名关联的语言服务\\{YourLanguageService GUID} \Extensions。 然后加载过程标准 VSPackage 加载你的 VSPackage，并创建语言服务的实例。  
  
 基本语言服务如下图所示。  
  
 ![语言服务模型图](../extensibility/media/vslanguageservicemodel.gif "vsLanguageServiceModel")  
核心编辑器和语言服务对象  
  
 核心编辑器文档数据对象称为文本缓冲区，由表示<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>对象。 文档视图对象称为文本视图，由表示<xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>对象。 通过语言服务以提供核心编辑器的统一的视图，这两个对象协同工作。 从文本缓冲区和文本视图显示在文档窗口中的信息调用代码窗口。 代码窗口文档由代码窗口管理器管理。  
  
## <a name="see-also"></a>另请参阅  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>   
 [通过使用旧版 API 提供的语言服务上下文](../extensibility/providing-a-language-service-context-by-using-the-legacy-api.md)   
 [IntelliSense 承载](../extensibility/intellisense-hosting.md)   
 [包含的语言](../extensibility/contained-languages.md)   
 [开发旧版语言服务](../extensibility/internals/developing-a-legacy-language-service.md)