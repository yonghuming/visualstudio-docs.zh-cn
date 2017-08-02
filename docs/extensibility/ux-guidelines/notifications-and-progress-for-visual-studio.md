---
title: "通知和进度 for Visual Studio |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f0ef65e9-0f1f-45f4-9f25-6e2398691168
caps.latest.revision: 6
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
ms.openlocfilehash: 1f7823754601161200edafdce998ebe9aeab2723
ms.lasthandoff: 02/22/2017

---
# <a name="notifications-and-progress-for-visual-studio"></a>通知和 Visual Studio 的进度
##  <a name="a-namebkmknotificationsystemsa-notification-systems"></a><a name="BKMK_NotificationSystems"></a>通知系统  
  
### <a name="overview"></a>概述  
 有多种方法以通知用户发生了什么情况在 Visual Studio 中有关其软件开发任务。  
  
 在实现任何种类的通知︰  
  
-   **将通知发送到所需的最低数量保持**有效数字。 通知消息应该应用于大多数 Visual Studio 用户或用户的特定功能/功能区域。 过多地使用通知可能 sidetrack 用户或降低，并让人察觉的易于使用的系统。  
  
-   **确保您提供清晰、 可操作的消息的不同**用户可以使用来调用合适的上下文中进行更复杂的选择和采取进一步操作。  
  
-   **相应地出现同步和异步消息。** 同步通知指示出现需要立即引起注意，例如，当 web 服务崩溃或代码会引发异常。 这些情况下立即以请求其输入，例如在一个模式对话框的方式，应通知用户。 异步通知是这些用户应该了解，但不是要求起作用时立即，如网站部署在生成操作完成时或完成。 这些消息应该更环境并不会中断用户的任务流。  
  
-   **使用模式对话框仅在需要以防止用户采取进一步操作时**之前确认消息或显示在对话框中的决策。  
  
-   **删除环境的通知时它们将不再有效。** 不需要用户如果它们已采取措施来解决的问题已得到有关通知，则关闭通知。  
  
-   **请注意，通知可能导致错误关联。** 用户可能会认为，一个或多个其操作触发一条通知时实际上没有任何因果关系。 清除为上下文、 触发器和通知的源有关的通知消息。  
  
### <a name="choosing-the-right-method"></a>选择正确的方法  
 使用此表来帮助您选择正确的方法以通知邮件的用户。  
  
|方法|使用|请不要使用|  
|------------|---------|----------------|  
|[模式错误消息对话框](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ModalErrorMessageDialogs)|在继续之前需要用户响应时使用。|无需阻止用户和中断其流时，不要使用。 避免使用模式对话框，如有可能要以另一台、 较少受侵入的方式显示的消息。|  
|[IDE 状态栏会显示](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_IDEStatusBar)|环境的文本信息与状态有关的进程时使用。|不单独使用。 最好一起使用与另一种反馈机制。|  
|[嵌入式信息栏](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_EmbeddedInfobar)|在工具窗口或文档窗口中，使用通知进度、 错误状态、 结果，和/或可操作信息。|如果信息与放置信息栏的位置无关，不要使用。<br /><br /> 不要使用文档/工具窗口之外。|  
|[鼠标光标会改变](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_MouseCursorChanges)|可用于通知进程正在进行。 此外用于通知有更改鼠标中的状态，如鼠标光标拖放时正在进行或，位于某种模式，如绘制模式。|不要使用短进度更改或 fluttering 的光标是否可能 （例如，当取决于较长正在运行的进程而不是整个过程的部分）。|  
|[进度指示器](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_NotSysProgressIndicators)|当你需要报告进度 （确定的或不确定） 时使用。 有多个进度指示器类型和每个特定的用量。 请参阅[进度指示器](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ProgressIndicators)。||  
|[Visual Studio 通知窗口](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_VSNotificationsToolWindow)|通知窗口不是公开可扩展的。 但是，它用于进行通信的一系列有关 Visual Studio 中，其中包括与您的许可证和信息性通知的更新到 Visual Studio 或包的关键问题的消息。|不要使用为其他类型的通知。|  
|[错误列表](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ErrorList)|当直接与用户的当前打开的解决方案时遇到问题 （错误/警告/信息） 相关的问题时，他们可能需要该代码对其执行操作。<br /><br /> 这可能包括，例如︰<br /><br /> 编译器消息 （错误/警告/信息）<br /><br /> 的有关代码代码分析器/诊断消息<br /><br /> -建立消息<br /><br /> 可能适合于与项目或解决方案文件中，相关的问题，但首先考虑的解决方案资源管理器指示。|不要使用为不具有与用户的打开的解决方案代码的任何关系项。|  
|编辑器通知︰ 灯泡图标|当您具有修补程序可用于修补在打开的文件中存在的问题时使用。<br /><br /> 请注意灯泡图标中也应使用用于承载对按需、 重构功能，如用户的代码执行，但这种情况下将不会出现"通知方式。"的快速操作|不要使用为打开的文件不具有任何关系项。|  
|编辑器通知︰ 波形曲线|使用其 open 代码 （例如，红色的波浪线有错误） 的特定范围的问题向用户发出警报。|不要使用为特定范围的打开的代码不相关的项。|  
|[嵌入式的状态栏](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_EmbeddedStatusBars)|用于提供与相关的内容或上下文特定的工具窗口、 文档窗口或对话框窗口中的进程的状态。|请使用面向一般产品通知、 进程或项中的特定时段内没有任何关系的内容。|  
|[Windows 任务栏通知](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_WindowsTray)|用来呈现进程外的进程的通知或伴生应用程序。|不要使用与 IDE 相关的通知。|  
|[通知气泡](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_NotificationBubbles)|使用远程进程的通知或更改**之外**的 IDE。|请不要用于作为一种方式通知用户进程**内**IDE。|  
  
