---
title: "清单： 创建旧语言服务 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- language services
- language services, native code
ms.assetid: 8b73b341-a33a-4ab5-9390-178c9e563d2d
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5c06d246f7467e19969075537f321061463d1755
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="checklist-creating-a-legacy-language-service"></a>清单： 创建旧语言服务
以下清单汇总了你必须接受以创建语言服务有关的基本步骤[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]核心编辑器。 若要将集成到你语言服务[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]，必须创建调试表达式计算器。 有关详细信息，请参阅[编写 CLR 表达式计算器](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)中[Visual Studio 调试器扩展性](../../extensibility/debugger/visual-studio-debugger-extensibility.md)。  
  
## <a name="steps-for-creating-a-language-service"></a>创建语言服务的步骤  
  
1.  实现 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> 接口。  
  
    -   在你的 VSPackage，实现<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>接口，以提供语言服务。  
  
    -   集成的开发环境 (IDE) 中提供语言服务你<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>实现。  
  
2.  实现<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>主要语言服务类中的接口。  
  
     <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>接口是核心编辑器和语言服务之间的交互的起始点。  
  
### <a name="optional-features"></a>可选功能  
 以下功能是可选的并且可以按任意顺序实现。 这些功能增加了语言服务的功能。  
  
-   语法着色  
  
     实现 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> 接口。 此接口的实现应返回适当的颜色信息的分析器信息。  
  
     <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A>方法返回<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>接口。 单独的着色器创建的实例为每个文本缓冲区，因此应实现<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>单独接口。 有关详细信息，请参阅[语法突出显示在旧语言服务](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)。  
  
-   “代码”窗口  
  
     实现<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>界面，以启用到语言服务以接收通知的时创建一个新的代码窗口。  
  
     <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A>方法返回<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>接口。 语言服务然后到代码窗口中添加特殊 UI <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A>。 语言服务还可以执行任何特殊处理，例如添加中的文本视图筛选器<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.OnNewView%2A>。  
  
-   文本视图筛选器  
  
     若要提供语言服务中的 IntelliSense 语句结束功能，必须截获某些文本视图将否则处理命令。 若要截获这些命令，请完成以下步骤：  
  
    -   实现<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>参与命令链和句柄编辑器命令。  
  
    -   调用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>方法并传入你<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>实现。  
  
    -   调用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.RemoveCommandFilter%2A>方法时，以便这些命令不会再传递到你从视图分离。  
  
     必须处理的命令取决于提供服务。 有关详细信息，请参阅[语言服务筛选器的重要命令](../../extensibility/internals/important-commands-for-language-service-filters.md)。  
  
    > [!NOTE]
    >  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>必须在与相同的对象上实现接口<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>接口。  
  
-   语句结束  
  
     实现 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> 接口。  
  
     支持的语句完成命令 (即， <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>) 并调用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A>中的方法<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>接口，将传递<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>接口。 有关详细信息，请参阅[旧语言服务中的语句结束](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md)。  
  
-   方法提示  
  
     实现<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>接口方法提示窗口中提供数据。  
  
     安装文本视图筛选器以适当地处理命令，以便知道何时显示方法数据提示窗口。 有关详细信息，请参阅[参数信息，请参阅旧语言服务](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)。  
  
-   错误标记  
  
     实现 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> 接口。  
  
     创建实现的标记对象的错误<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>接口并调用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A>方法，并传递<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>错误标记对象的接口。  
  
     通常，每个错误标记管理任务列表窗口中的项。  
  
-   任务列表项  
  
     实现任务项类提供<xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskItem>接口。  
  
     实现任务提供程序类提供<xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider>接口和<xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider2>接口。  
  
     实现任务枚举器类提供<xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumTaskItems>接口。  
  
     任务提供程序注册任务列表<xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.RegisterTaskProvider%2A>方法。  
  
     获取<xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList>接口通过调用服务 GUID 语言服务的服务提供商<xref:Microsoft.VisualStudio.Shell.Interop.SVsTaskList>。  
  
     创建任务项对象并调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.RefreshTasks%2A>中的方法<xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList>接口时有新或更新任务。  
  
-   注释任务项  
  
     使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo>接口和<xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumCommentTaskTokens>接口，以获得任务标记的注释。  
  
     获取<xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo>接口从<xref:Microsoft.VisualStudio.Shell.Interop.SVsTaskList>服务。  
  
     获取<xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumCommentTaskTokens>接口从<xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo.EnumTokens%2A>方法。  
  
     实现<xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskListEvents>接口来侦听令牌列表中的更改。  
  
-   大纲显示  
  
     有几个选项用于支持以大纲方式显示。 例如，可以支持**折叠到定义**命令，提供控制编辑器的大纲区域，也支持客户端控制区域。 有关详细信息，请参阅[如何： 提供扩展以大纲方式显示中的支持旧语言服务](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)。  
  
-   语言服务注册  
  
     有关如何注册语言服务的详细信息，请参阅[注册旧语言服务](../../extensibility/internals/registering-a-legacy-language-service2.md)和[管理 Vspackage](../../extensibility/managing-vspackages.md)。  
  
-   上下文相关帮助  
  
     通过以下方式之一提供到编辑器的上下文：  
  
    -   通过实现为文本标记中提供的上下文<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider>接口。  
  
 通过实现提供所有的用户上下文<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider>接口。  
  
## <a name="see-also"></a>另请参阅  
 [开发旧语言服务](../../extensibility/internals/developing-a-legacy-language-service.md)   
 [编写 CLR 表达式计算器](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)