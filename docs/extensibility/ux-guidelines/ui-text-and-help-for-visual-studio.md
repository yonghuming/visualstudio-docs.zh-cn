---
title: "UI 文本以及 Visual Studio 的帮助 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e8747d07-6c90-46cc-b425-55b589f7e9e4
caps.latest.revision: 2
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 2
---
# UI 文本以及 Visual Studio 的帮助
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

##  <a name="BKMK_UITextAndTerminology"></a> UI 文本和术语  
 易于理解的文本至关重要有效的用户界面。 软件的用户习惯于读取标签第一次，即那些最相关的完成手头的任务。 静态文本时读取更少的频率。 规划用户从他们的工作会话开始的整个窗口中后, 跟此大致顺序中的用户界面的读取一次快速扫描:  
  
1.  在中心中的交互控件  
  
2.  提交按钮  
  
3.  在其他地方找到的交互控件  
  
4.  主要说明  
  
5.  补充说明  
  
6.  窗口标题  
  
7.  中的主要部分的其他静态文本  
  
### UI 文本的使用模式  
  
#### 标题栏文本  
 标题栏文本必须与匹配生成用户界面的命令。  
  
#### 说明文字 \(帮助器文本\)  
 在一些对话框中，最好先提供突出主要说明解释如何在窗口或页面中。 这有时称为"帮助程序 text。  
  
##### 编写帮助器文本的样式规则  
  
-   不解释显而易见。 除非绝对有必要，否则不要包含说明性文本。  
  
-   说明文本始终放置在对话框的顶部，并应参考正在执行的任务。  
  
-   精确地向用户解释它们需要做什么。 避免过多的通信和冗余。  
  
-   查看每个窗口，并消除重复的单词和语句。  
  
-   保持简短的说明性文本。 如果有必要为某些用户或方案的详细信息，然后提供指向详细的概念性联机主题的链接。  
  
-   编写您的文本，以便保留权重和是必需的每个单词。  
  
-   遵循现有的 Microsoft 指南 [用户界面文本](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742478\(v=vs.85\).aspx) 和 [其次，要明确](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742477\(v=vs.85\).aspx)。  
  
#### 补充说明  
 补充说明提供可帮助用户了解控件或控制分组的其他信息。 这可能包括了解预期的输入的控件何种格式所需的提示文本。 补充说明应谨慎使用。 保留它们的情况下，它可能用户完全不了解后果的正在进行的选择。  
  
 ![Supplemental text in Visual Studio](../../extensibility/ux-guidelines/media/0601-b_supplementaltext1.png "0601\-b\_SupplementalText1")  
  
 **Visual Studio 中的补充文本**  
  
 ![Supplemental text in Visual Studio](~/extensibility/ux-guidelines/media/0601-c_supplementaltext2.png "0601\-c\_SupplementalText2")  
  
 **Visual Studio 中的补充文本**  
  
#### 信息提示  
 通常情况下，说明文本可能太长，将适当地定位在 UI 中或者可能仅对新用户，还觉得自己象有经验的用户的混乱有用。 在这种情况下，应为工具提示信息提示下放说明性\/信息性文本。  
  
 信息提示应放置在它们与相关，并且应使用特定的信息提示图标，也是按照不引人注意的控件附近明显。  
  
 ![InfoTip in Visual Studio](../../extensibility/ux-guidelines/media/0601-d_infotip.png "0601\-d\_InfoTip")  
  
 **在 Visual Studio 中的信息提示的示例**  
  
##### 信息提示的书写样式规则  
  
-   作为完整的句子编写信息提示。 它们需要特定的谓词，句子大小写和结束标点。  
  
-   使用信息提示来补充您的主要说明或信息。 如果您只需使用不同的单词次提醒你注意的主要设计理念，则不需要的信息提示。  
  
-   使信息提示保持简短而明了。 使用较小的单词和无格式、 日常支持并鼓励用户的语言。  
  
-   遵循现有的 Microsoft 指南 [用户界面文本](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742478\(v=vs.85\).aspx) 和 [其次，要明确](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742477\(v=vs.85\).aspx)。  
  
