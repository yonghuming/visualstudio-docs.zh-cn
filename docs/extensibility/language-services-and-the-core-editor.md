---
title: "语言服务和核心编辑器 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - language services
ms.assetid: e03199a6-ad5f-4075-bfba-8d36865112b7
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: c78c3c5e450ffe348a8af2687e2b9b30b1128e8e
ms.lasthandoff: 02/22/2017

---
# <a name="language-services-and-the-core-editor"></a>语言服务和核心编辑器
在 Visual Studio 中的编辑器是往往与语言服务。 除此之外，语言服务提供语法突出显示、 语句完成、 IntelliSense 和文本格式设置。  
  
## <a name="core-editors-and-document-data-objects"></a>核心编辑器和文档数据对象  
 当您访问核心编辑器时，您不会创建文档数据和文档视图对象。 IDE 创建和控制这两个对象，并通过工厂实现在您的编辑器中进行适当的调用获得它们的句柄。  
  
 有关详细信息，请参阅[确定哪种编辑器在项目中打开一个文件](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md)。  
  
## <a name="language-services-and-the-core-editor"></a>语言服务和核心编辑器  
 通过实现语言服务时，可以控制数据在文档视图中的显示方式。 语言服务提供的信息和特定于某种给定语言，如 Visual c + + 的行为。 当您创建文本缓冲区，并确定要打开的文档与文件扩展名时，文本缓冲区确定与从注册表项，HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Editors 此文件扩展名关联的语言服务\\{YourLanguageService GUID} \Extensions。 标准 VSPackage 加载过程，然后加载你的 VSPackage，并创建您的语言服务的实例。  
  
 基础语言服务是在下图中所示。  
  
 ![语言服务模型图](~/extensibility/media/vslanguageservicemodel.gif "vsLanguageServiceModel")  
核心编辑器和语言服务对象  
  
 核心编辑器文档的数据对象称为文本缓冲区，由表示<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>对象。</xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> 文档视图对象称为文本视图，由表示<xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>对象。</xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> 通过语言服务提供核心编辑器的统一的视图，这两个对象一起工作。 文本缓冲区和文档窗口中显示的文本视图中的信息称为代码窗口。 代码窗口文档由代码窗口管理器管理。  
  
## <a name="see-also"></a>另请参阅  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo></xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer></xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView></xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager></xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow></xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>   
 [提供通过使用旧 API 的语言服务上下文](../extensibility/providing-a-language-service-context-by-using-the-legacy-api.md)   
 [IntelliSense 承载](../extensibility/intellisense-hosting.md)   
 [包含的语言](../extensibility/contained-languages.md)   
 [开发旧语言服务](../extensibility/internals/developing-a-legacy-language-service.md)
