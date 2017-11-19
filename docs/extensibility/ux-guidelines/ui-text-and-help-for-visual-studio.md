---
title: "UI 文本和 Visual Studio 的帮助 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e8747d07-6c90-46cc-b425-55b589f7e9e4
caps.latest.revision: "2"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b0019a0687370ac328fe78f57f1d26e661eb214a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ui-text-and-help-for-visual-studio"></a>UI 文本和 Visual Studio 的帮助
##  <a name="BKMK_UITextAndTerminology"></a>UI 文本和术语  
 易于理解的文本至关重要有效 UI。 软件用户倾向于读取标签第一次，即那些完成手头的任务最相关。 使用较少频率读取静态文本。 若要使用的整个窗口中，跟此大致顺序中的用户界面的读取一次快速扫描启动其工作会话的用户的计划：  
  
1.  中心中的交互式控件  
  
2.  提交按钮  
  
3.  在其他位置找到的交互式控件  
  
4.  主要说明  
  
5.  补充说明  
  
6.  窗口标题  
  
7.  在主正文中其他静态文本  
  
### <a name="usage-patterns-for-ui-text"></a>UI 文本的使用模式  
  
#### <a name="title-bar-text"></a>标题栏文本  
 标题栏文本必须与匹配的命令，生成 UI。  
  
#### <a name="instructional-text-helper-text"></a>说明文本 （帮助程序文本）  
 在一些对话框中，很有助于提供突出显示主要用于说明要执行的操作在窗口或页中的说明。 这有时称为"帮助程序文本"。  
  
##### <a name="writing-style-rules-for-helper-text"></a>编写帮助器文本的样式规则  
  
-   不解释明显。 除非绝对需要不包括其他说明性文本。  
  
-   说明文本始终放置在对话框的顶部，并应参考正在执行的任务。  
  
-   精确地向用户说明他们需要做什么。 避免过多的通信和冗余。  
  
-   查看每个窗口，并消除重复的单词和语句。  
  
-   保持简短的说明性文本。 如果必要对于某些用户或方案的详细信息，然后提供详细的概念联机主题的链接。  
  
-   编写你的文本，使每个词保持权重，并是必需的。  
  
-   遵循现有 Microsoft 指南[用户界面文本](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742478\(v=vs.85\).aspx)和[其次，要明确](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742477\(v=vs.85\).aspx)。  
  
#### <a name="supplemental-instructions"></a>补充说明  
 补充说明提供可帮助用户了解控件或控制分组的其他信息。 这可能还包含了解预期的输入的控件何种格式所需的提示文本。 补充说明应谨慎使用。 保留它们的情况下，它可能用户不会完全了解后果的做出的选择。  
  
 ![Visual Studio 中的补充文本](../../extensibility/ux-guidelines/media/0601-b_supplementaltext1.png "0601 b_SupplementalText1")  
  
 **Visual Studio 中的补充文本**  
  
 ![Visual Studio 中的补充文本](../../extensibility/ux-guidelines/media/0601-c_supplementaltext2.png "0601 c_SupplementalText2")  
  
 **Visual Studio 中的补充文本**  
  
#### <a name="infotips"></a>InfoTips  
 通常情况下，说明文本可能太长，将适当地定位在 UI 中，或可能有用，仅向新用户，感觉像混乱有经验的用户的情况为准。 在这种情况下，应该为工具提示信息提示下放置说明性/信息性文本。  
  
 InfoTips 应该放置控件它们与相关，并且应使用尚不引人注目的特定信息提示图标附近明显。  
  
 ![Visual Studio 中的信息提示](../../extensibility/ux-guidelines/media/0601-d_infotip.png "0601 d_InfoTip")  
  
 **Visual Studio 中的提示信息的示例**  
  
##### <a name="writing-style-rules-for-infotips"></a>InfoTips 写入样式规则  
  
-   将 InfoTips 编写为完整的句子。 它们需要特定谓词，句子大小写和结束标点。  
  
-   使用 InfoTips 来补充主要指令或信息。 如果您只需使用不同的单词若要重述主要思路，则不需要的信息提示。  
  
-   保留 InfoTips 简洁明了。 使用多义词和无格式、 日常支持并鼓励使用用户的语言。  
  
-   遵循现有 Microsoft 指南[用户界面文本](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742478\(v=vs.85\).aspx)和[其次，要明确](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742477\(v=vs.85\).aspx)。  
  