#### 控件标签  
 控件标签应该是短、 简洁，并按照 [控件的 Windows 桌面指南](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742399\(v=vs.85\).aspx)。  
  
 有关控制标签格式以及放置在用户界面的详细信息，请参阅 [Visual Studio 的布局](../../extensibility/ux-guidelines/layout-for-visual-studio.md)。  
  
#### 帮助链接  
 中的说明文本或在用户界面的正文，也可以放帮助链接。 它们可以链接到帮助或启动内部对话框。  
  
##### 帮助链接的视觉样式规则  
  
-   将正确的环境颜色用于超链接。 正确设置了样式的超链接将不闪烁一下红色单击时。 如果你看到这一点，则表示未使用的环境颜色。  
  
-   只应在悬停或时该链接嵌入到一个段落下划线。  
  
-   可视化和交互的超链接的样式的更多详细信息，请参阅按钮和超链接。  
  
##### 编写帮助链接的样式规则  
  
-   在启动对话，维护省略号的标准: 导航栏中，如果任务需要额外的用户界面的省略号没有省略号。  
  
     ![Help link in Visual Studio](~/extensibility/ux-guidelines/media/0601-e_helplink.png "0601\-e\_HelpLink")  
  
     **省略号 \(...\) 在提供的帮助链接指示任务将需要其他用户界面。**  
  
-   因为这不是用户的意图，应不以"了解，"开头的链接。 用户想要回答的特定问题，不会收到常规教育。  
  
-   短语帮助链接起来，因此会问主题将回答这个问题。  
  
     不正确:  
     "了解有关 Windows Azure 移动服务定价的详细信息"  
  
     更正:  
     "哪些定价选项是一些可用于 Windows Azure 移动服务?"  
  
-   永远不会使用 *单击...* 到此链接文本。  
  
-   永远不会将链接只有词"在此处。" 这是一些屏幕读取器，将语音只有超链接的 word 的问题。  
  
     不正确:  
     "查找有关 Windows Azure 移动服务 **此处**"  
  
     更正:  
     "哪些定价选项是一些可用于 Windows Azure 移动服务?"  
  
-   帮助链接的正确的写作风格的详细信息，请参阅 [帮助的 Windows 桌面指南](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742494\(v=vs.85\).aspx)。  
  
#### 提示文本  
 作为水印在控件内或在控件的下方将显示提示文本。 通过使用适当的 VSColors 令牌，将应用正确的格式设置 `Environment.GrayText`。  
  
 它可以出现在多种形式。  
  
-   代替控件标签中:  
  
     ![Hint text in Visual Studio](../../extensibility/ux-guidelines/media/0601-f_hinttext1.png "0601\-f\_HintText1")  
  
-   以动词，给出的说明:  
  
     ![Hint text in Visual Studio](../../extensibility/ux-guidelines/media/0601-g_hinttext2.png "0601\-g\_HintText2")  
  
-   与表示所需的项的文本:  
  
     ![Hint text in Visual Studio](../../extensibility/ux-guidelines/media/0601-h_hinttext3.png "0601\-h\_HintText3")  
  
#### 水印文本  
 空设计图面上，该文本应指明要执行操作，以及提供链接以打开其他相关的窗口，在适当的内容:  
  
 ![Watermark text in Visual Studio](../../extensibility/ux-guidelines/media/0601-i_watermarktext.png "0601\-i\_WatermarkText")  
  
 **在 Visual Studio 中的水印文本的示例**  
  
### 常见术语  
  
