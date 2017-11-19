---
title: "演练： 显示语句结束 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], new - statement completion
ms.assetid: f3152c4e-7673-4047-a079-2326941d1c83
caps.latest.revision: "36"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7ebdc87e1dccf2bde66ccfeebb6c2b4fba144c70
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-displaying-statement-completion"></a>演练： 显示语句结束
你可以通过定义你想要提供完成的标识符，然后触发完成会话实现基于语言的语句结束。 你可以定义语言服务上下文中的语句完成、 定义你自己的文件扩展名和内容类型，然后显示完成只是该类型，或者可以触发完成现有内容类型 — 例如，"纯文本"。 本演练演示如何在触发"纯文本"内容类型，这是文本文件的内容类型的语句结束。 "Text"内容类型是所有其他内容类型，包括代码和 XML 文件的上级。  
  
 语句结束通常会触发通过键入某些字符-例如，通过键入如"using"标识符开头。 它通常通过按空格键、 选项卡上，或 Enter 键，以提交所选内容进行消失。 你可以实现触发通过击键是命令处理程序中键入字符的 IntelliSense 功能 (<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>接口) 和处理程序提供程序实现<xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>接口。 若要创建完成源，这是参与完成的标识符的列表，实现<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>接口和完成源提供程序 (<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider>接口)。 提供程序是 Managed Extensibility Framework (MEF) 组件部分。 他们负责导出的源和控制器类和导入服务和代理-例如， <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>，从而使文本缓冲区中的导航和<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>，随即将会触发完成会话。  
  
 本演练演示如何实现硬编码的一组标识符的语句结束。 在完整实现中，语言服务和语言文档是负责提供该内容。  
  