#### <a name="control-labels"></a>控件标签  
 控件标签应较短的简洁，并按照[控件的 Windows 桌面指南](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742399\(v=vs.85\).aspx)。  
  
 有关控件标签格式和放置在用户界面的详细信息，请参阅[for Visual Studio 布局](../../extensibility/ux-guidelines/layout-for-visual-studio.md)。  
  
#### <a name="help-links"></a>帮助链接  
 在说明文本或 UI 的正文中，或者可以放置帮助链接。 它们可以帮助的链接或启动内部对话框。  
  
##### <a name="visual-style-rules-for-help-links"></a>帮助链接的视觉样式规则  
  
-   使用正确环境颜色的超链接。 正确应用了样式的超链接将不简要以红色闪烁单击时。 如果你看到此内容，则会指示不使用环境颜色。  
  
-   仅应上悬停时或当链接嵌入在段落中使用下划线。  
  
-   有关 visual 和交互样式的超链接的更多详细信息，请参阅按钮和超链接。  
  
##### <a name="writing-style-rules-for-help-links"></a>编写帮助链接的样式规则  
  
-   在启动对话框，维护对于省略号的标准： 导航窗格中，如果任务需要其他 UI 省略号没有省略号。  
  
     ![Visual Studio 中的帮助链接](../../extensibility/ux-guidelines/media/0601-e_helplink.png "0601 e_HelpLink")  
  
     **省略号 （...） 中的帮助链接指示任务将需要其他 UI。**  
  
-   链接不应该开头"了解"，因为不是用户的意图。 用户想要回答特定的问题，不会收到常规教育版。  
  
-   短语帮助链接，以便会问主题将回答这个问题。  
  
     不正确：  
     "了解有关 Windows Azure 移动服务定价详细信息"  
  
     更正：  
     "哪些定价选项是一些可用于 Windows Azure 移动服务？"  
  
-   永远不会使用*单击...*到此链接文本。  
  
-   永远不会链接只有词"此处"。 这会产生问题的一些屏幕阅读器，这将语音只有超链接的词。  
  
     不正确：  
     "找到有关 Windows Azure 移动服务信息**此处**"  
  
     更正：  
     "哪些定价选项是一些可用于 Windows Azure 移动服务？"  
  
-   有关帮助链接的正确写入样式的详细信息，请参阅[Windows 桌面指南以获取帮助](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742494\(v=vs.85\).aspx)。  
  
#### <a name="hint-text"></a>提示文本  
 提示文本显示为水印控件内或在控件的下方。 通过使用适当的 VSColors 令牌中，将应用正确的格式设置`Environment.GrayText`。  
  
 它可以出现在大量的窗体。  
  
-   代替控件标签中：  
  
     ![提示 Visual Studio 中的文本](../../extensibility/ux-guidelines/media/0601-f_hinttext1.png "0601 f_HintText1")  
  
-   与谓词，给出的说明：  
  
     ![提示 Visual Studio 中的文本](../../extensibility/ux-guidelines/media/0601-g_hinttext2.png "0601 g_HintText2")  
  
-   带有文本，指示所需的项：  
  
     ![提示 Visual Studio 中的文本](../../extensibility/ux-guidelines/media/0601-h_hinttext3.png "0601 h_HintText3")  
  
#### <a name="watermark-text"></a>水印文本  
 在空设计图面上，文本应指示要执行操作，以及提供链接以打开其他相关的 windows，如果相应的内容：  
  
 ![水印 Visual Studio 中的文本](../../extensibility/ux-guidelines/media/0601-i_watermarktext.png "0601 i_WatermarkText")  
  
 **Visual Studio 中的水印文本的示例**  
  
### <a name="common-terminology"></a>常见术语  
  
|术语|说明|注释|  
|----------|-----------------|-------------|  
|登录/注销|使用同义词 web 表示转换的 web 属性的身份验证的谓词。 在客户端，我们使用此一次作为顶级概念进行入和移出 IDE 用户连接，它表示一个顶级的标识，提供更高级别的功能，例如漫游和许可，不能与所有其他连接一起签名。|IDE 用户是唯一的功能应表示登录 / 注销谓词，因为它表示顶级 IDE 用户。|  
|连接/断开连接|使用在其中一项功能维护与一项联机服务的单一连接的位置。|服务器资源管理器，其中只能有一个活动的 Azure 连接一次，是连接/断开连接的一个示例。|  
|添加/删除|非破坏性。 添加或从列表中删除内容时使用。|TFS 连接管理器服务器列表对话框是添加/删除的一个示例。|  
|删除|破坏性。 仅当要删除的元素将永久被弃用或从磁盘中删除时，才使用。|如果结果从磁盘中删除的文件，"删除"通常需要一条提示。|  
  