|术语|说明|注释|  
|--------|--------|--------|  
|登录\/注销|作为同义词使用与 web 用于表示身份验证内置于 web 属性的谓词。 在客户端，我们使用一次此作为顶级概念进行签名入和移出 IDE 用户连接，这表示提供更高级别的功能，例如漫游和授权，不是适用于所有其他连接的顶层标识。|IDE 用户是唯一的功能，应表示登录 \/ 注销谓词，因为它表示顶级 IDE 用户。|  
|连接\/断开连接|中的一项功能，维持到一项联机服务的单一连接的位置使用。|服务器资源管理器，其中只能有一个活动的 Azure 连接一次，是一种连接\/断开。|  
|添加\/删除|非破坏性。 添加或从列表中删除某些内容时使用。|TFS 连接管理器服务器列表对话框是举例说明如何添加\/删除。|  
|删除|破坏性。 仅当使用将永久丢弃或从磁盘中删除所移除的元素。|如果结果从磁盘中删除文件，"删除"通常需要一条提示。|  
  
## 错误消息  
  
### 概述  
 发生错误。 设置限制用户可以执行的操作是阻止发生可避免错误消息的合理的第一步。 但是，当确实发生错误，编写良好的错误消息可以方面走得更长的缓解此问题。 错误消息可以说是通知的一种最重要的用户可以看到，因为它们都是通知的同步的并指明需要解决的问题类型。 编写得非常糟糕的错误消息将用户保留在其自己以确定错误的原因和任何可能的解决方案。  
  
 用户可能会停止关注过度使用或混淆错误消息，所以，仅将必要写入将值添加到用户的消息。 如果消息只是一条通知，然后使用备用的演示文稿。  
  
### 创建一条错误消息的规则  
  
-   构造时的错误消息，请为用户选择相应的错误级别。 如果适用，请提供用户可以执行，一个操作的简单摘要的目标。 无状态用户不需要知道的任何内容。  
  
-   提供建设性的帮助。 会更加轻松地读取和处理包含说明的错误消息。  
  
-   不要使用双重否定。  
  
-   执行这两个自动和手动语法和拼写检查您编写的任何错误消息。  
  
-   对于复杂的错误消息，从而避免顺序通信。 永远不会使用 F1 挂接的错误消息。 消息本身应该已足够。  
  
-   使用正确的图标。  
  
-   使问题更易于理解和使用按钮具有清除选择，例如"删除"和"取消。  
  
-   对于警告，是清楚地了解继续操作的结果将是什么。 这些按钮应指示带来的后果。  
  
-   考虑到错误，说明用户可以如何解决此问题。 按钮应操作或说"关闭"。 不要使用"确定"按钮执行一条错误消息。  
  
-   要问问自己构造一条错误消息时的一些问题:  
  
    -   用户可以了解如何解决此错误仅出现的问题?  
  
    -   用户是否使用与此错误相同的词汇?  
  
    -   此错误 ambigious 还是在多个的情况下共享? 如果是这样，如何您指导用户设置所需的解决方案?  
  
#### 生成错误  
 由于 Visual Studio 是一种软件开发工具，有许多及其组件的编译时，将转换时，或编码步骤将开发人员的工作转换为二进制格式。 当编译器无法处理不正确编写的文件，或者当未正确设置编译器选项，这些转换可能会导致错误。  
  
 Visual Studio 用户可能要花费大量开发时间解决生成错误。 此解决时间可以提高时错误都有依赖关系或当错误消息将不佳写入，这可以使难被发现错误的来源。  
  
 最佳的生成错误是指那些不会出现在第一个位置，就是为什么 Visual Studio 提供记忆式键入功能，IntelliSense 画波浪线。 架构验证程序和类似的工具提供了相同类型的反馈。 这些机制主动指导用户构造格式良好的代码中，降低生成错误的可能性。  
  
 Visual Studio 提供了一个工具窗口，用户可以读取并浏览其文档窗口中发生的错误。 键盘快捷方式提供，以便用户可以快速导航大量的代码，并直接转到问题的位置。 Visual Studio 还允许每个生成错误，若要将绑定到某一特定的帮助关键字\/上下文 ID，以便用户可以直接转到更加深入地介绍有关错误的帮助主题。  
  
 编写清晰、 简洁的生成错误:  
  
-   **使用平实的语言** 来解释编译器术语中很少或没有与此问题。 生成错误的文本不应过于技术。  
  