## <a name="prerequisites"></a>先决条件  
 从 Visual Studio 2015 开始，你并不安装 Visual Studio SDK 从下载中心。 它将包括作为 Visual Studio 安装程序中的可选功能。 你还可以在以后安装 VS SDK。 有关详细信息，请参阅[安装 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## <a name="creating-a-mef-project"></a>创建 MEF 项目  
  
#### <a name="to-create-a-mef-project"></a>创建 MEF 项目  
  
1.  创建 C# VSIX 项目。 (在**新项目**对话框中，选择**Visual C# / 可扩展性**，然后**VSIX 项目**。)将解决方案命名`CompletionTest`。  
  
2.  向项目添加编辑器分类器项模板。 有关详细信息，请参阅[带有编辑器项模板创建扩展](../extensibility/creating-an-extension-with-an-editor-item-template.md)。  
  
3.  删除现有的类文件。  
  
4.  添加以下引用到项目，并确保**CopyLocal**设置为`false`:  
  
     Microsoft.VisualStudio.Editor  
  
     Microsoft.VisualStudio.Language.Intellisense  
  
     Microsoft.VisualStudio.OLE.Interop  
  
     Microsoft.visualstudio.shell.14.0 的引用  
  
     Microsoft.VisualStudio.Shell.Immutable.10.0  
  
     Microsoft.VisualStudio.TextManager.Interop  
  
## <a name="implementing-the-completion-source"></a>实现完成源  
 完成源负责收集标识符集并将内容添加到完成窗口中，当用户键入了完成触发器，如标识符的第一个字母。 在此示例中，标识符和及其说明是硬编码在<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A>方法。 在大多数实际使用时，你将使用你的语言的分析器来获取令牌以填充完成列表。  
  
#### <a name="to-implement-the-completion-source"></a>若要实现完成源  
  
1.  添加一个类文件并将其命名`TestCompletionSource`。  
  
2.  添加这些导入：  
  
     [!code-csharp[VSSDKCompletionTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_1.cs)]
     [!code-vb[VSSDKCompletionTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_1.vb)]  
  
3.  修改的类声明`TestCompletionSource`，以便实现<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>:  
  
     [!code-csharp[VSSDKCompletionTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_2.cs)]
     [!code-vb[VSSDKCompletionTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_2.vb)]  
  
4.  源提供程序、 文本缓冲区中，和的列表添加私有字段<xref:Microsoft.VisualStudio.Language.Intellisense.Completion>（它们分别对应于将参与完成会话的标识符） 的对象：  
  
     [!code-csharp[VSSDKCompletionTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_3.cs)]
     [!code-vb[VSSDKCompletionTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_3.vb)]  
  
5.  添加设置的源提供程序和缓冲区的构造函数。 `TestCompletionSourceProvider`在后续步骤中定义类：  
  
     [!code-csharp[VSSDKCompletionTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_4.cs)]
     [!code-vb[VSSDKCompletionTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_4.vb)]  
  
6.  实现<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A>想要提供的上下文中通过添加包含完成的完成集的方法。 每个完成集包含一套<xref:Microsoft.VisualStudio.Language.Intellisense.Completion>完成，并且对应于完成窗口的选项卡。 (在 Visual Basic 项目中，完成窗口选项卡名为**常见**和**所有**。)FindTokenSpanAtPosition 方法是在下一步中定义的。  
  
     [!code-csharp[VSSDKCompletionTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_5.cs)]
     [!code-vb[VSSDKCompletionTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_5.vb)]  
  
7.  以下方法用于查找与光标的位置的当前单词：  
  
     [!code-csharp[VSSDKCompletionTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_6.cs)]
     [!code-vb[VSSDKCompletionTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_6.vb)]  
  
8.  实现`Dispose()`方法：  
  
     [!code-csharp[VSSDKCompletionTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_7.cs)]
     [!code-vb[VSSDKCompletionTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_7.vb)]  
  
## <a name="implementing-the-completion-source-provider"></a>实现完成源提供程序  
 完成源提供程序是完成源进行实例化的 MEF 组件部分。  
  
#### <a name="to-implement-the-completion-source-provider"></a>实现完成源提供程序  
  
1.  添加一个名为类`TestCompletionSourceProvider`实现<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider>。 导出此类的<xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>"纯文本"和<xref:Microsoft.VisualStudio.Utilities.NameAttribute>的"测试完成"。  
  
     [!code-csharp[VSSDKCompletionTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_8.cs)]
     [!code-vb[VSSDKCompletionTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_8.vb)]  
  
2.  导入<xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>，用于完成源中查找当前的单词。  
  
     [!code-csharp[VSSDKCompletionTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_9.cs)]
     [!code-vb[VSSDKCompletionTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_9.vb)]  
  
3.  实现<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider.TryCreateCompletionSource%2A>方法可实例化完成源。  
  
     [!code-csharp[VSSDKCompletionTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_10.cs)]
     [!code-vb[VSSDKCompletionTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_10.vb)]  
  
## <a name="implementing-the-completion-command-handler-provider"></a>实现完成命令处理程序提供程序  
 完成命令处理程序提供程序派生自<xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>，其侦听的文本视图创建事件，并将转换将视图从<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>-这可以添加到 Visual Studio shell 命令链命令-到<xref:Microsoft.VisualStudio.Text.Editor.ITextView>. 由于此类是 MEF 导出，还可以使用导入所需的命令处理程序本身的服务  
  
#### <a name="to-implement-the-completion-command-handler-provider"></a>实现完成命令处理程序提供程序  
  
1.  添加名为的文件`TestCompletionCommandHandler`。  
  
2.  添加以下 using 语句：  
  
     [!code-csharp[VSSDKCompletionTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_11.cs)]
     [!code-vb[VSSDKCompletionTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_11.vb)]  
  
3.  添加一个名为类`TestCompletionHandlerProvider`实现<xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>。 导出此类的<xref:Microsoft.VisualStudio.Utilities.NameAttribute>的"令牌完成处理程序" <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "纯文本"和<xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>的<xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Editable>。  
  
     [!code-csharp[VSSDKCompletionTest#12](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_12.cs)]
     [!code-vb[VSSDKCompletionTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_12.vb)]  
  
4.  导入<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>，从而使从转换<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>到<xref:Microsoft.VisualStudio.Text.Editor.ITextView>、 <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>，和一个<xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>，使用户可以访问标准 Visual Studio 服务。  
  
     [!code-csharp[VSSDKCompletionTest#13](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_13.cs)]
     [!code-vb[VSSDKCompletionTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_13.vb)]  
  
5.  实现<xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A>方法可实例化的命令处理程序。  
  
     [!code-csharp[VSSDKCompletionTest#14](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_14.cs)]
     [!code-vb[VSSDKCompletionTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_14.vb)]  
  
## <a name="implementing-the-completion-command-handler"></a>实现完成命令处理程序  
 因为通过击键触发语句结束时，则必须实现<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>接口来接收并处理触发、 提交和关闭完成会话的键击。  
  
#### <a name="to-implement-the-completion-command-handler"></a>若要实现完成命令处理程序  
  
1.  添加一个名为类`TestCompletionCommandHandler`实现<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>:  
  
     [!code-csharp[VSSDKCompletionTest#15](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_15.cs)]
     [!code-vb[VSSDKCompletionTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_15.vb)]  
  
2.  将私有字段 （向其传递的命令） 的下一步命令处理程序、 文本视图、 命令处理程序提供程序 （允许使用对各种服务的访问），添加和完成会话：  
  
     [!code-csharp[VSSDKCompletionTest#16](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_16.cs)]
     [!code-vb[VSSDKCompletionTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_16.vb)]  
  
3.  添加一个构造函数设置文本视图和提供程序字段中，并将该命令添加到命令链：  
  
     [!code-csharp[VSSDKCompletionTest#17](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_17.cs)]
     [!code-vb[VSSDKCompletionTest#17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_17.vb)]  
  
4.  实现<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>方法，从而将沿命令：  
  
     [!code-csharp[VSSDKCompletionTest#18](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_18.cs)]
     [!code-vb[VSSDKCompletionTest#18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_18.vb)]  
  
5.  实现 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> 方法。 当此方法接收击键时，它必须执行以下操作之一：  
  
    -   允许的字符写入缓冲区，然后触发或筛选完成。 （打印字符执行此操作。）  
  
    -   提交完成，但不是允许写入到缓冲区的字符。 （空格、 制表符和 Enter 执行此操作时显示完成会话。）  
  
    -   允许该命令传递到下一个处理程序。 （所有其他命令。）  
  
     由于此方法可能会显示用户界面，调用<xref:Microsoft.VisualStudio.Shell.VsShellUtilities.IsInAutomationFunction%2A>以确保它不调用自动化上下文中：  
  
     [!code-csharp[VSSDKCompletionTest#19](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_19.cs)]
     [!code-vb[VSSDKCompletionTest#19](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_19.vb)]  
  
6.  此代码是私有方法触发完成会话：  
  
     [!code-csharp[VSSDKCompletionTest#20](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_20.cs)]
     [!code-vb[VSSDKCompletionTest#20](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_20.vb)]  
  
7.  下一个示例是一个私有方法，向取消订阅<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSession.Dismissed>事件：  
  
     [!code-csharp[VSSDKCompletionTest#21](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_21.cs)]
     [!code-vb[VSSDKCompletionTest#21](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_21.vb)]  
  
## <a name="building-and-testing-the-code"></a>生成和测试代码  
 若要测试此代码，生成 CompletionTest 解决方案并在实验实例中运行它。  
  
#### <a name="to-build-and-test-the-completiontest-solution"></a>若要生成和测试 CompletionTest 解决方案  
  
1.  生成解决方案。  
  
2.  在调试器中运行此项目时，Visual Studio 的第二个实例将进行实例化。  
  
3.  创建一个文本文件，并键入一些文本，其中包括 word"添加"。  
  
4.  当您第一次键入"a"，然后"d"，应显示包含"添加"和"改写"的列表。 请注意，添加处于选中状态。 当你键入另一个"d"时，该列表应包含仅"添加"，现在处于选中状态。 可以通过按空格键、 Tab 或 Enter 键，提交"添加"，也可以通过键入 Esc 或按任意键关闭该列表。  
  
## <a name="see-also"></a>另请参阅  
 [演练：将内容类型链接到文件扩展名](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)