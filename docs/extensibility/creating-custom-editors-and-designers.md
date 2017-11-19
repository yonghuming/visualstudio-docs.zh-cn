---
title: "创建自定义编辑器和设计器 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- designers [Visual Studio SDK]
- editors [Visual Studio SDK], custom
ms.assetid: b6a5e8b2-0ae1-4fc3-812d-09d40051b435
caps.latest.revision: "31"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 149870d9c9a0a281cb0bba167496cc4c37d6f83a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="creating-custom-editors-and-designers"></a>创建自定义编辑器和设计器
Visual Studio 集成的开发环境 (IDE) 可以托管不同类型的编辑器：  
  
-   Visual Studio 核心编辑器  
  
-   自定义编辑器  
  
-   外部编辑器  
  
-   设计器  
  
 以下信息可帮助你选择的编辑器，你需要的类型。  
  
## <a name="types-of-editor"></a>类型的编辑器  
 有关 Visual Studio 核心编辑器的信息，请参阅[扩展编辑器和语言服务](../extensibility/extending-the-editor-and-language-services.md)。  
  
##### <a name="custom-editors"></a>自定义编辑器  
 自定义编辑器是指用于在专用的情况下处理。 例如，你可能创建其作用是读取并将数据写入到一个特定的存储库，例如 Microsoft Exchange server 的编辑器。 如果想要一个编辑器，适用于仅您的项目类型，或如果您希望编辑器具有只有几个特定命令，请选择自定义编辑器。 但请注意，用户将无法使用自定义编辑器来编辑标准[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]项目。  
  
 自定义编辑器可以使用的编辑器工厂，并向注册表添加关于编辑器的信息。 但是，与自定义编辑器关联的项目类型可以实例化中的其他方法的自定义编辑器。  
  
 自定义编辑器可以使用就地激活或简化嵌入实现视图。  
  
##### <a name="external-editors"></a>外部编辑器  
 外部编辑器的未集成到 Visual Studio 中，如 Microsoft Word、 记事本或 Microsoft FrontPage 的编辑器。 如果，例如，您要传递文本到它从你的 VSPackage，你可能会调用此类编辑器。 外部编辑器将其本身注册和可以用在 Visual Studio 外。 当调用外部的编辑器中，并且它可以嵌入到主机窗口时，然后它显示在 IDE 中的窗口。 如果没有，则 IDE 将为其创建一个单独的窗口。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>方法使用按设置文档的优先级<xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY>枚举。 如果`DP_External`指定值，可以通过外部编辑器打开该文件。  
  
## <a name="editor-design-decisions"></a>编辑器设计决策  
 以下的设计问题将帮助你进行选择的编辑器最佳适合你的应用程序的类型：  
  
-   将你的应用程序及其数据在文件中是否保存？ 如果它会将其数据保存在文件中，它们将采用自定义或标准格式？  
  
     如果使用标准文件格式，除了你的项目的其他项目类型将能够打开和读/写数据到它们。 如果你使用自定义文件格式，但是，你的项目类型将能够打开和读/写数据到它们。  
  
     如果你的项目使用文件，然后你应该自定义标准编辑器。 如果你的项目不使用文件，但而是使用数据库或其他存储库中的项，则应创建自定义编辑器。  
  
-   你的编辑器是否需要承载 ActiveX 控件？  
  
     如果你的编辑器托管了 ActiveX 控件，然后实现就地激活编辑器中所述[就地激活](../extensibility/in-place-activation.md)。 如果它未承载 ActiveX 控件，然后使用简化的嵌入编辑器中，或自定义[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]默认编辑器。  
  
-   将你的编辑器支持多个视图？ 如果您希望您的编辑器的默认编辑器时要显示的视图，你必须支持多个视图。  
  
     如果你的编辑器需要支持多个视图，文档数据和编辑器的文档视图对象必须是单独的对象。 有关详细信息，请参阅[支持多个文档视图](../extensibility/supporting-multiple-document-views.md)。  
  
     如果你的编辑器支持多个视图，你是否打算使用[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]核心编辑器的文本缓冲区实现 (<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>对象) 为你的文档数据对象？ 要在即支持你编辑器视图的并行与[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]核心编辑器？ 若要执行此操作的能力是窗体设计器的基础...  
  
-   如果您需要承载外部编辑器，可编辑器嵌入在[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]？  
  
     如果它可以嵌入，应为外部编辑器创建一个主机窗口，然后调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>方法和组<xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY>枚举值到`DP_External`。 如果不能嵌入编辑器，则 IDE 将自动为其创建单独的窗口。  
  
## <a name="in-this-section"></a>本节内容  
 [演练：创建自定义编辑器](../extensibility/walkthrough-creating-a-custom-editor.md)  
 说明如何创建自定义编辑器。  
  
 [演练：在自定义编辑器中添加功能](../extensibility/walkthrough-adding-features-to-a-custom-editor.md)  
 说明如何将功能添加到自定义编辑器。  
  
 [设计器初始化和元数据配置](../extensibility/designer-initialization-and-metadata-configuration.md)  
 说明如何初始化设计器。  
  
 [向设计器提供撤消支持](../extensibility/supplying-undo-support-to-designers.md)  
 说明如何为设计器提供撤消支持。  
  
 [自定义编辑器中的语法着色](../extensibility/syntax-coloring-in-custom-editors.md)  
 说明语法颜色设置和自定义编辑器中核心编辑器之间的差异。  
  
 [自定义编辑器中的文档数据和文档视图](../extensibility/document-data-and-document-view-in-custom-editors.md)  
 介绍如何实现自定义编辑器中的文档数据和文档视图。  
  
## <a name="related-sections"></a>相关章节  
 [在编辑器中的旧接口](../extensibility/legacy-interfaces-in-the-editor.md)  
 说明如何通过旧版 API 访问核心编辑器。  
  
 [开发旧版语言服务](../extensibility/internals/developing-a-legacy-language-service.md)  
 介绍如何实现语言服务。  
  
 [扩展 Visual Studio 的其他部分](../extensibility/extending-other-parts-of-visual-studio.md)  
 说明如何创建匹配的其余部分的 UI 元素[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。  
  
## <a name="see-also"></a>另请参阅  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>