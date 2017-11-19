---
title: "Visual Studio 的 UX Essentials |Microsoft 文档"
ms.custom: 
ms.date: 04/26/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a793cf7a-f230-43ce-88d0-fa5d6f1aa9c7
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 368540b909536523515ea610e509b22600628f81
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ux-essentials-for-visual-studio"></a>Visual Studio 的 UX Essentials
## <a name="best-practices"></a>最佳实践  
  
### <a name="1-be-consistent-within-the-visual-studio-environment"></a>1.是在 Visual Studio 环境一致。  
  
-   请按照现有[交互模式](interaction-patterns-for-visual-studio.md)在外壳程序内。  
  
-   设计功能，使其与 shell 的可视语言一致和[编程工作要求](evaluation-tools-for-visual-studio.md)。  
  
-   它们存在时，请使用共享的命令并控制。  
  
-   了解 Visual Studio 层次结构以及如何建立上下文，并驱动器 UI。  
  
### <a name="2-use-the-environment-service-for-fonts-and-colors"></a>2.使用字体和颜色的环境服务。  
  
-   UI 应遵守当前[环境字体](fonts-and-formatting-for-visual-studio.md)设置，除非它公开用于在选项对话框的字体和颜色页中的自定义。  
  
-   UI 元素必须使用[VSColor 服务](colors-and-styling-for-visual-studio.md)，使用共享环境令牌或特定于功能的令牌。  
  
### <a name="3-make-all-imagery-consistent-with-the-new-vs-style"></a>3.使所有图像使用新的 VS 样式保持一致。  
  
-   按照 Visual Studio 图标、 标志符号和其他图形的设计原则。  
  
-   不要将文本放在图形元素。  
  
### <a name="4-design-from-a-user-centric-perspective"></a>4.设计从以用户为中心的角度来看。  
  
-   创建任务流之前在其中的各个功能。  
  
-   熟悉你的用户并在你规范中明确这一知识。  
  
-   当查看用户界面，将评估完成体验，以及详细信息。  
  
-   设计你的 UI，以便它仍然适用且而不考虑区域设置或语言吸引人。  
  
## <a name="screen-resolution"></a>屏幕分辨率  
  
### <a name="minimum-resolution"></a>最小分辨率  
 - Visual Studio dev14 中的最小解决方法是**1280 x 720**。 这意味着它是*可能*解析时，使用 Visual Studio，尽管它可能不是最佳用户体验。 就不能保证所有方面将都可在低于 1280 x 720 的解决方法。  
  
 - Visual Studio 的目标解决方法是**1366x768**。 这是从该处我们保证的最低分辨率*良好*用户体验。

 - 应为初始对话框高度**小于 700 像素**，因此它适合 96 dpi IDE 框架的最小分辨率。
  
### <a name="high-density-displays"></a>高密度显示  
 Visual Studio 中的 UI 必须适用于所有 DPI 缩放 Windows 支持现成的因素： 150%、 200%和 250%。  
  
## <a name="anti-patterns"></a>反模式  
 Visual Studio 包含 UI 的许多的示例，请按照我们的指导原则和最佳做法。 为了保持一致，开发人员通常借用从产品的 UI 设计模式类似于它们正在生成。 虽然这是一个不错的方法，可帮助我们驱动器的用户交互和可视化设计保持一致，我们执行有时提供与不满足我们的指导原则由于计划约束或脱离优先级的一些详细信息的功能。 在这些情况下，我们不希望对其中一种"反模式"的副本的团队因为它们数量不正确或不一致的 UI，Visual Studio 环境中的不断增加。  
  
### <a name="required-fieldssettings-shown-in-error-state-by-default"></a>默认情况下处于错误状态显示的所需的字段/设置  
  
#### <a name="feature-team-goals"></a>功能团队目标  
  
-   此警告用户他们添加了必须配置的元素。  
  
-   引起用户对需要输入的区域。  
  
#### <a name="anti-pattern-solution"></a>反模式解决方案  
 只要用户已开始操作，它们具有完成任务前，立即将关键停止图标放置在旁需要配置的区域。  
  
#### <a name="example-manifest-designer-declarations"></a>示例： 清单设计器声明  
 立即将声明添加到列表将将其放在错误状态，保存，直到用户设置所需的属性。  
  
 在这种情况下，没有其他问题因为用于警报的图标会包含"&times;"图标，因此无法使用常见的删除图标旁边。 因此，UI 使用删除按钮，更不灵活的控件。  
  
 ![UI 置于错误状态默认情况下是 Visual Studio 反模式。] (../../extensibility/ux-guidelines/media/manifestdesignererrordeclarationsanti-pattern.png "ManifestDesignererrordeclarationsanti 模式")<br />UI 置于错误状态默认情况下是 Visual Studio 反模式。
  
#### <a name="alternatives"></a>替代项  
 更好的解决方案，此问题是：  
  
-   允许用户添加的声明而不发出警告，然后立即移动在该项上设置属性。  
  
-   添加警告图标 （黄金三角形） 时焦点将从移动项，如将另一个声明添加到列表，或尝试更改设计器中的选项卡。  
  
-   如果用户尝试在设置属性的任何声明之前更改选项卡，弹出一个对话框，该对话框说明应用程序将不生成 （或任何影响） 直到警告都得到解决。 如果用户关闭对话框并更改选项卡仍要然后图标 （关键或警告，根据需要） 添加到声明选项卡。  
  
### <a name="multiple-clicks-to-dismiss-ui"></a>多个单击以取消 UI  
  