## <a name="error-messages"></a>错误消息  
  
### <a name="overview"></a>概述  
 错误发生。 设置限制用户可以执行的操作是阻止不如错误消息的合理第一步。 但是，当确实发生错误，编写良好的错误消息可以转对于缓解此问题。 错误消息可能是有最重要的用户将看到，因为它们是同步的指示需要解决的问题的通知类型之一。 编写不佳的错误消息将保留在其自己以确定错误原因和任何可能的解决方案上的用户。  
  
 注意，若要过度使用或混淆以便将值添加到用户的写入仅将必需消息遇到以下错误消息，用户可能会停止。 如果消息是只需一个通知，然后使用备用的演示文稿。  
  
### <a name="rules-for-creating-an-error-message"></a>用于创建一条错误消息的规则  
  
-   构造时错误消息，请为用户选择相应的错误级别。 如果适用，简单的摘要，可提供用户的操作的目的是可能需要。 用户不需要知道的任何内容不状态。  
  
-   提供建设性协助。 很容易地读取和处理的错误消息包含指令。  
  
-   不要使用两个负值。  
  
-   执行这两个自动和手动语法和拼写检查在你编写的任何错误消息。  
  
-   对于复杂的错误消息，避免顺序通信。 错误消息，永远不会使用 F1 挂钩。 消息本身应该够用。  
  
-   使用正确的图标。  
  
-   使问题更易于了解和使用按钮具有清除选择，例如"删除"和"取消。  
  
-   警告，为清楚地了解将哪些继续的后果。 按钮应指明带来的后果。  
  
-   对于错误，描述了执行哪些用户可以操作来解决此问题。 按钮应操作或说出"关闭"。 不要使用"确定"按钮执行一条错误消息。  
  
-   要提出自己构造一条错误消息时的一些问题：  
  
    -   用户可以了解如何解决此错误仅出现的问题？  
  
    -   用户是否使用与此错误相同词汇？  
  
    -   此错误 ambigious 或在多个情况下共享？ 如果是这样，如何你指导用户设置所需的解决方案？  
  
#### <a name="build-errors"></a>生成错误  
 由于 Visual Studio 是软件开发工具，有许多及其组件的编译时，将转换，或编码步骤将开发人员工作转换为二进制格式。 当编译器无法处理不正确编写的文件时，或未正确设置编译器选项时，这些转换可能导致错误。  
  
 Visual Studio 用户可以花了包含大量解决生成错误的开发时间。 当错误存在依赖关系或时写入错误消息是不佳，这可以使难以发现的错误的源，可提高此解决时间。  
  
 最佳的生成错误是那些不出现在第一个位置，这正是 Visual Studio 提供记忆式键入功能和 IntelliSense 的波形曲线。 架构验证程序和类似工具提供的相同类型的反馈。 这些机制主动指导用户构造格式正确的代码，减少了生成错误的可能性。  
  
 Visual Studio 提供的工具窗口，其中用户能够阅读和浏览其文档窗口中发生的错误。 提供了键盘快捷方式，以便用户能够快速导航大量的代码并直接转至问题的位置。 Visual Studio 还允许每个生成错误，若要将绑定到特定的帮助关键字/上下文 ID，以便用户可以直接转到帮助主题提供有关错误的更多详细信息。  
  
 编写清晰、 简洁生成错误：  
  
-   **使用纯语言**说明的问题很少或没有编译器行话。 生成错误的文本不应为过于技术。  
  
-   **概述了可能的原因。** 例如，"缺少的属性和值之间冒号 （属性）: （值） 声明。"  
  
-   提供有关潜在修复的详细信息。 如果没有足够的空间，然后其他详细信息可能会放入相应的帮助主题。  
  
### <a name="components-of-a-well-written-error-message"></a>编写良好的错误消息的组件  
  