-   **概述了可能的原因。**例如，"缺少冒号属性中的值之间 \(属性\): \(值\) 声明。"  
  
-   提供有关潜在修复的详细信息。 如果没有足够的空间，然后其他详细信息可能会放入相应的帮助主题。  
  
### 编写良好的错误消息的组件  
  
#### 使用命令行程序对话框服务存在错误消息。  
 使用命令行程序对话框服务允许您控制消息的外观 — 尤其是字体 — 而无需对各个元素的主要更改。 使用 **IErrorInfo** 机制并报告这些使用 **IVsUIShell::SetErrorInfo\/ReportErrorInfo**。  
  
#### 选择一个有效且适当的通知的演示文稿。  
 如果需要立即采取措施以避免丢失数据 \(同步通知\)，请使用一个模式对话框具有严重警告。 在关闭消息，而读取它会导致造成负面影响的情况下保留关键图标。 数据丢失是严重的情况下，需要的警报等级响应。 严重图标的过度使用 desensitizes 用户添加到它的重要性。 如果错误消息是进行例行通知，实际上，请考虑一个模式对话框 \(异步通知\) 的替代方法。  
  
#### 提供清晰、 简洁而不是技术说明发生此问题的原因的解释。  
 具有说明中的技术详细信息的用户数据库负担过重会使它们更容易忽略错误消息。 好消息的示例:  
  
-   "无法打开请求的文件。"  
  
-   "无法连接到 Internet。"  
  
#### 提供有关如何解决此问题的信息。  
 提供了如何解决此问题的用户的建议。 坦白地讲与该用户是否有任何建议。 提供指向其他联机资源，如技术支持或社区支持的直接链接。 请尝试将用户引到与该问题相关的特定在线信息。 错误 ID，请考虑将用户链接到有关该特定错误的讨论话题。 好消息的示例:  
  
-   "请确保您连接到 Internet 并重新尝试此操作。"  
  
-   "请确保该文件存在并且您有权打开它。"  
  
#### 编写一条消息，又短又到点。  
 一条错误消息可以通知，解释，并提供解决方案但太罗嗦是否仍被忽略。 一种解决方案是使用渐进式公开具有详细信息按钮。 例如，为提供一个简短的描述\/解决方案，然后将详细信息按钮下的更多详细信息。 如果用户选择可以了解有关错误的详细信息，用户可以这样做。  
  
 应在消息中的语言:  
  
-   **域适当。**使用用户能够理解的语言。 尽管我们的客户都是开发人员，他们通常没有上下文和我们的术语。  
  
-   **特定。**避免含糊不清的用词并为所涉及对象的特定名称和位置。 例如，一条错误消息如"无效字符"不是很有用。 用于转换的字符? "找不到文件"。 哪些文件?  
  
-   **得体。**请不要责怪用户，或使它们羞愧感。 避免恶意或攻击性语言 \(终止、 执行和终止，致命的非法\)。 避免使用大写的文本，它通常被视为地大喊大叫并不是为可读。 不要使用幽默。  
  
-   **更正。**\(即使在 alpha 版\) 中使用正确的拼写和语法。 键入错误是很不专业和令人难堪。  
  
-   **上下文相关。**使用相应的按钮的文本。 避免"确定"按钮，而是使用"继续"或"是\/否"  
  
### 错误消息示例  
  
|好|错误|  
|-------|--------|  
|"您拨打的号码服务中已不存在。 请检查数以及重试或为操作符拨打 0。"|-   "错误 \(: 449\): 非法数字"<br />-   "此未处理的异常错误情况表示操作成功完成"。<br /><br /> ![Bad error message in Visual Studio](~/extensibility/ux-guidelines/media/0602-a_errordialog.png "0602\-a\_ErrorDialog")|  
  
## 访问帮助  
  
### 概述  
 除了 MSDN 中的文档，Visual Studio 用户具有多个访问点，以帮助用户在 UI 中。 若要确保这些接入点都始终可用，功能团队需要利用该环境所提供的帮助系统。 这些访问点是:  
  