### <a name="notification-methods"></a>通知方法  
  
####  <a name="a-namebkmkmodalerrormessagedialogsa-modal-error-message-dialogs"></a><a name="BKMK_ModalErrorMessageDialogs"></a>模式错误消息对话框  
 模式错误消息对话框用于显示错误消息，要求用户确认或操作。  
  
 ![模式错误消息](~/extensibility/ux-guidelines/media/0901-01_modalerrormessage.png "0901年&01;_ModalErrorMessage")  
  
 **模式错误消息对话框提醒用户数据库无效的连接字符串**  
  
####  <a name="a-namebkmkidestatusbara-ide-status-bar"></a><a name="BKMK_IDEStatusBar"></a>IDE 状态栏会显示  
 用户注意到状态栏文本的可能性将关联到其全能计算机体验和与 Windows 平台特定的体验。 Visual Studio 客户群往往是这两个方面方面具有丰富经验，但即使知识渊博的 Windows 用户可能会缺失状态栏中的更改。 因此，状态栏是最适合用于提供信息之目的或作为冗余的提示信息的信息显示在其他位置。 在对话框中或在通知工具窗口中，应提供任何类型的用户必须立即解决的关键信息。  
  
 Visual Studio 状态栏旨在允许多种类型的信息将会显示。 它分为的反馈、 设计器、 进度条、 动画和客户端区域。  
  
 反馈区域和设计器区域始终是可见的。 进度条和动画区域始终是动态的、 基于用户上下文。 设计器区域中具有静态宽度由从随附的短信的资源提取字符串的长度。 这样，本地化而无需代码的更改调整列宽。 为英语，此字符串的宽度大约为 220 像素。 设计器区域的通常行为且反馈区域可以吸收各种剩余的空间。  
  
 状态栏还着色通信各种 IDE 状态更改，例如当 IDE 处于调试模式下通过添加视觉效果和功能的值。  
  
 ![IDE 状态栏颜色更改](~/extensibility/ux-guidelines/media/0901-02_idestatusbar.png "0901年&02;_IDEStatusBar")  
  
 **IDE 状态栏的颜色**  
  
####  <a name="a-namebkmkembeddedinfobara-embedded-infobar"></a><a name="BKMK_EmbeddedInfobar"></a>嵌入式信息栏  
 可以在文档窗口或工具窗口的顶部使用一个信息栏，用于通知状态或条件的用户。 它还可以提供的命令，以使用户可以轻松地执行操作的方法。 信息栏是一个标准外壳控件。 避免创建您自己，它将执行操作并显示在 IDE 中与其他人不一致。 请参阅[信息栏](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars)有关实现详细信息和使用情况的指导。  
  
 ![嵌入式信息栏](~/extensibility/ux-guidelines/media/0901-03_embeddedinfobar.png "0901年&03;_EmbeddedInfobar")  
  
 **一个信息栏嵌入在文档窗口中，警报 IDE 是历史调试模式下，编辑器将不会响应相同的方式与在标准调试模式下的用户。**  
  
####  <a name="a-namebkmkmousecursorchangesa-mouse-cursor-changes"></a><a name="BKMK_MouseCursorChanges"></a>鼠标光标会改变  
 当将鼠标光标更改，使用绑定到 VSColor 服务，并且已与游标相关联的颜色。 光标发生变化，可用于指示正在进行的操作，以及命中的区域用户悬停的目标，可以拖动、 放置到，或用来选择某一对象的位置。  
  
 仅当所有可用的 CPU 时间必须保留对于操作，防止用户表达任何进一步的输入时，请使用忙/等待鼠标光标。 与编写良好的应用程序使用多线程处理的大多数情况下，当将阻止用户执行其他操作的时间应该很少见。  
  
 请记住光标发生变化，可按所提供冗余信息提示提供其他位置。 不依赖于作为至关重要，用户必须解决的唯一方式尤其是在尝试传递的内容时与用户进行通信的光标更改。  
  