#### <a name="use-the-shell-dialog-service-for-error-messages"></a>使用命令行程序对话框服务的错误消息。  
 使用 shell 对话框服务可让你具体而言，控制消息，字体的外观，而对各个元素的重大更改。 使用**IErrorInfo**机制，并报告它们使用**IVsUIShell::SetErrorInfo/ReportErrorInfo**。  
  
#### <a name="choose-an-effective-and-appropriate-notification-presentation"></a>选择一个有效且相应通知的演示文稿。  
 如果需要立即采取措施来避免丢失数据 （同步通知），请使用一个模式对话框具有严重警告。 在关闭消息，而读取它可能导致造成负面影响的情况下保留关键图标。 数据丢失，则需要警报级别响应的关键情况。 严重图标的过度使用 desensitizes 到其重要性的用户。 如果错误消息为信息性本质，请考虑一个模式对话框 （异步通知） 的替代方法。  
  
#### <a name="provide-a-clean-succinct-explanation-of-why-the-problem-occurred-rather-than-a-technical-explanation"></a>提供而不是技术说明出现问题的原因的干净、 简洁的说明。  
 会使负担过重的说明中的技术详细信息的用户会使它们更有可能忽略错误消息。 好消息传递的示例：  
  
-   "无法打开请求的文件。"  
  
-   "无法连接到 Internet。"  
  
#### <a name="provide-information-about-how-to-fix-the-problem"></a>提供有关如何解决此问题的信息。  
 提供如何解决此问题的用户的建议。 如果不有任何建议，则为与用户诚实。 提供到备用的联机资源，如技术支持或社区支持的直接链接。 尝试为用户指向与问题相关的特定联机信息。 错误 ID，请考虑将用户链接到有关该特定错误的讨论线程。 好消息传递的示例：  
  
-   "请确保你连接到 Internet，重试此操作。"  
  
-   "请确保文件存在，而且您有权打开它。"  
  
#### <a name="write-a-message-that-is-short-and-to-the-point"></a>编写一条消息，是短并点。  
 一条错误消息可以通知，说明，并提供解决方案但如果太过罗嗦仍被忽略。 一种解决方案是将与详细信息按钮使用渐进式泄露。 例如，为短说明/解决方案，然后将详细信息按钮下的更多详细信息。 如果用户选择读取错误的详细信息，用户可以这样做。  
  
 消息中的语言应为：  
  
-   **域相对应。** 使用用户将能理解的语言。 即使我们的客户是开发人员，它们通常没有的上下文和我们有的术语。  
  
-   **特定。** 避免含糊措词，提供特定名称和位置所涉及的对象。 例如，一条错误消息如"无效字符"不是很有用。 用于转换的字符？ "找不到文件"。 哪些文件？  
  
-   **一种礼貌。** 不要责怪用户或让他们感到愚笨。 避免恶意或冒犯性的语言 （终止、 执行和终止，致命的非法）。 避免使用大写的文本，通常被视为喊叫且不为读。 不要使用幽默。  
  
-   **更正。** （即使在 alpha 版） 中使用正确的拼写和语法。 拼写错误是不专业和讨厌。  
  
-   **上下文相关。** 使用相应的按钮文本。 避免"确定"按钮并改为使用"继续"或"是/否"  
  
### <a name="error-message-examples"></a>错误消息示例  
  
|好|错误|  
|----------|---------|  
|"拨打的号码不再在服务中。 请检查数以及重试或为操作符拨打 0。"|-"错误 (449): 非法数"<br />-"此未经处理的异常错误情况表示操作成功完成"。<br /><br /> ![Visual Studio 中的无效的错误消息](../../extensibility/ux-guidelines/media/0602-a_errordialog.png "0602 a_ErrorDialog")|  
  
## <a name="accessing-help"></a>访问帮助  
  
### <a name="overview"></a>概述  
 除了 MSDN 中的文档，Visual Studio 用户具有多个访问点，以帮助用户在 UI 中。 若要确保这些接入点始终可用，功能团队需要充分利用由环境提供的帮助系统。 这些访问点是：  
  
-   **对话框中的说明和补充性文本。** 不提供方向或说明上图面或可在将鼠标悬停在信息提示图标上的用户界面, 的静态文本。  
  