-   **在对话框中的说明和补充性文本。**不提供方向或说明，在图面或在将鼠标悬停在信息提示图标上提供的用户界面上的静态文本。  
  
-   **F1 帮助** \(仅在编辑器中\)。 在 Visual Studio 编辑器中，用户可以相信，在任何时候，按 f1 即可将弹出一个帮助主题特定于当前所选内容。 确保与 f1 键关联的主题是适当和信息性。  
  
-   **指向帮助主题的超链接。**对话框、 工具窗口中或启动主题来帮助用户了解更多有关技术、 功能或有关如何完成某项任务的信息的设计图面内的超链接。  
  
-   **帮助器 UI 机制，例如智能标记和构建对话。**这些机制帮助用户了解 UI 元素，或帮助实现一个任务，例如智能标记或生成器对话框。  
  
-   **UI 帮助按钮** \(不推荐使用\)。 提供访问权限的相关的 F1 帮助主题的标题栏中可见的指示符。  
  
### Text  
  
#### 在对话框中的说明和补充文本  
 在对话框中，支持复杂的任务，可能需要为说明文本在 UI 中，通常提供顶部的对话框中或在复杂的控件附近。 请参阅 [UI 文本和术语](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology) 有关写作风格的详细信息。  
  
#### 信息提示  
 通常情况下，说明文本可能太长，放置在用户界面中的位置，或者可能仅对新用户，还觉得自己象有经验的用户的混乱有用。 在这种情况下，应为工具提示信息提示下放说明性\/信息性文本。  
  
 信息提示应放置在它们与相关，并且应使用特定的信息提示图标，也是按照不引人注意的控件附近明显。  
  
 ![InfoTip in Visual Studio](../../extensibility/ux-guidelines/media/0601-d_infotip.png "0601\-d\_InfoTip")  
  
 **在 Visual Studio 中的信息提示的示例**  
  
### 交互式帮助机制  
  
#### F1 帮助  
 是必需的 F1 帮助中的编辑器或设计图面上，但不是在其他地方在 Visual Studio 环境中。  
  
#### 指向帮助主题的超链接  
 超链接可以用于执行某项操作，IDE 中，导航或浏览器中启动的帮助。 请参阅 [UI 文本和术语](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology) 有关语言和 07.10.01 的详细信息按钮和视觉和布局的指南的超链接。  
  
#### 帮助 \(不推荐使用\) 的对话框标题栏中的 \[?\] 按钮  
 大多数情况下，对话框的标题栏中的帮助 \[?\] 按钮已被否决。 用户界面主题不再是模型的一部分我们的文档，并因此可能不会有相关的主题，以链接到。 从根本上来说，标题栏按钮一样 F1 帮助，，不再需要在对话框中。 在某些情况下，这仍可作为指示器有概念或过程的详细信息可用，尽管在较新的用户界面中更常用于超链接。  
  
##### 通过在环境创建的对话框  
 通过创建的许多命令行程序对话 **VBDialogBoxParam** 函数。 此共享的函数已更新，以帮助移动 **帮助** 从到对话框的按钮 **?** 按钮，同时保留的体系结构来向后兼容和可扩展。  
  
 具体而言， **VBDialogBoxParam** 函数查找其 ID 是一个按钮的对话框模板在 **IDHELP** \(9\) 或标签是 **帮助** 或 **\(& a\) 帮助**。 如果找到帮助按钮，则它会隐藏和 **WS\_EX\_CONTEXTHELP** 样式添加到对话框中，后者会将置于 **?** 对话框的标题栏中按钮。  
  
 创建对话框时，它将推送到堆栈上的对话框过程，并与名为预处理对话框 proc 调用对话框 **DialogPreProc**。 当 **?** 单击按钮时，将发送 **WM\_SYSCOMMAND** 的 **SC\_CONTEXTHELP** 到了对话框。**DialogPreProc** 捕获此命令并将这些更改到 **WM\_HELP** 消息传递到原始对话框处理器。  
  
 大多数环境创建对话框对对话框的帮助按钮。 显示对话框时，帮助按钮时，自动隐藏，并且只 **?** 按钮的工作方法。 如果 **?** 按钮会删除或在 Windows 中更改，此解决方案允许您快速将移回至原始的帮助按钮。  
  
 这种解决方案才可能会导致 bug 的四种假设:  
  