#### <a name="feature-team-goals"></a>功能团队目标  
 不允许用户以关闭而不显示的说明文本第一个 UI。  
  
#### <a name="anti-pattern"></a>反模式  
 在 VS UI 中的不同位置插入视频的链接的团队决定针对常见的模式"&times;"作为的关闭按钮和工具提示说明指定的用户体验，，而是实现下拉列表和"不再次显示"链接。  

#### <a name="example-video-links-in-team-explorer"></a>在团队资源管理器中的示例： 视频链接
强制用户在解除 UI 之前阅读解释性文本是 Visual Studio 中的反模式。 正确设计、 视频链接应显示带有其他信息的工具提示上悬停时，然后单击"&times;"应关闭而无需进一步交互消息。


 ![解释性文本反 &#45; 模式 &#45;不正确](../../extensibility/ux-guidelines/media/incorrectuseofmultipleclicks.png "Incorrectuseofmultipleclicks")<br />视频的链接不正确模式
  
#### <a name="result"></a>结果  
 而不是简单的关闭按钮 （一次单击），强制用户使用两次单击只需关闭显示的视频的链接的每个位置中的用户界面。  
  
#### <a name="alternatives"></a>替代项  
 这种情况下的正确设计可以访问 Internet 资源管理器、 Office 和 Visual Studio 的常见模式： 悬停时，用户可以看到的工具提示说明并一次单击隐藏用户界面。  
  
 ![解释性文本反 &#45; 模式 &#45;正确](../../extensibility/ux-guidelines/media/explanatorytextanti-pattern-correct.png "Explanatorytextanti 模式更正")<br />正确的视频链接模式
  
### <a name="using-command-bars-for-settings"></a>使用命令栏设置  
 **图 A**表示此反模式： 将适用于以外的其他命令的命令按钮下方的设置。 在此草有除了启动调试的命令-如在浏览器、 启动但不调试，和单步执行视图-将遵从所选的设置。  

  ![答： 图命令栏反模式](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figurea.png "Commandbaranti 模式 FigureA")<br />答： 图命令栏反模式
  
 中所示稍好，但仍不将此类型的设置放在工具栏中，**图 B**。拆分按钮占用较少空间，并因而改善通过下拉列表，而这两个设计仍在使用工具栏以提升内容不是真正的命令。  
 
 ![图 b： 好，但仍命令栏反模式](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figureb.png "Commandbaranti 模式 FigureB")<br />图 b： 稍好，但仍命令栏反模式
 
  在正确的方法中所示**图 C**，设置绑定到的一系列命令。 没有设置任何全局设置，我们要只需要四个命令之间切换。 这是中的工具栏中的命令都可接受的唯一情形。 

 ![图 c： 更正 Visual Studio 命令栏模式的使用](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figurec.png "Commandbaranti 模式 FigureC")<br />图 c： 正确使用 Visual Studio 命令栏模式
   
### <a name="control-anti-patterns"></a>控制反模式  
 若干反模式是只是不正确的使用情况或表示法的控件或组控件。  
  
#### <a name="underlining-used-as-a-group-label-not-a-hyperlink"></a>使用作为组标签，而不是超链接的下划线  
 下划线文本应仅用于超链接。  
  
 **错误：**    
 ![不是超链接的带下划线的文本是 Visual Studio 反模式。] (../../extensibility/ux-guidelines/media/0102-g_grouplabelincorrect.png "0102 g_GroupLabelIncorrect")<br />不是超链接的带下划线的文本是 Visual Studio 反模式。
  
 **好：**   
 ![正确设置样式，非超链接文本将显示未修饰在环境字体。] (../../extensibility/ux-guidelines/media/0102-h_grouplabelcorrect.png "0102 h_GroupLabelCorrect")<br />正确设置样式，非超链接文本将显示未修饰在环境字体。
  
#### <a name="clicking-on-a-check-box-results-in-a-pop-up-dialog"></a>单击在弹出对话框中的复选框结果  
 立即单击"发布 Windows Azure 应用程序"向导的"启用为所有角色的远程桌面"复选框将显示弹出对话框中，Visual Studio 反模式。 此外，复选框字段未填充带一个复选框后，选择另一种交互反模式。  
  
 ![提出一个对话框，单击复选框后 Visual Studio 反模式。] (../../extensibility/ux-guidelines/media/0102-i_checkboxpopup.png "0102 i_CheckboxPopup")<br />提出一个对话框，单击复选框后 Visual Studio 反模式。
  
### <a name="hyperlink-anti-patterns"></a>超链接反模式  
 下面的示例包含两个反模式。  
  
1.  悬停时打开红色前台意味着未使用正确的共享的颜色从字体服务。  
  
2.  "了解详细信息"不到概念主题的链接的相应文本。 用户的目标是不了解详细信息，它是了解他们选择的后果。  
  
 ![忽略颜色服务，并使用"了解详细信息"的超链接是 Visual Studio 反模式。] (../../extensibility/ux-guidelines/media/0102-j_hyperlinkincorrect.png "0102 j_HyperlinkIncorrect")<br />忽略颜色服务，并使用"了解详细信息"的超链接是 Visual Studio 反模式。  
  
 **更好的解决方案：**会带来问题，用户将询问通过单击的链接。  
  
-   Windows Azure 服务是如何工作的？  
  
-   何时需要 Windows Azure 移动服务项目？  
  
#### <a name="using-click-here-for-links"></a>使用"单击此处"链接的  
 应自我描述的超链接。 它是要使用"单击此处"反模式或任何类似的变体。  
  
 **错误：** "单击此处以说明有关如何创建新项目。"
  
 **良好：** "如何创建新项目？"