-   **F1 帮助**（仅编辑器）。 在 Visual Studio 编辑器中，用户可以信任，任何时候，按 F1 会弹出一个特定于当前所选内容的帮助主题。 确保 F1 与关联的主题是适当和信息性。  
  
-   **帮助主题的超链接。** 在对话框、 工具窗口中或启动主题以了解更多有关技术、 功能或有关如何完成某项任务的信息帮助用户的设计图面超链接。  
  
-   **帮助器 UI 机制，例如智能标记和生成对话框。** 这些机制帮助用户了解 UI 元素，或帮助实现的任务，例如，智能标记或生成器对话框。  
  
-   **UI 帮助按钮**（已弃用）。 在标题栏提供访问权限的相关的 F1 帮助主题中的可见标记。  
  
### <a name="text"></a>Text  
  
#### <a name="instructional-and-supplemental-text-in-dialogs"></a>对话框中的说明和补充文本  
 在对话框中，支持复杂的任务，可能需要在顶部的对话框中或其附近复杂控件通常提供在 UI 中中的说明文本。 请参阅[UI 文本和术语](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology)有关编写样式的详细信息。  
  
#### <a name="infotips"></a>InfoTips  
 通常情况下，说明文本可能太长，将放置在 UI 中的位置，或者可能有用，仅向新用户，感觉像混乱有经验的用户的情况为准。 在这种情况下，应该为工具提示信息提示下放置说明性/信息性文本。  
  
 InfoTips 应该放置控件它们与相关，并且应使用尚不引人注目的特定信息提示图标附近明显。  
  
 ![Visual Studio 中的信息提示](../../extensibility/ux-guidelines/media/0601-d_infotip.png "0601 d_InfoTip")  
  
 **Visual Studio 中的提示信息的示例**  
  
### <a name="interactive-help-mechanisms"></a>交互式帮助机制  
  
#### <a name="f1-help"></a>F1 帮助  
 是必需的 F1 帮助编辑器或设计图面上，但不是在其他位置在 Visual Studio 环境中。  
  
#### <a name="hyperlinks-to-help-topics"></a>帮助主题的超链接  
 超链接可以用于执行的操作、 导航 IDE 中，或在浏览器中启动的帮助。 请参阅[UI 文本和术语](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology)有关语言和 07.10.01 的详细信息按钮和 visual 和布局指南的超链接。  
  
#### <a name="help--buttons-in-dialog-title-bars-deprecated"></a>帮助 （已弃用） 对话框标题栏中的 [？] 按钮  
 大多数情况下，在对话框的标题栏中的帮助 [？] 按钮已被否决。 UI 主题不再是我们的文档模型中的一部分，因此有可能不是相关的主题，以将链接到。 从根本上来说，标题栏按钮已作为 F1 帮助，相同的操作，并且不再要求对话框中。 在某些情况下，这仍可作为指示器具有概念或过程的详细信息可用，尽管在较新的 UI 中更常用于超链接。  
  
##### <a name="dialogs-created-through-the-environment"></a>通过环境创建的对话框  
 许多 shell 对话框创建通过**VBDialogBoxParam**函数。 此共享的函数进行更新，以帮助移动**帮助**从到对话框的按钮**？** 按钮时保留一个体系结构，可向后兼容并可扩展。  
  
 具体而言， **VBDialogBoxParam**函数检查其 id 的按钮的对话框模板**IDHELP** (9) 或标签是**帮助**或**（& a) 帮助**. 如果找到一个帮助按钮，则其处于隐藏状态和**WS_EX_CONTEXTHELP**样式添加到对话框中，然后放置**？** 在对话框的标题栏中的按钮。  
  
 创建对话框时，它将推送到堆栈对话框 proc 并使用名为预处理对话框 proc 调用对话框**DialogPreProc**。 当**？** 单击按钮时，将发送**WM_SYSCOMMAND**的**SC_CONTEXTHELP**到了对话框。 **DialogPreProc**捕获此命令并将其到更改**WM_HELP**消息，传递到原始对话框处理器。  
  
 大多数环境创建对话框必须在对话框上的帮助按钮。 帮助按钮显示对话框时，是自动隐藏，只有在**？** 按钮正常工作。 如果**？** 按钮会删除或在 Windows 中更改，此解决方案可以快速将移回原始的帮助按钮。  
  
 此解决方案使可能会导致 bug 的四个假设：  
  
-   对话框的帮助按钮是**IDHELP** (9)。  
  