####  <a name="a-namebkmknotsysprogressindicatorsa-progress-indicators"></a><a name="BKMK_NotSysProgressIndicators"></a>进度指示器  
 进度指示器很重要，在需要超过几秒钟后才完成的过程将用户提供反馈。 可以显示进度指示器的就地 （附近正在进行的操作的启动点），在嵌入的状态栏中、 在模式对话框中，或在 Visual Studio 状态栏中。 请按照中的指导[进度指示器](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ProgressIndicators)有关它们的使用和实现。  
  
####  <a name="a-namebkmkvsnotificationstoolwindowa-visual-studio-notifications-window"></a><a name="BKMK_VSNotificationsToolWindow"></a>Visual Studio 通知窗口  
 Visual Studio 通知窗口中会通知开发人员有关的授权、 环境 (Visual Studio)、 扩展和更新。 用户可以消除各个通知或者可以选择忽略某些类型的通知。 在中管理的已忽略通知列表**工具&1;> 选项**页。  
  
 通知窗口不是当前可扩展的。  
  
 ![Visual Studio 通知窗口](~/extensibility/ux-guidelines/media/0901-06_vsnotificationswindow.png "0901年&06;_VSNotificationsWindow")  
  
 **Visual Studio 通知工具窗口**  
  
####  <a name="a-namebkmkerrorlista-error-list"></a><a name="BKMK_ErrorList"></a>错误列表  
 错误列表中的通知指示错误和警告的编译过程中发生和或生成过程中，并允许用户在该特定的代码错误的代码中导航。  
  
 ![错误列表](~/extensibility/ux-guidelines/media/0901-08_errorlist.png "0901年&08;_ErrorList")  
  
 **在 Visual Studio 中的错误列表**  
  
####  <a name="a-namebkmkembeddedstatusbarsa-embedded-status-bars"></a><a name="BKMK_EmbeddedStatusBars"></a>嵌入式的状态栏  
 IDE 状态栏是动态的使用其客户端区域上下文设置为活动文档窗口和更新用户的上下文和/或系统响应上的信息，因为很难维护连续显示信息或使对长期异步进程的状态。 例如，IDE 状态栏会显示不适合的多个运行和/或立即采取行动的项选择的测试运行结果的通知。 请务必保留此类上下文中的用户进行的选择，或将启动一个进程的文档或工具窗口的状态信息。  
  
 ![嵌入式的状态栏](~/extensibility/ux-guidelines/media/0901-09_embeddedstatusbar.png "0901年&09;_EmbeddedStatusBar")  
  
 **在 Visual Studio 中的嵌入式的状态栏**  
  
####  <a name="a-namebkmkwindowstraya-windows-tray-notifications"></a><a name="BKMK_WindowsTray"></a>Windows 任务栏通知  
 Windows 通知区域是旁边系统时钟在 Windows 任务栏上。 很多实用程序和软件组件提供此区域中的图标，以便用户可以获得系统级任务，如更改屏幕分辨率或获取软件更新的上下文菜单。  
  
 在 Visual Studio 通知中心，不在 Windows 通知区域中不应会出现环境级别通知。  
  
####  <a name="a-namebkmknotificationbubblesa-notification-bubbles"></a><a name="BKMK_NotificationBubbles"></a>通知气泡  
 通知气泡可作为信息性编辑器/设计器中或作为 Windows 通知区域的一部分出现。 用户感觉这是一项优势为非关键通知这些气泡为更高版本，它们可以解决的问题。 气泡都不适合于用户必须立即解决的关键信息。 如果您在 Visual Studio 中使用通知气泡，请按照[Windows 桌面通知气泡指南](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742472\(v=vs.85\).aspx)。  
  
 ![通知气泡](~/extensibility/ux-guidelines/media/0901-07_notificationbubbles.png "0901年&07;_NotificationBubbles")  
  
 **用于 Visual Studio 的 Windows 通知区域中的通知气泡**  
  
##  <a name="a-namebkmkprogressindicatorsa-progress-indicators"></a><a name="BKMK_ProgressIndicators"></a>进度指示器  
  
### <a name="overview"></a>概述  
 进度指示器是一个用于提供用户反馈的通知系统的一个重要部分。 流程和操作将完成时，他们会告诉用户。 熟悉的指示器类型包括进度条、 旋转游标和动画的图标。 类型和进度指示器的位置取决于上下文，包括报告的内容和多长时间的进程或操作所需完成。  
  
#### <a name="factors"></a>因素  
 要确定哪个指示器类型是合适的您需要确定下列因素。  
  
1.  **计时︰**操作所花的时间长度  
  
2.  **模态︰**操作是模式适合环境 （锁定 UI 过程完成之前）  
  
