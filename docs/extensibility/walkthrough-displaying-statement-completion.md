---
title: "演练: 显示语句完成 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "编辑器 [Visual Studio SDK]，新的语句结束"
ms.assetid: f3152c4e-7673-4047-a079-2326941d1c83
caps.latest.revision: 36
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 36
---
# 演练: 显示语句完成
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可以通过定义您想要提供完成的标识符，然后触发完成会话实现基于语言的语句结束。 可以定义的语言服务上下文中的语句完成、 定义您自己的文件扩展名和内容类型并显示完成只是该类型，或者可以触发的现有内容类型完成 — 例如，"纯文本"。 本演练演示如何在触发的"纯文本"内容类型，它是文本文件的内容类型的语句结束。 "Text"内容类型是所有其他内容类型，包括代码和 XML 文件的祖先。  
  
 通过键入某些字符通常触发语句完成 — 例如，通过键入如"使用"标识符的开头。 它通常是通过按空格键、 Tab 或 Enter 键以提交所选内容来取消。 您可以实现由通过击键命令处理程序中键入一个字符触发的 IntelliSense 功能 \( <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 接口\) 和处理程序实现的提供程序 <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> 接口。 若要创建完成源时，这是参与完成的标识符的列表，实现 <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource> 接口和完成源提供程序 \( <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider> 接口\)。 提供程序是托管可扩展性框架 \(MEF\) 部件的组件。 他们负责导出的源和控制器类和导入服务和代理 — 例如， <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>, ，这样文本缓冲区中的导航和 <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>, ，这样触发完成会话。  
  
 本演练演示如何实现硬编码的一组标识符的语句结束。 在完全实现中，该语言服务和相应语言文档是负责提供该内容。  
  