-   隐藏帮助按钮时，对话框上去正确。  
  
-   对话框将其 winproc 不替换。  
  
-   对话框中未嵌入在另一个对话框，内部。  
  
 如果你的对话框位于 msenv 内，并且不使用**VBDialogBoxParam**，调查利用**VBDialogBoxParam**实现你自己的处理程序之前。  
  
##### <a name="dialogs-created-through-other-packages"></a>通过其他包创建的对话框  
 你可以实现你自己的解决方案之外 msenv 驻留的对话框。 你的 VSPackage 中的共享的对话框类，请考虑将按钮移到标题栏或在每个对话框上实现一个处理程序。 下面的代码是实现以帮助你开始骨架：  
  
```  
struct DLGPROCITEM  
{  
    FARPROC proc; // The info used to create the dialog.  
    DLGPROCITEM* procPrev;  
};  
  
DLGPROCITEM* g_dlgProcStack = NULL;  
  
// A dialog starter/wrapper function is used to push the new  
// dialog proc to the top of our dialog proc stack.  
  
int SomeDialogStarterFunction(hinst, id, proc, etc)  
{  
    if (g_dlgProcStack == NULL)  
    {  
        g_dlgProcStack = new DLGPROCITEM;  
        g_dlgProcStack->procPrev = NULL;  
    }  
    else  
    {  
        DLGPROCITEM* procItem = new DLGPROCITEM;  
        g_dlgProcStack->procPrev = g_dlgProcStack;  
        g_dlgProcStack = procItem;  
    }  
}  
  
// Pop this dialog proc off the dialog proc stack.  
  
DialogBoxIndirectParam...(...)  
{  
    DLGPROCITEM* procItem = g_dlgProcStack->procPrev;  
    delete g_dlgProcStack;  
    g_dlgProcStack = procItem;  
}  
  
// A wrapper dialog procedure will allow us to capture the  
// SC_CONTEXTHELP button on the title bar from Windows and  
// forward it as a simple WM_HELP message back to the dialog.  
  
INT_PTR CALLBACK DialogPreProc(HWND hwndDlg, UINT uMsg,  
    WPARAM wParam, LPARAM lParam)  
{  
    if (uMsg == WM_SYSCOMMAND && wParam == SC_CONTEXTHELP)  
    {  
        uMsg = WM_HELP;  
        wParam = 0;  
        lParam = 0;  
    }  
    return CallWindowProc((WNDPROC)g_dlgProcStack->proc,  
        hwndDlg, uMsg, wParam, lParam);  
}  
```  
  
##### <a name="help-buttons-in-managed-code"></a>在托管代码中的帮助按钮  
 重写窗口标题栏帮助按钮的默认行为是在托管代码中轻松。 下面是演示此行为的完整演示应用程序。 实质上，您需要重写你的窗体**WndProc**方法和关闭的 F1 帮助然后激发请求时**SC_CONTEXTHELP**截获消息。  
  
```  
using System;  
using System.Windows.Forms;  
  
public class HelpForm : Form  
{  
    private const int SC_CONTEXTHELP = 0xF180;  
    private const int WM_SYSCOMMAND = 0x0112;  
  
    public HelpForm()  
    {  
        this.ClientSize = new System.Drawing.Size(300, 250);  
        this.HelpButton = true;  
        this.MaximizeBox = false;  
        this.MinimizeBox = false;  
        this.Name = "HelpForm";  
        this.Text = "Help Form";  
    }  
  
    protected override void WndProc(ref Message m)  
    {  
        if (m.Msg == WM_SYSCOMMAND && SC_CONTEXTHELP == (int)m.WParam)  
            ShowHelp();  
        else  
            base.WndProc(ref m);  
    }  
  
    private void ShowHelp()  
    {  
        MessageBox.Show("F1 Help goes here.");  
    }  
  
     [STAThread]  
    static void Main()  
    {  
        Application.EnableVisualStyles();  
        Application.EnableRTLMirroring();  
        Application.Run(new HelpForm());  
    }  
}  
```  
  
## <a name="see-also"></a>另请参阅  
 [字体和 Visual Studio 的格式设置](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md)   
 [Visual Studio 的布局](../../extensibility/ux-guidelines/layout-for-visual-studio.md)   
 [Visual Studio 的通知和进度](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md)