3.  **持续性/暂时的︰**进度的最终结果是否需要在更高版本时进行报告和/或查看  
  
4.  **确定/不确定︰**可计算的操作结束时间和进度  
  
5.  **图形/Textual 位置︰**的进度或进程是否在一条消息或特定的控件，如树控件的主体中捕获的内联  
  
6.  **邻近︰**是否进度应在紧靠它与 UI 中。 （例如，可以是在状态栏，它可能远，或没有要在启动进程的按钮附近？）  
  
#### <a name="determinate-progress"></a>确定的进度  
  
|进度类型|何时以及如何使用|备注|  
|-------------------|-------------------------|-----------|  
|（确定） 的进度栏|预期的持续时间&1;>&5; 秒。<br /><br /> 可能包括文本说明的过程的详细信息。|**不**嵌入到动画的文本。|  
|信息栏|与上下文的用户界面相关联的消息传递。 请参阅[信息栏](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars)。<br /><br /> 可能包括文本说明的过程的详细信息。|**不**需要指示多个进程时使用多个信息栏。 请改用堆积的进度栏。|  
|输出窗口|瞬态通知︰ 该用户希望应用程序级别的流程**查看**完成此操作后的详细信息。|**不**如果用户将需要更高版本引用数据使用。|  
|日志文件|与在情况下 intransient 通知成对使用，对重要时**保存**完成此操作后的详细信息。||  
|状态栏|瞬态通知︰ 应用程序级别的流程该用户将**不需要**完成此操作后的详细信息。<br /><br /> 带有嵌入的进度条。<br /><br /> 可能包括文本说明的过程的详细信息。||  
  
#### <a name="indeterminate-progress"></a>不确定的进度  
  
|进度类型|何时以及如何使用|备注|  
|-------------------|-------------------------|-----------|  
|（不确定） 的进度栏|预期的持续时间&1;>&5; 秒。<br /><br /> 可能包括文本说明的过程的详细信息。|**不**嵌入到动画的文本。|  
|Ants （动画水平点）|到服务器的往返过程。<br /><br /> 在父容器的顶部放置近点的上下文。|**不**如果没有作为其父级的整个容器，请使用。|  
|微调框 （进度环）|进程关联的上下文的用户界面，或其中的空间是一个考虑因素。<br /><br /> 可能包括文本说明的过程的详细信息。||  
|信息栏|与上下文的用户界面相关联的消息传递。 请参阅[信息栏](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars)。|**不**需要指示多个进程时使用多个信息栏。 请改用堆积的进度栏。|  
|输出窗口|瞬态通知︰ 该用户将需要应用程序级别的流程**查看**完成此操作后的详细信息。|**不**用于需要在会话之间保持的信息。|  
|日志文件|与在情况下 intransient 通知成对使用，对重要时**保存**完成此操作后的详细信息。||  
|状态栏|瞬态通知︰ 应用程序级别的流程该用户将**不需要**完成此操作后的详细信息。<br /><br /> 包含嵌入的进度栏。<br /><br /> 可能包括文本说明的过程的详细信息。||  
  
### <a name="progress-indicator-types"></a>进度指示器类型  
  
#### <a name="progress-bars"></a>进度栏  
  
##### <a name="indeterminate"></a>不确定  
 ![不确定的进度栏](~/extensibility/ux-guidelines/media/0901-04_indeterminate.png "0901年&04;_Indeterminate")  
  
 **不确定的进度栏**  
  
 "不确定"意味着某项操作的总体进度或无法确定过程。 使用不确定的进度条为需要一段时间的不受限制的操作或访问未知的数量的对象。 使用的文本说明伴随发生了什么情况。 使用超时功能赋予边界访问基于时间的操作。 不确定的进度栏使用动画以显示进度操作正在进行，但不提供任何其他信息。 不要选择仅基于单独的准确性可能缺乏不确定的进度栏。  
  
##### <a name="determinate"></a>确定  
 ![确定的进度栏](~/extensibility/ux-guidelines/media/0901-05_determinate.png "0901年&05;_Determinate")  
  
 **确定的进度栏**  
  
 "确定"是指操作或进程需要界定的长时间，即使这段时间不能准确地预测。 清楚地表示完成。 不要让一个进度栏，请转到 100%，除非该操作已完成。 确定的进度栏动画将从左到右从 0 移到 100%。  
  
 永远不会移动一次操作中向后的进度指示器。 栏应向前移动稳定时该操作开始和结束时达到 100%。 进度栏的点是为用户提供了解整个操作所花费的时间，而不考虑所涉及的步骤数。  
  
