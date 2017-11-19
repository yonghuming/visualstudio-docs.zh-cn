---
title: "演练： 显示签名帮助 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], new - signature help/parameter info
ms.assetid: 4a6a884b-5730-4b54-9264-99684f5b523c
caps.latest.revision: "28"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7078ee1e125ca11b0707b22b0d824cd0fc2d75b6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-displaying-signature-help"></a>演练： 显示签名帮助
签名帮助 (也称为*参数信息*) 用户键入的参数列表的起始字符 （通常是一个左括号） 时，将显示工具提示中的方法的签名。 参数和参数分隔符 （通常为逗号） 已类型化，工具提示会更新以显示下一个参数以粗体显示。 你可以定义签名帮助语言服务上下文中或可以定义你自己的文件名称扩展和内容类型，并显示只是该类型的签名帮助或可以为现有的内容类型 （例如，"文本"） 显示签名帮助。 本演练演示如何显示为"text"的内容类型的签名帮助。  
  
 签名帮助通常会触发通过键入特定字符，例如，"("（左括号），并通过键入另一个字符，例如，关闭")"（右括号）。 可以通过使用键击是命令处理程序实现触发通过键入字符的 IntelliSense 功能 (<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>接口) 和处理程序提供程序实现<xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>接口。 若要创建的签名帮助的源，这是参与签名帮助中的签名的列表，实现<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource>接口和实现的源提供程序<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider>接口。 提供程序个 Managed Extensibility Framework (MEF) 组件部分，以及负责导出的源和控制器类和导入服务和代理，例如， <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>，这样在文本缓冲区中，导航和<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker>，随即将会触发签名帮助会话。  
  
 本演练演示如何实现签名帮助硬编码的一组标识符。 在完整实现中，语言负责提供该内容。  
  
