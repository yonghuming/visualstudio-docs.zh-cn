---
title: "演练︰ 显示签名帮助 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "编辑器 [Visual Studio SDK]，新的签名帮助/参数信息"
ms.assetid: 4a6a884b-5730-4b54-9264-99684f5b523c
caps.latest.revision: 28
caps.handback.revision: 28
ms.author: "gregvanl"
manager: "ghogen"
---
# 演练︰ 显示签名帮助
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

签名帮助 \(也称为 *参数信息*\) 用户键入的参数列表开始字符 （通常是一个左括号） 时，工具提示中显示的方法的签名。 键入的参数和参数分隔符 （通常为逗号），工具提示将更新以显示下一个参数以粗体显示。 可以在语言服务的上下文中定义签名帮助或可以定义你自己的文件名称扩展和内容类型和显示签名帮助只是该类型，也可以为现有内容类型 \(例如，"text"\) 显示签名帮助。 本演练演示如何显示为"text"内容类型的签名帮助。  
  
 通过键入特定字符通常触发签名帮助"\("（左括号），并通过键入另一个字符，例如，关闭"\)"（右括号）。 可通过击键命令处理程序实现触发通过输入字符的智能感知功能 \( <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 接口\) 和处理程序实现的提供程序 <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> 接口。 若要创建签名帮助源，是签名的签名帮助参与的列表，实现 <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource> 接口和源提供程序实现 <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider> 接口。 提供程序是部件的 Managed Extensibility Framework \(MEF\) 组件，并负责导出的源和控制器类和服务和分销商，例如，导入 <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>, ，这样文本缓冲区中导航和 <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker>, ，这样触发签名帮助会话。  
  
 本演练演示如何为硬编码的一组标识符实现签名帮助。 在完整的实现，该语言是负责提供该内容。  
  