-   对话框的帮助按钮是 **IDHELP** \(9\)。  
  
-   隐藏帮助按钮时，对话框中查找正确。  
  
-   对话框中不能将替换其 winproc。  
  
-   对话框中未嵌入在另一个对话框。  
  
 如果您的对话框位于 msenv 内，也不使用 **VBDialogBoxParam**, ，调查利用 **VBDialogBoxParam** 实施您自己的处理程序之前。  
  
##### 通过其他包创建的对话框  
 您可以实现你自己的解决方案位于外部 msenv 的对话框。 在你的 VSPackage 中共享的对话框类，请考虑将该按钮移到标题栏或在每个对话框实现一个处理程序。 下面的代码是实现的一个框架以帮助您入门:  
  
```  
struct DLGPROCITEM { FARPROC proc; // The info used to create the dialog. DLGPROCITEM* procPrev; }; DLGPROCITEM* g_dlgProcStack = NULL; // A dialog starter/wrapper function is used to push the new // dialog proc to the top of our dialog proc stack. int SomeDialogStarterFunction(hinst, id, proc, etc) { if (g_dlgProcStack == NULL) { g_dlgProcStack = new DLGPROCITEM; g_dlgProcStack->procPrev = NULL; } else { DLGPROCITEM* procItem = new DLGPROCITEM; g_dlgProcStack->procPrev = g_dlgProcStack; g_dlgProcStack = procItem; } } // Pop this dialog proc off the dialog proc stack. DialogBoxIndirectParam...(...) { DLGPROCITEM* procItem = g_dlgProcStack->procPrev; delete g_dlgProcStack; g_dlgProcStack = procItem; } // A wrapper dialog procedure will allow us to capture the // SC_CONTEXTHELP button on the title bar from Windows and // forward it as a simple WM_HELP message back to the dialog. INT_PTR CALLBACK DialogPreProc(HWND hwndDlg, UINT uMsg, WPARAM wParam, LPARAM lParam) { if (uMsg == WM_SYSCOMMAND && wParam == SC_CONTEXTHELP) { uMsg = WM_HELP; wParam = 0; lParam = 0; } return CallWindowProc((WNDPROC)g_dlgProcStack->proc, hwndDlg, uMsg, wParam, lParam); }  
```  
  
##### 在托管代码中的帮助按钮  
 可以很容易在托管代码中重写窗口标题栏帮助按钮的默认行为。 下面是一个完整的演示应用程序，演示了此行为。 从本质上讲，您需要重写窗体的 **WndProc** 方法和关闭的 F1 帮助然后火灾的请求时 **SC\_CONTEXTHELP** 截获消息。  
  
```  
using System; using System.Windows.Forms; public class HelpForm : Form { private const int SC_CONTEXTHELP = 0xF180; private const int WM_SYSCOMMAND = 0x0112; public HelpForm() { this.ClientSize = new System.Drawing.Size(300, 250); this.HelpButton = true; this.MaximizeBox = false; this.MinimizeBox = false; this.Name = "HelpForm"; this.Text = "Help Form"; } protected override void WndProc(ref Message m) { if (m.Msg == WM_SYSCOMMAND && SC_CONTEXTHELP == (int)m.WParam) ShowHelp(); else base.WndProc(ref m); } private void ShowHelp() { MessageBox.Show("F1 Help goes here."); } [STAThread] static void Main() { Application.EnableVisualStyles(); Application.EnableRTLMirroring(); Application.Run(new HelpForm()); } }  
```  
  
## 请参阅  
 [字体和格式对 Visual Studio](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md)   
 [Visual Studio 的布局](../../extensibility/ux-guidelines/layout-for-visual-studio.md)   
 [通知和 Visual Studio 的进度](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md)