## <a name="prerequisites"></a>先决条件  
 从 Visual Studio 2015 开始，你并不安装 Visual Studio SDK 从下载中心。 它将包括作为 Visual Studio 安装程序中的可选功能。 你还可以在以后安装 VS SDK。 有关详细信息，请参阅[安装 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## <a name="creating-a-mef-project"></a>创建 MEF 项目  
  
#### <a name="to-create-a-mef-project"></a>创建 MEF 项目  
  
1.  创建 C# VSIX 项目。 (在**新项目**对话框中，选择**Visual C# / 可扩展性**，然后**VSIX 项目**。)将解决方案命名`SignatureHelpTest`。  
  
2.  向项目添加编辑器分类器项模板。 有关详细信息，请参阅[带有编辑器项模板创建扩展](../extensibility/creating-an-extension-with-an-editor-item-template.md)。  
  
3.  删除现有的类文件。  
  
4.  添加以下引用到项目中，并确保**CopyLocal**设置为`false`:  
  
     Microsoft.VisualStudio.Editor  
  
     Microsoft.VisualStudio.Language.Intellisense  
  
     Microsoft.VisualStudio.OLE.Interop  
  
     Microsoft.visualstudio.shell.14.0 的引用  
  
     Microsoft.VisualStudio.TextManager.Interop  
  
## <a name="implementing-signature-help-signatures-and-parameters"></a>实现签名帮助签名和参数  
 签名帮助源取决于实现的签名<xref:Microsoft.VisualStudio.Language.Intellisense.ISignature>，其中每个包含实现的参数<xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>。 在完整的实现中，将从语言文档，获取此信息，但在此示例中，签名是硬编码。  
  
#### <a name="to-implement-the-signature-help-signatures-and-parameters"></a>若要实现的签名帮助签名和参数  
  
1.  添加一个类文件并将其命名`SignatureHelpSource`。  
  
2.  添加以下导入。  
  
     [!code-vb[VSSDKSignatureHelpTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_1.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_1.cs)]  
  
3.  添加一个名为类`TestParameter`实现<xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>。  
  
     [!code-vb[VSSDKSignatureHelpTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_2.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_2.cs)]  
  
4.  添加设置所有属性的构造函数。  
  
     [!code-vb[VSSDKSignatureHelpTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_3.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_3.cs)]  
  
5.  添加的属性<xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>。  
  
     [!code-vb[VSSDKSignatureHelpTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_4.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_4.cs)]  
  
6.  添加一个名为类`TestSignature`实现<xref:Microsoft.VisualStudio.Language.Intellisense.ISignature>。  
  
     [!code-vb[VSSDKSignatureHelpTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_5.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_5.cs)]  
  
7.  添加一些私有字段。  
  
     [!code-vb[VSSDKSignatureHelpTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_6.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_6.cs)]  
  
8.  添加一个构造函数，将字段设置和订阅到<xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed>事件。  
  
     [!code-vb[VSSDKSignatureHelpTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_7.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_7.cs)]  
  
9. 声明`CurrentParameterChanged`事件。 在签名中的参数之一的用户填写时，引发此事件。  
  
     [!code-vb[VSSDKSignatureHelpTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_8.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_8.cs)]  
  
10. 实现<xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.CurrentParameter%2A>属性，以便它引发`CurrentParameterChanged`事件的属性值发生更改时。  
  
     [!code-vb[VSSDKSignatureHelpTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_9.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_9.cs)]  
  
11. 添加一个方法来引发`CurrentParameterChanged`事件。  
  
     [!code-vb[VSSDKSignatureHelpTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_10.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_10.cs)]  
  
12. 添加一个方法来通过比较中的逗号数计算当前参数<xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A>的数字签名中的逗号。  
  
     [!code-vb[VSSDKSignatureHelpTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_11.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_11.cs)]  
  
13. 添加事件处理程序<xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed>调用的事件`ComputeCurrentParameter()`方法。  
  
     [!code-vb[VSSDKSignatureHelpTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_12.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#12](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_12.cs)]  
  
14. 实现 <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A> 属性。 此属性保存<xref:Microsoft.VisualStudio.Text.ITrackingSpan>，它对应于签名应用到的缓冲区中的文本范围。  
  
     [!code-vb[VSSDKSignatureHelpTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_13.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#13](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_13.cs)]  
  
15. 实现其他参数。  
  
     [!code-vb[VSSDKSignatureHelpTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_14.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#14](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_14.cs)]  
  
## <a name="implementing-the-signature-help-source"></a>实现签名帮助源  
 签名帮助的源是为其提供信息的签名集。  
  
#### <a name="to-implement-the-signature-help-source"></a>若要实现的签名帮助源  
  
1.  添加一个名为类`TestSignatureHelpSource`实现<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource>。  
  
     [!code-vb[VSSDKSignatureHelpTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_15.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#15](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_15.cs)]  
  
2.  添加对文本缓冲区的引用。  
  
     [!code-vb[VSSDKSignatureHelpTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_16.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#16](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_16.cs)]  
  
3.  添加设置文本缓冲区和签名帮助源提供程序的构造函数。  
  
     [!code-vb[VSSDKSignatureHelpTest#17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_17.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#17](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_17.cs)]  
  
4.  实现 <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.AugmentSignatureHelpSession%2A> 方法。 在此示例中，签名是硬编码的但在完整的实现将从语言文档获取此信息。  
  
     [!code-vb[VSSDKSignatureHelpTest#18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_18.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#18](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_18.cs)]  
  
5.  帮助器方法`CreateSignature()`提供仅供阐释。  
  
     [!code-vb[VSSDKSignatureHelpTest#19](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_19.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#19](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_19.cs)]  
  
6.  实现 <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.GetBestMatch%2A> 方法。 在此示例中，有两个签名，其中每个具有两个参数。 因此，此方法不是必需的。 在更完整的实现中，在其中多个签名帮助源可用，此方法用于决定是否优先级最高的签名帮助源可以提供匹配的签名。 如果无法实现，该方法返回 null 并要求的下一步-优先级最高的源提供匹配项。  
  
     [!code-vb[VSSDKSignatureHelpTest#20](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_20.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#20](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_20.cs)]  
  
7.  实现 dispose （） 方法：  
  
     [!code-vb[VSSDKSignatureHelpTest#21](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_21.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#21](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_21.cs)]  
  
## <a name="implementing-the-signature-help-source-provider"></a>实现的签名帮助源提供程序  
 签名帮助源提供程序负责用于导出的 Managed Extensibility Framework (MEF) 组件部分并实例化的签名帮助的源。  
  
#### <a name="to-implement-the-signature-help-source-provider"></a>若要实现的签名帮助源提供程序  
  
1.  添加一个名为类`TestSignatureHelpSourceProvider`实现<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider>，并将其与导出<xref:Microsoft.VisualStudio.Utilities.NameAttribute>、 <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "text"和<xref:Microsoft.VisualStudio.Utilities.OrderAttribute>的 Before ="default"。  
  
     [!code-vb[VSSDKSignatureHelpTest#22](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_22.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#22](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_22.cs)]  
  
2.  实现<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider.TryCreateSignatureHelpSource%2A>方法是实例化`TestSignatureHelpSource`。  
  
     [!code-vb[VSSDKSignatureHelpTest#23](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_23.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#23](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_23.cs)]  
  
## <a name="implementing-the-command-handler"></a>实现命令处理程序  
 签名帮助通常会通过触发 (字符和已通过消除) 字符。 你可以通过实现处理这些击键<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>，以便它将触发当它收到的签名帮助的会话 (字符前面有一个已知的方法名称，并解除当它收到的会话) 字符。  
  
#### <a name="to-implement-the-command-handler"></a>若要实现的命令处理程序  
  
1.  添加一个名为类`TestSignatureHelpCommand`实现<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>。  
  
     [!code-vb[VSSDKSignatureHelpTest#24](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_24.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#24](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_24.cs)]  
  
2.  添加私有字段<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>适配器 （它可以用于将命令处理程序添加到的链的命令处理程序）、 文本视图、 签名帮助 broker 和会话， <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator>，接下来<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>。  
  
     [!code-vb[VSSDKSignatureHelpTest#25](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_25.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#25](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_25.cs)]  
  
3.  添加一个构造函数初始化这些字段以及用于将命令筛选器添加到命令链筛选器。  
  
     [!code-vb[VSSDKSignatureHelpTest#26](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_26.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#26](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_26.cs)]  
  
4.  实现<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A>方法来触发当命令筛选器收到的签名帮助的会话 (字符后之一已知的方法名称，并消除当它收到的会话) 字符会话时仍处于活动状态。 在所有情况下，该命令将转发。  
  
     [!code-vb[VSSDKSignatureHelpTest#27](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_27.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#27](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_27.cs)]  
  
5.  实现<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>方法，以便它始终将命令转发。  
  
     [!code-vb[VSSDKSignatureHelpTest#28](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_28.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#28](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_28.cs)]  
  
## <a name="implementing-the-signature-help-command-provider"></a>实现签名帮助命令提供程序  
 你可以通过实现提供签名帮助命令<xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>创建文本视图时实例化的命令处理程序。  
  
#### <a name="to-implement-the-signature-help-command-provider"></a>若要实现的签名帮助命令提供程序  
  
1.  添加一个名为类`TestSignatureHelpController`实现<xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>并将其与导出<xref:Microsoft.VisualStudio.Utilities.NameAttribute>， <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>，和<xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>。  
  
     [!code-vb[VSSDKSignatureHelpTest#29](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_29.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#29](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_29.cs)]  
  
2.  导入<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>(用于获取<xref:Microsoft.VisualStudio.Text.Editor.ITextView>、 给定<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>对象)，则<xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>（用来查找当前的单词），和<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker>（来触发签名帮助会话）。  
  
     [!code-vb[VSSDKSignatureHelpTest#30](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_30.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#30](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_30.cs)]  
  
3.  实现<xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A>方法是实例化的方法`TestSignatureCommandHandler`。  
  
     [!code-vb[VSSDKSignatureHelpTest#31](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_31.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#31](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_31.cs)]  
  
## <a name="building-and-testing-the-code"></a>生成和测试代码  
 若要测试此代码，生成 SignatureHelpTest 解决方案并在实验实例中运行它。  
  
#### <a name="to-build-and-test-the-signaturehelptest-solution"></a>若要生成和测试 SignatureHelpTest 解决方案  
  
1.  生成解决方案。  
  
2.  在调试器中运行此项目时，Visual Studio 的第二个实例将进行实例化。  
  
3.  创建文本文件和某些文本，其中包括 word"添加"的类型以及一个左括号。  
  
4.  键入左括号后，你应看到显示的两个签名列表的工具提示`add()`方法。  
  
## <a name="see-also"></a>另请参阅  
 [演练：将内容类型链接到文件扩展名](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)