## 系统必备  
 启动 Visual Studio 2015 中，您并不安装 Visual Studio SDK 从下载中心获得。 它将包括作为 Visual Studio 安装程序中的可选功能。 您还可以在以后安装 VS SDK。 有关详细信息，请参阅[安装 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## 创建 MEF 项目  
  
#### 创建 MEF 项目  
  
1.  创建 C\# VSIX 项目。 \(在 **新项目** 对话框中，选择 **Visual C\# \/ 可扩展性**, ，然后 **VSIX 项目**。\) 将解决方案命名 `SignatureHelpTest`。  
  
2.  向项目添加编辑器分类器项模板。 有关详细信息，请参阅[在编辑器中的项模板创建扩展](../extensibility/creating-an-extension-with-an-editor-item-template.md)。  
  
3.  删除现有的类文件。  
  
4.  添加以下引用到项目中，并确保 **CopyLocal** 设置为 `false`:  
  
     Microsoft.VisualStudio.Editor  
  
     Microsoft.VisualStudio.Language.Intellisense  
  
     Microsoft.VisualStudio.OLE.Interop  
  
     Microsoft.VisualStudio.Shell.14.0  
  
     Microsoft.VisualStudio.TextManager.Interop  
  
## 实现签名帮助签名和参数  
 签名帮助源取决于实现的签名 <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature>, ，其中每个包含实现的参数 <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>。 在完整的实现中，将从相应语言文档，获取此信息，但在此示例中，签名是硬编码。  
  
#### 若要实现的签名帮助签名和参数  
  
1.  添加一个类文件并将其命名 `SignatureHelpSource`。  
  
2.  添加以下导入。  
  
     [!CODE [VSSDKSignatureHelpTest#1](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#1)]  
  
3.  添加一个名为类 `TestParameter` 实现 <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>。  
  
     [!CODE [VSSDKSignatureHelpTest#2](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#2)]  
  
4.  添加设置的属性的构造函数。  
  
     [!CODE [VSSDKSignatureHelpTest#3](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#3)]  
  
5.  属性添加 <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>。  
  
     [!CODE [VSSDKSignatureHelpTest#4](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#4)]  
  
6.  添加一个名为类 `TestSignature` 实现 <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature>。  
  
     [!CODE [VSSDKSignatureHelpTest#5](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#5)]  
  
7.  添加一些私有字段。  
  
     [!CODE [VSSDKSignatureHelpTest#6](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#6)]  
  
8.  添加一个构造函数，将字段设置和订阅到 <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> 事件。  
  
     [!CODE [VSSDKSignatureHelpTest#7](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#7)]  
  
9. 声明 `CurrentParameterChanged` 事件。 在签名中的参数之一的用户填写时，引发此事件。  
  
     [!CODE [VSSDKSignatureHelpTest#8](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#8)]  
  
10. 实现 <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.CurrentParameter%2A> 属性，以便它引发 `CurrentParameterChanged` 事件的属性值发生更改时。  
  
     [!CODE [VSSDKSignatureHelpTest#9](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#9)]  
  
11. 添加一个方法来引发 `CurrentParameterChanged` 事件。  
  
     [!CODE [VSSDKSignatureHelpTest#10](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#10)]  
  
12. 添加一个方法来通过比较中的逗号数来计算当前参数 <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A> 签名中的逗号分隔的数字。  
  
     [!CODE [VSSDKSignatureHelpTest#11](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#11)]  
  
13. 添加事件处理程序 <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> 调用的事件 `ComputeCurrentParameter()` 方法。  
  
     [!CODE [VSSDKSignatureHelpTest#12](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#12)]  
  
14. 实现 <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A> 属性。 此属性保存 <xref:Microsoft.VisualStudio.Text.ITrackingSpan> ，它对应于该签名所应用到的缓冲区中的文本范围。  
  
     [!CODE [VSSDKSignatureHelpTest#13](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#13)]  
  
15. 实现其他参数。  
  
     [!CODE [VSSDKSignatureHelpTest#14](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#14)]  
  
## 实现签名帮助源  
 签名帮助源是的签名为其提供信息的集合。  
  
#### 若要实现签名帮助源  
  
1.  添加一个名为类 `TestSignatureHelpSource` 实现 <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource>。  
  
     [!CODE [VSSDKSignatureHelpTest#15](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#15)]  
  
2.  添加到文本缓冲区的引用。  
  
     [!CODE [VSSDKSignatureHelpTest#16](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#16)]  
  
3.  添加设置文本缓冲区和签名帮助源提供程序的构造函数。  
  
     [!CODE [VSSDKSignatureHelpTest#17](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#17)]  
  
4.  实现 <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.AugmentSignatureHelpSession%2A> 方法。 在此示例中，签名是硬编码的但在完整的实现将从相应语言文档获取此信息。  
  
     [!CODE [VSSDKSignatureHelpTest#18](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#18)]  
  
5.  帮助器方法 `CreateSignature()` 提供仅供阐释。  
  
     [!CODE [VSSDKSignatureHelpTest#19](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#19)]  
  
6.  实现 <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.GetBestMatch%2A> 方法。 在此示例中，有两个签名，其中每个具有两个参数。 因此，此方法不是必需的。 在更完整的实现中，在其中多个签名帮助源不可用，此方法用于确定优先级最高的签名帮助源是否会提供匹配的签名。 如果无法实现，该方法返回 null，并且下一步最高优先级源需要提供一个匹配项。  
  
     [!CODE [VSSDKSignatureHelpTest#20](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#20)]  
  
7.  实现 dispose （） 方法︰  
  
     [!CODE [VSSDKSignatureHelpTest#21](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#21)]  
  
## 实现签名帮助源提供程序  
 签名帮助源提供程序是负责导出 Managed Extensibility Framework \(MEF\) 组件部件，并实例化签名帮助源。  
  
#### 若要实施此签名帮助源提供程序  
  
1.  添加一个名为类 `TestSignatureHelpSourceProvider` 实现 <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider>, ，并将其与导出 <xref:Microsoft.VisualStudio.Utilities.NameAttribute>, 、 <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> 的"text"和 <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> 的之前 \="default"。  
  
     [!CODE [VSSDKSignatureHelpTest#22](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#22)]  
  
2.  实现 <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider.TryCreateSignatureHelpSource%2A> 通过实例化 `TestSignatureHelpSource`。  
  
     [!CODE [VSSDKSignatureHelpTest#23](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#23)]  
  
## 实现命令处理程序  
 通常由触发签名帮助 \(字符和通过已忽略\) 字符。 您可以通过实现来处理这些击键 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> ，以便触发时收到一个签名帮助的会话 \(字符前面有一个已知的方法名称，并解除当接收该会话\) 字符。  
  
#### 若要实现的命令处理程序  
  
1.  添加一个名为类 `TestSignatureHelpCommand` 实现 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>。  
  
     [!CODE [VSSDKSignatureHelpTest#24](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#24)]  
  
2.  添加私有字段的 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 适配器 （这可以让您可以将命令处理程序添加到命令链处理程序）、 文本视图、 签名帮助 broker 和会话， <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator>, ，以及接下来的 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>。  
  
     [!CODE [VSSDKSignatureHelpTest#25](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#25)]  
  
3.  添加一个构造函数来初始化这些字段并将命令筛选器添加到命令链筛选器。  
  
     [!CODE [VSSDKSignatureHelpTest#26](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#26)]  
  
4.  实现 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> 方法可用于触发命令筛选器时收到的签名帮助的会话 \(字符之一的已知的方法名称，并消除当接收该会话后\) 字符会话时仍处于活动状态。 在所有情况下，转发该命令。  
  
     [!CODE [VSSDKSignatureHelpTest#27](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#27)]  
  
5.  实现 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> 方法，以便它始终将命令转发。  
  
     [!CODE [VSSDKSignatureHelpTest#28](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#28)]  
  
## 实现签名帮助命令提供程序  
 通过实现可以提供签名帮助命令 <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> 时要实例化的命令处理程序创建的文本视图。  
  
#### 若要实施此签名帮助命令提供程序  
  
1.  添加一个名为类 `TestSignatureHelpController` 实现 <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> 并将其与导出 <xref:Microsoft.VisualStudio.Utilities.NameAttribute>, ，<xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>, ，和 <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>。  
  
     [!CODE [VSSDKSignatureHelpTest#29](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#29)]  
  
2.  导入 <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> \(用于获取 <xref:Microsoft.VisualStudio.Text.Editor.ITextView>, ，给定 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 对象\)，则 <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> （用来查找当前的单词），与 <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker> （来触发签名帮助会话）。  
  
     [!CODE [VSSDKSignatureHelpTest#30](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#30)]  
  
3.  实现 <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A> 方法通过实例化 `TestSignatureCommandHandler`。  
  
     [!CODE [VSSDKSignatureHelpTest#31](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#31)]  
  
## 生成和测试代码  
 若要测试此代码，生成 SignatureHelpTest 解决方案并在实验实例中运行它。  
  
#### 若要生成并测试 SignatureHelpTest 解决方案  
  
1.  生成解决方案。  
  
2.  在调试器中运行此项目时，Visual Studio 的第二个实例将进行实例化。  
  
3.  创建一个文本文件和某些文本，其中包括单词"添加"的类型以及一个左括号。  
  
4.  键入左括号后，您应看到显示的两个签名的列表的工具提示 `add()` 方法。  
  
## 请参阅  
 [演练: 将内容类型链接到的文件扩展名](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)