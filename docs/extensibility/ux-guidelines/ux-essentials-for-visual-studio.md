---
title: "Visual Studio 的用户体验 Essentials |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a793cf7a-f230-43ce-88d0-fa5d6f1aa9c7
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 7f10e2cefc0986a2457cc61945a60acfd1a4ef78
ms.lasthandoff: 02/22/2017

---
# <a name="ux-essentials-for-visual-studio"></a>Visual Studio 的用户体验 Essentials
## <a name="best-practices"></a>最佳实践  
  
### <a name="1-be-consistent-within-the-visual-studio-environment"></a>1.在 Visual Studio 环境中保持一致。  
  
-   请按照在命令行界面中的现有交互模式。  
  
-   设计功能与外壳的 visual 语言和耕耘所得到的需求保持一致。  
  
-   如果它们存在，使用共享的命令和控件。  
  
-   了解 Visual Studio 层次结构以及如何建立上下文，并推动 UI。  
  
### <a name="2-use-the-environment-service-for-fonts-and-colors"></a>2.使用字体和颜色的环境服务。  
  
-   除非公开为自定义在选项对话框的字体和颜色页中，UI 应遵从的当前环境字体设置。  
  
-   UI 元素必须使用 VSColor 服务中，使用共享的环境令牌或特定于功能的令牌。  
  
### <a name="3-make-all-imagery-consistent-with-the-new-vs-style"></a>3.使所有图像与新的 VS 样式保持一致。  
  
-   请按照图标、 字形和其他图形的 Visual Studio 设计原则。  
  
-   不要将文本放在图形元素。  
  
### <a name="4-design-from-a-user-centric-perspective"></a>4.设计从以用户为中心的角度来看。  
  
-   创建任务流之前在其中的各个功能。  
  
-   熟悉您的用户和您规范中明确知道密码。  
  
-   在检查用户界面时，评估的完整体验以及详细信息。  
  
-   设计你的 UI，以便它仍然适用且吸引人，而不考虑区域设置或语言。  
  
## <a name="screen-resolution"></a>屏幕分辨率  
  
### <a name="minimum-resolution"></a>最小分辨率  
 Visual Studio dev14 中的最小分辨率为 1280 x 1024。 这意味着它是*可能*解析时，使用 Visual Studio，尽管它可能不是最佳用户体验。 就不能保证所有方面，都可在分辨率低于 1280 x 1024。  
  
 初始对话框大小不应超过 1000年像素高度以便容纳在 IDE 中最小分辨率为 96 dpi 的帧。  
  
### <a name="high-density-displays"></a>高密度显示  
 在 Visual Studio 中的用户界面必须也在所有 DPI 缩放因素 Windows 支持在初始状态下工作︰ 150%、 200%和 250%。  
  
## <a name="anti-patterns"></a>反模式  
 Visual Studio 包含许多 UI 的示例，它们遵循我们的指导原则和最佳实践。 为了保持一致，开发人员通常借用产品 UI 设计模式类似于他们的构建。 虽然这是一个不错的方法，可帮助我们驱动器需要用户交互和可视化设计的一致性，我们有时提供功能和一些未满足我们的指导原则由于计划限制或未脱离优先顺序的详细信息。 在这些情况下，我们不希望复制这些"反模式"的团队因为它们数量不正确或不一致的用户界面，在 Visual Studio 环境中的不断增加。  
  
### <a name="required-fieldssettings-shown-in-error-state-by-default"></a>显示处于错误状态默认情况下所需的字段/设置  
  
#### <a name="feature-team-goals"></a>功能团队的目标  
  
-   警告用户他们添加必须配置的元素。  
  
-   绘制到哪些区域需要输入的用户的注意力。  
  
#### <a name="anti-pattern-solution"></a>反模式解决方案  
 只要用户启动的操作，它们已完成任务之前，立即将关键性停止图标放置在需要配置的区域旁。  
  
#### <a name="example-manifest-designer-declarations"></a>示例︰ 清单设计器中声明  
 立即向列表添加一个声明将其置于错误状态，保存，直到用户设置所需的属性。  
  
 在这种情况下，没有其他问题因为牡 ボ 一起使用的图标包含一个"x"，因此对常见删除图标不能使用其旁边。 因此，UI 使用一个删除按钮，更笨拙的控件。  
  
 ![清单设计器错误声明反模式](../../extensibility/ux-guidelines/media/manifestdesignererrordeclarationsanti-pattern.png "ManifestDesignererrordeclarationsanti 模式")  
  
 **UI 置于错误状态默认情况下是 Visual Studio 反模式。**  
  
#### <a name="alternatives"></a>替代方法  
 更好的解决方案，此问题是︰  
  
-   允许用户添加的声明而不发出警告，然后立即移动项上设置属性。  
  
-   添加警告图标 （金牌三角形） 时焦点从移开该项目，如将另一个声明添加到列表，或尝试更改设计器中的选项卡。  
  
-   如果用户尝试更改选项卡上的任何声明中设置属性之前，弹出一个对话框，说明该应用程序将不生成 （或任何含义） 直到警告都得到解决。 如果用户关闭对话框并更改选项卡仍要则图标 （关键或警告，视情况而定） 添加到声明选项卡。  
  
### <a name="forcing-the-user-to-read-text-before-dismissing-ui"></a>强制用户之前需要阅读的文本关闭用户界面  
  
