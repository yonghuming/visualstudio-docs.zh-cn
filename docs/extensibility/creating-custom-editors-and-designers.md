---
title: "创建自定义编辑器和设计器 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "设计器 [Visual Studio SDK]"
  - "编辑器 [Visual Studio SDK]，自定义"
ms.assetid: b6a5e8b2-0ae1-4fc3-812d-09d40051b435
caps.latest.revision: 31
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 31
---
# 创建自定义编辑器和设计器
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Visual Studio 集成的开发环境 \(IDE\) 可以承载不同类型的编辑器:  
  
-   Visual Studio 核心编辑器  
  
-   自定义编辑器  
  
-   外部编辑器  
  
-   设计器  
  
 以下信息帮助您选择的编辑器所需的类型。  
  
## 类型的编辑器  
 有关 Visual Studio 核心编辑器的信息，请参阅 [扩展编辑器和语言服务](../extensibility/extending-the-editor-and-language-services.md)。  
  
##### 自定义编辑器  
 自定义编辑器是一种用于处理在特殊环境中。 例如，您可以创建其作用是读取并将数据写入到一个特定的存储库，例如 Microsoft Exchange 服务器的编辑器。 如果需要适用于仅您的项目类型的编辑器，或者如果您希望编辑器具有的只有几个特定命令，请选择自定义编辑器。 但是，请注意，用户将无法使用自定义编辑器来编辑标准 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 项目。  
  
 自定义编辑器可以使用编辑器工厂，并在注册表中添加关于编辑器的信息。 但是，与自定义编辑器关联的项目类型可以实例化中的其他方法的自定义编辑器。  
  
 自定义编辑器可用于在就地激活或简化嵌入实现视图。  
  
##### 外部编辑器  
 外部编辑器就是未集成到 Visual Studio 中，如 Microsoft Word、 记事本或 Microsoft FrontPage 的编辑器。 例如，要通过文本向其传递从你的 VSPackage 才，您可能调用此类编辑器。 外部编辑器自行注册，可以在 Visual Studio 外使用。 当调用外部编辑器，并嵌入的宿主窗口时，然后它显示在 IDE 的窗口中。 如果没有，则 IDE 将为其创建一个单独的窗口。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> 方法使用按设置文档的优先级 <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> 枚举。 如果 `DP_External` 指定值，可以通过外部编辑器打开该文件。  
  
## 编辑器设计决策  
 以下的设计问题将帮助您选择适合您的应用程序的最佳编辑器类型:  
  
-   将您的应用程序及其数据文件中是否保存? 如果它将在文件中保存其数据，它们将采用自定义或标准格式?  
  
     如果使用标准文件格式，除了你的项目的其他项目类型将能够打开并读取\/写入数据到它们。 如果您使用自定义文件格式，但是，您的项目类型将能够打开并读取\/写入数据到它们。  
  
     如果您的项目使用的文件，然后应该自定义标准编辑器。 如果您的项目不使用文件，但而是使用一个数据库或其他存储库中的项，则应创建自定义编辑器。  
  
-   您的编辑器是否需要承载 ActiveX 控件?  
  
     如果您的编辑器承载 ActiveX 控件，然后实现就地激活编辑器中，如中所述 [就地激活](../misc/in-place-activation.md)。 如果它不承载 ActiveX 控件，然后使用简化的嵌入编辑器中，或自定义 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 默认编辑器。  
  
-   将您的编辑器支持多个视图? 如果您希望您的编辑器的默认编辑器时要显示的视图，您必须支持多个视图。  
  
     如果您的编辑器需要同时支持多个视图，文档数据和编辑器的文档视图对象必须是单独的对象。 有关详细信息，请参阅[支持多个文档视图](../extensibility/supporting-multiple-document-views.md)。  
  
     如果您的编辑器支持多个视图，你是否打算使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 核心编辑器的文本缓冲区实现 \(<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> 对象\) 为您的文档数据对象? 也就是说，要支持您编辑器视图的并行使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 核心编辑器? 若要执行此操作的能力是窗体设计器的基础...  
  
-   如果您需要承载外部编辑器，可编辑器嵌入在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]?  
  
     如果它可以嵌入，应为外部编辑器创建宿主窗口，然后调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> 方法和组 <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> 枚举值到 `DP_External`。 如果不能嵌入编辑器，IDE 会自动为它创建一个单独的窗口。  
  
## 本节内容  
 [演练: 创建自定义编辑器](../extensibility/walkthrough-creating-a-custom-editor.md)  
 说明如何创建自定义编辑器。  
  
 [演练 ︰ 将功能添加到自定义编辑器](../extensibility/walkthrough-adding-features-to-a-custom-editor.md)  
 说明如何将功能添加到自定义编辑器。  
  
 [设计器的初始化和元数据配置](../extensibility/designer-initialization-and-metadata-configuration.md)  
 说明如何初始化设计器。  
  
 [向设计器提供撤消支持](../extensibility/supplying-undo-support-to-designers.md)  
 说明如何为设计器提供撤消支持。  
  
 [语法着色中自定义编辑器](../extensibility/syntax-coloring-in-custom-editors.md)  
 解释了语法突出显示在核心编辑器和自定义编辑器中的区别。  
  
 [文档数据和自定义编辑器中的文档视图](../extensibility/document-data-and-document-view-in-custom-editors.md)  
 说明如何实现自定义编辑器中的文档数据和文档视图。  
  
## 相关章节  
 [在编辑器中的旧接口](../extensibility/legacy-interfaces-in-the-editor.md)  
 说明如何通过传统的 API 访问核心编辑器。  
  
 [开发语言服务](../extensibility/internals/developing-a-legacy-language-service.md)  
 介绍如何实现语言服务。  
  
 [扩展 Visual Studio 的其他部分](../extensibility/extending-other-parts-of-visual-studio.md)  
 说明如何创建匹配的其余部分的 UI 元素 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。  
  
## 请参阅  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>