##### <a name="concurrent-reporting-stacked-progress-bars"></a>并发报告 （堆积的进度栏）  
 如果某项操作需要很长时间-可能是可能使用几分钟 – 然后两个进度栏，其中一个，将显示总体进度的操作，另一个用于当前步骤的进度。 例如，如果安装程序正在复制很多文件，然后一个进度栏可用于指示多长时间的整个过程需要的时间，第二个表示的当前文件的百分比，或者复制目录。 不会报告多包含五个并发操作或使用堆积的进度栏的进程。 如果您有五个以上的并发操作或进程对报表，使用一个模式对话框与取消按钮以及报表到输出窗口的进度详细信息。  
  
##### <a name="textual-descriptions"></a>文字说明  
 使用的文本说明伴随发生了什么情况和估计的完成时间。 如果无法确定某项操作将需要多长时间，提供反馈的更好的选择可能的动画的图标而不是一个进度栏。  
  
 Visual Studio 提供了一个标准进度栏在可由任何产品集成到 Visual Studio 的状态栏中。 有关发生的进度栏动画处理的过程的文本说明，可以更新状态栏文本。  
  
#### <a name="other-progress-indicators"></a>其他进度指示器  
  
##### <a name="ants-animated-horizontal-dots"></a>Ants （动画水平点）  
 ![进度蚂蚁](~/extensibility/ux-guidelines/media/0903-01_ants.png "0903年&01;_Ants")  
  
 "蚂蚁"动画的水平点，为不确定的往返服务器过程提供可视参考。  
  
##### <a name="spinner-progress-ring"></a>微调框 （进度环）  
 ![进度微调框](~/extensibility/ux-guidelines/media/0903-02_spinner.png "0903年&02;_Spinner")  
  
 微调框 （也称为"进度环"） 是相对于上下文的用户界面主要用于不确定的进度指示器。 在紧靠其相关的内容，如文本类别标题、 消息、 或控件中显示微调框。  
  