## 系统必备  
 启动 Visual Studio 2015 中，您并不安装 Visual Studio SDK 从下载中心获得。 它将包括作为 Visual Studio 安装程序中的可选功能。 您还可以在以后安装 VS SDK。 有关详细信息，请参阅[安装 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## 创建 MEF 项目  
  
#### 创建 MEF 项目  
  
1.  创建 C\# VSIX 项目。 \(在 **新项目** 对话框中，选择 **Visual C\# \/ 可扩展性**, ，然后 **VSIX 项目**。\) 将解决方案命名 `CompletionTest`。  
  
2.  向项目添加编辑器分类器项模板。 有关详细信息，请参阅[在编辑器中的项模板创建扩展](../extensibility/creating-an-extension-with-an-editor-item-template.md)。  
  
3.  删除现有的类文件。  
  
4.  添加以下引用到项目并确保 **CopyLocal** 设置为 `false`:  
  
     Microsoft.VisualStudio.Editor  
  
     Microsoft.VisualStudio.Language.Intellisense  
  
     Microsoft.VisualStudio.OLE.Interop  
  
     Microsoft.VisualStudio.Shell.14.0  
  
     Microsoft.VisualStudio.Shell.Immutable.10.0  
  
     Microsoft.VisualStudio.TextManager.Interop  
  
## 实现完成源  
 完成源是负责收集组标识符，并将内容添加到完成窗口中，当用户键入完成触发器，如标识符的第一个字母。 在此示例中，标识符和及其说明是硬编码在 <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A> 方法。 在大多数实际使用时，你将使用您的语言分析器来获取令牌以填充的完成列表。  
  
#### 若要实现完成源  
  
1.  添加一个类文件并将其命名 `TestCompletionSource`。  
  
2.  添加这些导入:  
  
     [!code-cs[VSSDKCompletionTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_1.cs)]
     [!code-vb[VSSDKCompletionTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_1.vb)]  
  
3.  修改的类声明的 `TestCompletionSource` ，使其实现 <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>:  
  
     [!code-cs[VSSDKCompletionTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_2.cs)]
     [!code-vb[VSSDKCompletionTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_2.vb)]  
  
4.  源提供程序、 文本缓冲区中，和的列表添加私有字段 <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> 对象 \(分别对应于将参与完成会话的标识符\):  
  
     [!code-cs[VSSDKCompletionTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_3.cs)]
     [!code-vb[VSSDKCompletionTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_3.vb)]  
  
5.  添加设置的源提供程序和缓冲区的构造函数。`TestCompletionSourceProvider` 在后续步骤中定义类:  
  
     [!code-cs[VSSDKCompletionTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_4.cs)]
     [!code-vb[VSSDKCompletionTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_4.vb)]  
  
6.  实现 <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A> 您想要提供的上下文中通过添加包含补全选项一完成组的方法。 每个完成集包含一套 <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> 完成项，并对应于完成窗口中的选项卡。 \(在 Visual Basic 项目中，将完成窗口选项卡名为 **常见** 和 **所有**。\) FindTokenSpanAtPosition 方法是在下一步中定义的。  
  
     [!code-cs[VSSDKCompletionTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_5.cs)]
     [!code-vb[VSSDKCompletionTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_5.vb)]  
  
7.  下面的方法用于查找当前从游标的位置的单词:  
  
     [!code-cs[VSSDKCompletionTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_6.cs)]
     [!code-vb[VSSDKCompletionTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_6.vb)]  
  
8.  实现 `Dispose()` 方法:  
  
     [!code-cs[VSSDKCompletionTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_7.cs)]
     [!code-vb[VSSDKCompletionTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_7.vb)]  
  
## 实现完成源提供程序  
 完成源提供程序完成源进行实例化的 MEF 组件部分。  
  
#### 若要实现完成源提供程序  
  
1.  添加一个名为类 `TestCompletionSourceProvider` 实现 <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider>。 导出此类的 <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "纯文本"和一个 <xref:Microsoft.VisualStudio.Utilities.NameAttribute> 的"测试完成"。  
  
     [!code-cs[VSSDKCompletionTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_8.cs)]
     [!code-vb[VSSDKCompletionTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_8.vb)]  
  
2.  导入 <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>, ，它用于完成源中查找当前的单词。  
  
     [!code-cs[VSSDKCompletionTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_9.cs)]
     [!code-vb[VSSDKCompletionTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_9.vb)]  
  
3.  实现 <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider.TryCreateCompletionSource%2A> 方法来实例化完成源。  
  
     [!code-cs[VSSDKCompletionTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_10.cs)]
     [!code-vb[VSSDKCompletionTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_10.vb)]  
  
## 实现完成命令处理程序提供程序  
 完成命令处理程序提供程序派生自 <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>, ，它侦听文本视图创建事件，并将转换将视图从 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>— 这样添加到 Visual Studio shell 命令链命令 — 到 <xref:Microsoft.VisualStudio.Text.Editor.ITextView>。 由于此类是 MEF 导出，还可以使用导入所需的命令处理程序本身的服务  
  
#### 若要实现完成命令处理程序提供程序  
  
1.  添加一个名为文件 `TestCompletionCommandHandler`。  
  
2.  添加以下 using 语句:  
  
     [!code-cs[VSSDKCompletionTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_11.cs)]
     [!code-vb[VSSDKCompletionTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_11.vb)]  
  
3.  添加一个名为类 `TestCompletionHandlerProvider` 实现 <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>。 导出此类的 <xref:Microsoft.VisualStudio.Utilities.NameAttribute> 的"令牌完成处理程序" <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "纯文本"和一个 <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> 的 <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Editable>。  
  
     [!code-cs[VSSDKCompletionTest#12](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_12.cs)]
     [!code-vb[VSSDKCompletionTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_12.vb)]  
  
4.  导入 <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>, ，这样从转换 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 到 <xref:Microsoft.VisualStudio.Text.Editor.ITextView>, 、 <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>, ，和一个 <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> ，使用户可以访问 Visual Studio 的标准服务。  
  
     [!code-cs[VSSDKCompletionTest#13](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_13.cs)]
     [!code-vb[VSSDKCompletionTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_13.vb)]  
  
5.  实现 <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A> 方法来实例化的命令处理程序。  
  
     [!code-cs[VSSDKCompletionTest#14](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_14.cs)]
     [!code-vb[VSSDKCompletionTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_14.vb)]  
  
## 实现完成命令处理程序  
 由于按键触发语句完成时，您必须实现 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 接口来接收并处理触发、 提交和关闭完成会话的键击。  
  
#### 若要实现完成命令处理程序  
  
1.  添加一个名为类 `TestCompletionCommandHandler` 实现 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>:  
  
     [!code-cs[VSSDKCompletionTest#15](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_15.cs)]
     [!code-vb[VSSDKCompletionTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_15.vb)]  
  
2.  添加私有字段 \(向其传递的命令\) 的下一个命令处理程序、 文本视图、 命令处理程序提供程序 \(可启用对各种服务的访问\)，并完成会话:  
  
     [!code-cs[VSSDKCompletionTest#16](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_16.cs)]
     [!code-vb[VSSDKCompletionTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_16.vb)]  
  
3.  添加一个构造函数设置的文本视图和提供程序字段中，并会将命令添加到命令链:  
  
     [!code-cs[VSSDKCompletionTest#17](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_17.cs)]
     [!code-vb[VSSDKCompletionTest#17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_17.vb)]  
  
4.  实现 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> 通过将命令传递给传递方法:  
  
     [!code-cs[VSSDKCompletionTest#18](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_18.cs)]
     [!code-vb[VSSDKCompletionTest#18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_18.vb)]  
  
5.  实现 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> 方法。 当此方法接收一个键击时，它必须执行以下操作之一:  
  
    -   允许的字符写入到缓冲区中，然后触发或筛选完成。 \(打印字符这么做。\)  
  
    -   提交完成时，但不是允许向缓冲区写入字符。 \(空格、 制表符和 enter 键执行此操作显示完成会话时。\)  
  
    -   允许该命令将在传递给下一个处理程序。 \(所有其他命令。\)  
  
     由于此方法可能会显示用户界面，因此调用 <xref:Microsoft.VisualStudio.Shell.VsShellUtilities.IsInAutomationFunction%2A> 以确保它不调用上下文中的自动化:  
  
     [!code-cs[VSSDKCompletionTest#19](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_19.cs)]
     [!code-vb[VSSDKCompletionTest#19](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_19.vb)]  
  
6.  此代码是一个触发器完成会话的私有方法:  
  
     [!code-cs[VSSDKCompletionTest#20](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_20.cs)]
     [!code-vb[VSSDKCompletionTest#20](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_20.vb)]  
  
7.  下一个示例是取消订阅中的私有方法 <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSession.Dismissed> 事件:  
  
     [!code-cs[VSSDKCompletionTest#21](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_21.cs)]
     [!code-vb[VSSDKCompletionTest#21](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_21.vb)]  
  
## 生成和测试代码  
 若要测试此代码，生成 CompletionTest 解决方案并在实验实例中运行它。  
  
#### 若要生成并测试 CompletionTest 解决方案  
  
1.  生成解决方案。  
  
2.  在调试器中运行此项目时，Visual Studio 的第二个实例将进行实例化。  
  
3.  创建一个文本文件，并键入一些文本，其中包括单词"添加"。  
  
4.  当您第一次键入"a"，然后"d"，应显示列表，其中包含"加法"和"改写"。 请注意，加法处于选中状态。 当您键入另一个"d"时，此列表应该包含仅"加法"，它们现在处于选中状态。 您可以通过按空格键、 Tab 或 Enter 键，提交"加法"，或通过键入 Esc 或按任意键关闭该列表。  
  
## 请参阅  
 [演练: 将内容类型链接到的文件扩展名](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)