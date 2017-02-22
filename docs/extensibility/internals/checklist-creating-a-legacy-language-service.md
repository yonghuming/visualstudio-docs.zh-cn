---
title: "清单︰ 创建传统语言服务 | Microsoft Docs"
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
  - "语言服务"
  - "语言服务，本机代码"
ms.assetid: 8b73b341-a33a-4ab5-9390-178c9e563d2d
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# 清单︰ 创建传统语言服务
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

以下检查表摘要必须花费创建 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 核心编辑器的语言服务的基本步骤。  若要集成语言服务 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]，必须创建调试表达式计算器。  有关更多信息，请参见中 [Visual Studio 调试器可扩展性](../../extensibility/debugger/visual-studio-debugger-extensibility.md)的 [编写 CLR 表达式计算器](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md) 。  
  
## 创建的语言服务步骤  
  
1.  实现 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> 接口。  
  
    -   在 VSPackage 中，请实现 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> 接口提供语言服务。  
  
    -   将语言服务可供集成 \(IDE\)开发环境。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> 实现。  
  
2.  实现在主语言服务类的 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> 接口。  
  
     <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> 接口是的核心编辑器和语言服务之间的交互。  
  
### 可选功能  
 以下功能是可选的，可以按任意顺序实现。  这些功能增加语言服务的功能。  
  
-   语法着色  
  
     实现 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> 接口。  此接口的实现如果返回分析器的信息适当的颜色信息。  
  
     <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> 方法返回 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> 接口。  单独 colorizer 实例为每个文本缓冲区中创建，因此，应单独实现 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> 接口。  有关更多信息，请参见 [语法着色在传统语言服务](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)。  
  
-   代码窗口  
  
     ，在新代码组窗口中创建，则实现 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> 接口允许语言服务接收通知。  
  
     <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> 方法返回 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> 接口。  语言服务可以添加特殊 UI 到 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A>的代码窗口。  语言服务还可以执行任何特殊处理，如添加到 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.OnNewView%2A>的一个文本视图筛选器。  
  
-   text " 视图筛选器  
  
     若要提供 IntelliSense 语句完成语言服务，您必须截获某些命令文本视图原本处理。  若要截获这些命令，请完成以下步骤:  
  
    -   实现 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 参与命令字符串和处理编辑器顺序。  
  
    -   调用 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> 方法并传入 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 实现。  
  
    -   调用 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.RemoveCommandFilter%2A> 方法，当从视图时分离，以便这些命令不再传递给您。  
  
     必须处理的命令取决于提供的服务。  有关更多信息，请参见 [重要的语言服务筛选器的命令](../../extensibility/internals/important-commands-for-language-service-filters.md)。  
  
    > [!NOTE]
    >  在对象必须实现 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> 接口和 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 接口相同。  
  
-   语句结束  
  
     实现 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> 接口。  
  
     支持语句完成订单 \(即 <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>\) 并调用 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 接口的 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> 方法，通过 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> 接口。  有关更多信息，请参见 [传统语言服务中的语句结束](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md)。  
  
-   方法提示  
  
     实现 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> 接口的方法提示窗口提供数据。  
  
     正确安装文本视图筛选器将处理命令，因此，您知道何时显示方法数据提示窗口。  有关更多信息，请参见 [传统语言服务中的参数信息](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)。  
  
-   错误标记  
  
     实现 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> 接口。  
  
     创建实现 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> 接口并调用 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> 方法是错误的标记对象，通过错误标记对象的 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> 接口。  
  
     通常每个错误标记管理中的项任务列表 " 窗口。  
  
-   任务列表项  
  
     实现提供 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskItem> 接口的任务项类。  
  
     实现提供 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider> 接口和 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider2> 接口的任务提供程序类。  
  
     实现提供 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumTaskItems> 接口的任务枚举器类。  
  
     注册任务列表的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.RegisterTaskProvider%2A> 方法的任务提供程序。  
  
     通过调用语言服务的服务提供程序中获取 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList> 接口与服务 GUID <xref:Microsoft.VisualStudio.Shell.Interop.SVsTaskList>。  
  
     ，当具有新功能或更新任务时，请创建任务项对象并调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList> 接口的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.RefreshTasks%2A> 方法。  
  
-   注释任务项  
  
     使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo> 接口和 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumCommentTaskTokens> 接口获取注释任务标记。  
  
     从 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTaskList> 服务的一 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo> 接口。  
  
     从 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo.EnumTokens%2A> 方法的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumCommentTaskTokens> 接口。  
  
     实现接口 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskListEvents> 侦听该标记中的更改列表。  
  
-   大纲显示  
  
     具有支持大纲显示的若干选项。  例如，可以支持 **折叠到定义** 命令，提供编辑控件轮廓区域或支持客户端控件区域。  有关更多信息，请参见 [如何︰ 提供旧语言服务中的扩展大纲显示支持](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)。  
  
-   语言服务注册  
  
     有关注册语言服务的更多信息，请参见 [注册早期语言服务](../../extensibility/internals/registering-a-legacy-language-service2.md) 和 [管理 Vspackage](../../extensibility/managing-vspackages.md)。  
  
-   区分上下文的帮助  
  
     提供上下文到编辑器以下列方式之一:  
  
    -   提供文本标记提供上下文通过实现 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> 接口。  
  
 通过实现 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider> 接口提供所有用户上下文。  
  
## 请参阅  
 [开发语言服务](../../extensibility/internals/developing-a-legacy-language-service.md)   
 [编写 CLR 表达式计算器](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)