##### <a name="cursor-feedback"></a>光标的反馈  
 2-7 秒之间执行的操作，对于提供游标反馈。 通常情况下，这意味着使用由操作系统提供将等待光标。 指南，请参阅 MSDN 文章[Cursors.Wait 属性](https://msdn.microsoft.com/en-us/library/system.windows.input.cursors.wait\(v=vs.110\).aspx)。  
  
#### <a name="progress-indicator-locations"></a>进度指示器位置  
  
##### <a name="status-bar"></a>状态栏  
 状态栏为您的应用程序提供了位置不会中断用户的工作的情况下向用户显示消息和有用的信息。 通常显示在窗口底部，进度的状态将不包括有关进度的度量标准的消息中与进度条指示器结合使用的工具提示窗格。  
  
 ![具有进度栏的状态栏](~/extensibility/ux-guidelines/media/0903-03_statusbarprogressbar.png "0903年&03;_StatusBarProgressBar")  
  
 **具有进度栏的状态栏**  
  
 ![具有消息传递的状态栏](~/extensibility/ux-guidelines/media/0903-04_statusbarmessage.png "0903年&04;_StatusBarMessage")  
  
 **具有文本说明的状态栏**  
  
##### <a name="infobar"></a>信息栏  
 类似于状态栏信息栏提供上下文通知和消息处理，它还可以使用如进度栏或微调框的不确定的进度指示器配对。 细粒度级别的进度或确定的进度指示不应对提供的信息栏。 请参阅[信息栏](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars)。  
  
 ![具有进度栏和消息传送的信息栏](~/extensibility/ux-guidelines/media/0903-05_infobar.png "0903年&05;_InfoBar")  
  
 **具有进度栏和文本说明的信息栏**  
  
 ![一个窗口中的信息栏](~/extensibility/ux-guidelines/media/0903-06_infobarinwindow.png "0903年&06;_InfoBarInWindow")  
  
 **代码分析窗口中的信息栏**  
  
##### <a name="inline"></a>内联  
 内联进度指示可以表示任何进度加载器类型。 通常的进度指示器配对使用消息，但这不是一项要求。  
  
 ![内联进度微调框](~/extensibility/ux-guidelines/media/0903-07_inlinespinner.png "0903年&07;_InlineSpinner")  
  
 **微调框与文本说明结合使用**  
  
 ![内联堆积进度栏](~/extensibility/ux-guidelines/media/0903-08_inlinestackedprogress.png "0903年&08;_InlineStackedProgress")  
  
 **确定堆积的进度栏**  
  
 ![内联进度消息传递](~/extensibility/ux-guidelines/media/0903-09_inlinetext.png "0903年&09;_InlineText")  
  
 **服务器资源管理器中的内联文本︰ 刷新...**  
  
##### <a name="tool-windows"></a>工具窗口  
 全局进度指示由正下方的工具栏中定位的不确定的进度栏表示。  
  
 ![全局不确定的进度栏](~/extensibility/ux-guidelines/media/0903-23_globalindeterminate.png "0903年&23;_GlobalIndeterminate")  
  
 **团队资源管理器全局不确定的进度栏**  
  
##### <a name="dialogs"></a>对话框  
 对话框可以包含任何进度加载器类型。 进度指示器可以是与消息传送成对出现，以及与多个级别的来精确表示日期和子进程的进度指示结合使用。  
  
 ![具有多个进度指示器类型的对话框](~/extensibility/ux-guidelines/media/0903-11_dialog.png "0903年&11;_Dialog")  
  
 **Visual Studio 与并发流程和多个进度指示器类型对话框**  
  
 ![具有进度加载器和消息传递的对话框](~/extensibility/ux-guidelines/media/0903-12_dialog2.png "0903年&12;_Dialog2")  
  
 **Visual Studio 具有进度加载器和消息传送内联发出命令对话框**  
  
##### <a name="document-well"></a>好的文档  
 嗯，文档可以在与控件一起显示多个进度加载器类型。  
  
 ![文档进度消息传递也](~/extensibility/ux-guidelines/media/0903-13_documentwell.png "0903年&13;_DocumentWell")  
  
 **不确定的进度栏下方工具栏**  
  
##### <a name="output-window"></a>输出窗口  
 输出窗口是合适的处理过程前进和通过内联文本消息传送的进度状态。 应使用状态栏以及任何输出窗口进度报告。  
  
 ![输出窗口中的消息的进度](~/extensibility/ux-guidelines/media/0903-14_outputwindow.png "0903年&14;_OutputWindow")  
  
 **正在进行的进程状态下的输出窗口，并等到消息传送**  
  
##  <a name="a-namebkmkinfobarsa-infobars"></a><a name="BKMK_Infobars"></a>信息栏  
  
### <a name="overview"></a>概述  
 信息栏向用户提供接近关注其点指示符，并使用共享的信息栏控件确保可视外观和交互的一致性。  
  
 ![信息栏](~/extensibility/ux-guidelines/media/0904-01_infobar.png "0904年&01;_Infobar")  
  
 **在 Visual Studio 中的信息栏**  
  
#### <a name="appropriate-uses-for-an-infobar"></a>正确使用一个信息栏  
  
-   若要为用户提供与当前上下文相关的非阻塞的但很重要消息  
  
-   若要指示用户界面中的某个状态或条件执行的一些交互产生的影响，如历史调试  
  
-   系统已检测到问题，例如当扩展会引起性能问题时通知用户  
  
-   提供一种方法来轻松地执行操作，例如当编辑器中检测到一个文件有混合制表符和空格的用户  
  
##### <a name="do"></a>执行操作︰  
  
-   简单地说，到点保留的信息栏消息文本。  
  
-   链接和按钮上显示的文本保持简洁。  
  
-   确保向用户提供的"操作"选项非常小，显示所需的操作。  
  
##### <a name="dont"></a>不要：  
  
-   使用一个信息栏提供标准应放置在工具栏中的命令。  
  
-   使用一个模式对话框代替一个信息栏。  
  
-   创建的时段之外的浮点型消息。  
  
-   在同一窗口内的多个位置中使用多个信息栏。  
  
#### <a name="can-multiple-infobars-show-at-the-same-time"></a>可以同时显示多个信息栏？  
 是，多个信息栏可以显示在同一时间。 与上边距和其他信息栏显示下面显示的第一个信息栏，将先来先服务顺序显示它们。  
  
 用户将看到最多三个信息栏，一次之后，如果多个信息栏是可用的信息栏区域将变得可滚动。  
  
### <a name="creating-an-infobar"></a>创建一个信息栏  
 信息栏包含四个部分，从左到右︰  
  
-   **图标︰**这是，您将在其中添加任何图标你想要显示的信息栏，例如警告图标。  
  
-   **文本︰**可以添加文本来描述方案/情况用户是在中，将文本中的链接以及根据需要。 请记住保留文本简洁。  
  
-   **操作︰**本部分应包含一些链接和按钮的用户可以在您的信息栏采取的操作。  
  
-   **关闭按钮︰**右侧最后一个部分可以具有关闭按钮。  
  
#### <a name="creating-a-standard-infobar-in-managed-code"></a>在托管代码中创建标准的信息栏  
 InfoBarModel 类可以用于创建数据源的一个信息栏。 使用上述四个构造函数之一︰  
  
```  
public InfoBarModel(IEnumerable<IVsInfoBarTextSpan> textSpans, ImageMoniker image = default(ImageMoniker), bool isCloseButtonVisible = true);  
  
```  
  
```  
public InfoBarModel(string text, ImageMoniker image = default(ImageMoniker), bool isCloseButtonVisible = true);  
  
```  
  
```  
public InfoBarModel(IEnumerable<IVsInfoBarTextSpan> textSpans, IEnumerable<IVsInfoBarActionItem> actionItems, ImageMoniker image = default(ImageMoniker), bool isCloseButtonVisible = true);  
  
```  
  
```  
public InfoBarModel(string text, IEnumerable<IVsInfoBarActionItem> actionItems, ImageMoniker image = default(ImageMoniker), bool isCloseButtonVisible = true);  
```  
  
 下面是带有一些文本与超链接、 一个操作按钮和图标创建 InfoBarModel 示例。  
  
 ![具有超链接的信息栏](~/extensibility/ux-guidelines/media/0904-02_infobarhyperlink.png "0904年&02;_InfobarHyperlink")  
  
```  
var infoBar = new InfoBarModel(  
    textSpans: new[]  
    {  
        new InfoBarTextSpan("This is a "),  
        new InfoBarHyperlink("hyperlink"),  
        new InfoBarTextSpan(" InfoBar.")  
    },  
    actionItems: new[]  
    {  
        new InfoBarButton("Click Me")  
    },  
    image: KnownMonikers.StatusInformation,  
    isCloseButtonVisible: true);  
  
```  
  
#### <a name="creating-a-standard-infobar-in-native-code"></a>在本机代码中创建标准的信息栏  
 实现 IVsInfoBar 接口以便提供从本机代码的一个信息栏。  
  
```  
public interface IVsInfoBar  
{  
    IVsInfoBarActionItemCollection ActionItems { get; }  
    ImageMoniker Image { get; }  
    bool IsCloseButtonVisible { get; }  
    IVsInfoBarTextSpanCollection TextSpans { get; }  
}  
  
```  
  
#### <a name="getting-an-infobar-uielement-from-an-infobar"></a>从一个信息栏中获取一个信息栏 UIElement  
 InfoBarModel 或 IVsInfoBar 实现是必须转换为 UIElement 为了 UI 中显示的数据模型。 可以通过 SVsInfoBarUIFactory/IVsInfoBarUIFactory 服务检索 UIElement。  
  
```  
private bool TryCreateInfoBarUI(IVsInfoBar infoBar, out IVsInfoBarUIElement uiElement)  
{  
    IVsInfoBarUIFactory infoBarUIFactory = serviceProvider.GetService(typeof(SVsInfoBarUIFactory)) as IVsInfoBarUIFactory;  
    if (infoBarUIFactory == null)  
    {  
        uiElement = null;  
        return false;  
    }  
  
    uiElement = infoBarUIFactory.CreateInfoBar(infoBar);  
    return uiElement != null;  
}  
```  
  
### <a name="placement"></a>放置  
 可以在一个或多个以下位置中显示信息栏︰  
  
-   工具窗口  
  
-   在文档选项卡  
  
> [!IMPORTANT]
>  就可以放置一个信息栏，以提供有关全局上下文的消息。 这将显示工具栏和文档也之间。 因为它会导致问题的"跳转和跃度"，所以不推荐在 IDE 的应避免将除非绝对必要且适用。  
  
#### <a name="placing-an-infobar-in-a-toolwindowpane"></a>在 ToolWindowPane 中放置一个信息栏  
 ToolWindowPane.AddInfoBar(IVsInfoBar) 方法可以用于将一个信息栏添加到工具窗口。 此 API 可以添加 IVsInfoBar （哪个 InfoBarModel 是默认实现），或 IVsUIElement。  
  
#### <a name="placing-an-infobar-in-a-document-or-non-toolwindowpane"></a>在文档或非 ToolWindowPane 中放置一个信息栏  
 若要将一个信息栏放入任何 IVsWindowFrame，VSFPROPID_InfoBarHost 属性用于获取 IVsInfoBarHost 的框架，然后添加信息栏 UIElement。  
  
```  
private void AddInfoBar(IVsWindowFrame frame, IVsUIElement uiElement)  
{  
    IVsInfoBarHost infoBarHost;  
    if (TryGetInfoBarHost(frame, out infoBarHost))  
    {  
        infoBarHost.AddInfoBar(uiElement);  
    }  
}  
private bool TryGetInfoBarHost(IVsWindowFrame frame, out IVsInfoBarHost infoBarHost)  
{  
    object infoBarHostObj;  
    if (ErrorHandler.Failed(frame.GetProperty((int)__VSFPROPID7.VSFPROPID_InfoBarHost, out infoBarHostObj)))  
    {  
        infoBarHost = null;  
        return false;  
    }  
  
    infoBarHost = infoBarHostObj as IVsInfoBarHost;  
    return infoBarHost != null;  
}  
  
```  
  
#### <a name="placing-an-infobar-in-the-main-window"></a>在主窗口中放置一个信息栏  
 若要在主窗口中放置一个信息栏，用于获取主窗口的 IVsInfoBarHost IVsShell 服务 VSSPROPID_MainWindowInfoBarHost，然后向其中添加信息栏 UIElement。  
  
### <a name="will-i-know-when-the-user-takes-action-in-my-infobar"></a>将知道何时用户执行的操作在我的信息栏？  
 是，我们将返回到信息栏作者的每个事件的操作。 然后负责采取措施在 IDE 中基于用户所选信息栏中的信息栏作者。 信息栏将会自动从主机中删除其关闭按钮被单击，但如果其他信息栏需要删除后关闭，则需要额外的工作。 遥测还将需要单独记录的每个信息栏。  
  
#### <a name="receiving-infobar-events-in-a-toolwindowpane"></a>ToolWindowPane 中接收的信息栏事件  
 ToolWindowPane 具有两个事件的信息栏。 关闭信息栏中 ToolWindowPane 时引发 InfoBarClosed 事件。 单击超链接或内信息栏按钮时，引发 InfoBarActionItemClicked 事件。  
  
#### <a name="receiving-infobar-events-directly-from-the-uielement"></a>直接从 UIElement 接收信息栏事件  
 IVsInfoBarUIElement.Advise 可以用于直接从一个信息栏 UIElement 订阅事件。 实现 IVsInfoBarUIEvents 将允许作者以关闭接收并单击事件。  
  
```  
public interface IVsInfoBarUIEvents  
{  
    void OnActionItemClicked(IVsInfoBarUIElement infoBarUIElement, IVsInfoBarActionItem actionItem);  
    void OnClosed(IVsInfoBarUIElement infoBarUIElement);  
}  
  
```  
  
##  <a name="a-namebkmkerrorvalidationa-error-validation"></a><a name="BKMK_ErrorValidation"></a>验证错误  
 当用户输入不是可接受的如必填的字段时将跳过或格式不正确的数据输入的信息时，最好是与使用控件验证或而不是使用阻止的弹出错误对话框控件附近的反馈。  
  
### <a name="field-validation"></a>字段验证  
 窗体和字段验证由三个组件组成︰ 一个控件、 一个图标和工具提示。 虽然可以使用几种类型的控件，这样，文本框将用作一个示例。  
  
 ![字段验证 （空）](~/extensibility/ux-guidelines/media/0905-01_fieldvalidation.png "0905年&01;_FieldValidation")  
  
 如果此字段是必需的应该有打水印文本指出**\<必需&1;>**字段背景应该为 light 和黄色 (VSColor: `Environment.ControlEditRequiredBackground`) 和前景应为灰色 (VSColor: `Environment.ControlEditRequiredHintText`):  
  
 ![字段验证具有"必须"标签](~/extensibility/ux-guidelines/media/0905-02_fieldvalidationrequired.png "0905年&02;_FieldValidationRequired")  
  
 该程序可以确定该控件处于的状态*输入的无效内容*焦点移动到另一个控件时或当用户单击确定提交按钮时或者当用户保存文档或窗体。  
  
 在确定无效的内容状态后，在控件内或只是其旁边出现一个图标。 对错误进行描述的工具提示应显示的图标或控件的悬停时的。 此外，1 像素的边框应创建无效的状态的控件周围出现。  
  
 ![字段验证布局规范](~/extensibility/ux-guidelines/media/0905-03_layoutspecs.png "0905年&03;_LayoutSpecs")  
  
 **字段验证布局规范**  
  
#### <a name="acceptable-variations-for-icon-location"></a>可接受的变体图标位置  
 有大量用户需要了解有关验证错误的唯一情况。 考虑到控件类型和配置用户界面中，选择适合于您的具体情况的图标位置。  
  
 ![图标位置的可接受位置](~/extensibility/ux-guidelines/media/0905-04_iconlocation.png "0905年&04;_IconLocation")  
  
 **可接受的变体字段验证图标位置**  
  
#### <a name="validation-requiring-a-round-trip-to-a-server-or-network-connection"></a>需要到服务器或网络连接的往返行程的验证  
 在某些情况下，到服务器的往返行程要求验证的内容，而且是很重要，以显示用户进度，验证，以及错误状态。 下图显示了这种情况和建议的用户界面的示例。  
  
 ![涉及到一台服务器的往返行程的验证](~/extensibility/ux-guidelines/media/0905-05_roundtrip.png "0905年&05;_RoundTrip")  
  
 **涉及到一台服务器的往返行程的验证**  
  
 请注意，必须以适应"验证..."提供足够的可用空间，右侧的控件 和"重试"文本。  
  
#### <a name="in-place-warning-text"></a>就地警告文本  
 如果空间可用于将接近控件的错误消息放入错误的状态，这是优于使用单独的工具提示。  
  
 ![就地警告](~/extensibility/ux-guidelines/media/0905-06_inplacewarning.png "0905年&06;_InPlaceWarning")  
  
 **就地警告文本**  
  
#### <a name="watermarks"></a>水印  
 有时整个控件或窗口处于错误状态。 在此情况下，使用水印以指示错误。  
  
 ![水印](~/extensibility/ux-guidelines/media/0905-07_watermark.png "0905年&07;_Watermark")  
  
 **水印字段验证**