#### <a name="feature-team-goals"></a>功能团队的目标  
 不允许用户以取消用户界面而不首先看到说明文本。  
  
#### <a name="anti-pattern"></a>反模式  
 团队决定针对 X 的常见模式与用户界面内的不同位置插入视频链接关闭按钮和工具提示说明指定的用户体验，并改为实现下拉列表中，"不要再显示"链接。  
  
 ![解释性文本反模式-正确](../../extensibility/ux-guidelines/media/incorrectuseofmultipleclicks.png "Incorrectuseofmultipleclicks")  
  
 **不正确︰ 强制用户之前需要阅读说明文字关闭用户界面是在 Visual Studio 内的反模式。**  
  
#### <a name="result"></a>结果  
 而不是简单的关闭按钮 （一次单击），用户会强制使用两次单击来只是解除视频的链接将显示每个位置中的用户界面。  
  
#### <a name="alternatives"></a>替代方法  
 这种情况下正确的设计是到 Internet Explorer、 Office 和 Visual Studio 遵循通用模式︰ 悬停时，用户可以看到工具提示说明，并一次单击隐藏用户界面。  
  
 ![解释性文本反模式-正确](../../extensibility/ux-guidelines/media/explanatorytextanti-pattern-correct.png "Explanatorytextanti 模式纠正")  
  
 **正确︰ 设计时，视频链接应悬停时，显示带有其他信息的工具提示并单击"X"应关闭该消息而无需进一步交互。**  
  
### <a name="using-command-bars-for-settings"></a>使用命令栏的设置  
 ![命令栏反模式-图 A](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figurea.png "Commandbaranti 模式 FigureA")  
  
 **图 a︰ 命令栏反模式**  
  
 **图 A**表示此反模式︰ 将适用于以外的其他命令的命令按钮之下的设置。 在这段代码中，有一些除了启动调试命令 — 如在浏览器、 启动不调试，以及单步执行视图 —，将考虑所选的设置。  
  
 ![命令栏反模式-图 B](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figureb.png "Commandbaranti 模式 FigureB")  
  
 **图 b︰ 好一些，但仍命令栏反模式**  
  
 如中所示稍好一些，但仍不将这种类型的设置放在工具栏中，**图 B**。拆分按钮占用较少空间，并因此是一项改进，通过下拉列表，而这两个设计也仍使用工具栏以促进这不是真正的命令。  
  
 ![命令栏反模式-图 C](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figurec.png "Commandbaranti 模式 FigureC")  
  
 **图 c︰ 正确使用 Visual Studio 命令栏模式**  
  
 在**图 C**，设置绑定到一系列命令。 没有设置没有全局设置，我们只四个命令之间进行切换。 这是其中的工具栏中的命令是可接受的唯一情况。  
  
### <a name="control-anti-patterns"></a>控制反模式  
 一些反模式是用法只是不正确或表示法的控件或控件组。  
  
#### <a name="underlining-used-as-a-group-label-not-a-hyperlink"></a>使用作为组标签，而不是超链接的下划线  
 下划线的文本应仅用于超链接。  
  
 **错误︰**  
  
 ![组标签中的下划线反模式](../../extensibility/ux-guidelines/media/0102-g_grouplabelincorrect.png "0102 g_GroupLabelIncorrect")  
  
 **不是超链接的带下划线的文本是 Visual Studio 反模式。**  
  
 **很好︰**  
  
 ![组标签 （正确） 中的下划线反模式](../../extensibility/ux-guidelines/media/0102-h_grouplabelcorrect.png "0102 h_GroupLabelCorrect")  
  
 **正确设置样式，非超链接文本将显示未修饰在环境字体。**  
  
#### <a name="clicking-on-a-check-box-results-in-a-pop-up-dialog"></a>单击在弹出对话框中的复选框结果  
 立即单击"启用为所有角色的远程桌面"复选框，在"发布 Windows Azure 应用程序"向导中显示弹出对话框中，Visual Studio 反模式。 此外，复选框字段未填充有一个复选框被选中后另一种交互反模式。  
  
 ![复选框弹出反模式](../../extensibility/ux-guidelines/media/0102-i_checkboxpopup.png "0102 i_CheckboxPopup")  
  
 **单击复选框，这是 Visual Studio 反模式后，将打开一个对话框。**  
  
### <a name="hyperlink-anti-patterns"></a>超链接反模式  
 下面的示例包含两个反模式。  
  
1.  红色开启悬停时的前景意味着未使用正确的共享的颜色从字体服务。  
  
2.  "了解详细信息"不是指向概念性主题的链接的相应文本。 用户的目标是不了解它是了解他们选择的后果。  
  
 ![超链接反模式](../../extensibility/ux-guidelines/media/0102-j_hyperlinkincorrect.png "0102 j_HyperlinkIncorrect")  
  
 **忽略颜色服务，并使用"了解"超链接是 Visual Studio 反模式。**  
  
 **更好的解决方案︰**会带来问题，用户会询问通过单击的链接。  
  
-   Windows Azure 服务是如何工作的？  
  
-   何时需要 Windows Azure 移动服务项目？  
  
#### <a name="using-click-here-for-links"></a>使用"单击此处"链接  
 超链接应该是可以自我描述。 它是反模式使用"单击此处"或任何类似的变体。  
  
 **错误︰** "单击此处查看有关如何创建一个新项目的说明进行操作。"  
  
 **良好︰** "如何创建一个新的项目？"
