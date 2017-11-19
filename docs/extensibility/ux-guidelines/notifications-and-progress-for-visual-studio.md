---
title: "通知和 for Visual Studio 的进度 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f0ef65e9-0f1f-45f4-9f25-6e2398691168
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0d16ed0f58929a6559812261c3443b3561375205
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="notifications-and-progress-for-visual-studio"></a>通知和 for Visual Studio 的进度
##  <a name="BKMK_NotificationSystems"></a>通知系统  
  
### <a name="overview"></a>概述  
 有多种方法向用户通知发生了什么情况 Visual Studio 中有关其软件开发任务。  
  
 在实现任何类型的通知：  
  
-   **保留的最小的通知数**有效数量。 通知消息应应用于大部分 Visual Studio 用户或用户的特定功能区域。 过度使用的通知可能 sidetrack 用户，或降低产生可感知到的易用性系统。  
  
-   **确保您要呈现清晰、 可操作的消息**用户可以使用来调用合适的上下文中进行更复杂选择和采取进一步操作。  
  
-   **相应地提供同步和异步消息。** 同步通知指示出现需要立即关注，例如何时发生故障的 web 服务或代码引发异常。 应立即在要求其输入，如在一个模式对话框的方式这些情况下通知用户。 异步通知是这些用户应了解有关，但不是会要求起作用时立即，如网站部署在生成操作完成时或完成。 这些消息应更环境并不会中断用户的任务流。  
  
-   **使用仅在需要以防止用户采取进一步操作时的模式对话框**之前确认消息或显示在对话框中的决策。  
  
-   **删除环境的通知时它们将不再有效。** 不需要用户若要消除通知，如果它们已执行了操作以解决该问题有关，他们已收到通知。  
  
-   **请注意通知可能会导致错误关联。** 用户可能会认为，一个或多个其操作触发通知时实际上没有任何因果关系。 清除为有关上下文、 触发器和通知的源的通知消息。  
  
### <a name="choosing-the-right-method"></a>选择正确的方法  
 使用此表来帮助你选择正确的方法，以通知邮件的用户。  
  
|方法|使用|不要使用|  
|------------|---------|----------------|  
|[模式错误消息对话框](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ModalErrorMessageDialogs)|在继续之前需要用户响应时使用。|无需阻止用户和中断其流时，不要使用。 避免使用模式对话框，如果可能，以显示消息以另一个、 少受侵入的方式。|  
|[IDE 状态栏会显示](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_IDEStatusBar)|环境的文本信息与状态有关的进程时使用。|不要在单独使用。 最好与结合使用另一种反馈机制。|  
|[嵌入式信息栏](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_EmbeddedInfobar)|在工具窗口或文档窗口中，使用要通知的进度、 错误状态、 结果，和/或可操作的信息。|如果没有与信息栏所在的位置相关信息，不要使用。<br /><br /> 不要使用文档/工具窗口外。|  
|[鼠标光标更改](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_MouseCursorChanges)|可用于通知的过程进行的操作。 此外用于通知有更改鼠标中的状态，例如鼠标光标拖放时正在进行或，位于特定模式，如绘制模式。|不使用短进行更改，或如果 fluttering 的光标很可能 （例如，当取决于较长正在运行的进程而不是整个过程的部分）。|  
|[进度指示器](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_NotSysProgressIndicators)|当你需要报告进度 （确定的或不确定的） 时使用。 有各种进度指示器类型和使用特定的每个。 请参阅[进度指示器](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ProgressIndicators)。||  
|[Visual Studio 通知窗口](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_VSNotificationsToolWindow)|通知窗口不公开可扩展。 但是，它用于通信一系列 Visual Studio 中，包括与您的许可证和信息性通知的更新到 Visual Studio 或包的关键问题有关的消息。|不要使用为其他类型的通知。|  
|[错误列表](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ErrorList)|当直接与用户的当前打开的解决方案时遇到问题 （错误/警告/信息） 相关问题时，他们可能需要代码对其执行操作。<br /><br /> 这包括，例如：<br /><br /> 编译器消息 （错误/警告/信息）<br /><br /> 有关代码的代码分析器/诊断消息<br /><br /> -生成消息<br /><br /> 可能适合项目或解决方案文件，相关的问题，但首先考虑的解决方案资源管理器指示。|不要使用不具有与用户的打开的解决方案代码的任何相关的项。|  
|编辑器通知： 灯泡|当你有可用于修补打开的文件中存在的问题的修补程序时使用。<br /><br /> 请注意灯泡还应该使用用于托管对用户的代码按需、 重构，如执行但在这种情况下将不会出现"通知样式。"快速操作|不要使用打开的文件没有任何关系的项。|  
|编辑器通知： 波形曲线|使用向其打开的代码 （例如，红色的波浪线有错误） 的特定范围的问题用户发出警报。|不要使用适用于不与打开的代码的特定范围的项。|  
|[嵌入式的状态栏](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_EmbeddedStatusBars)|用于提供与内容或在特定工具窗口、 文档窗口或对话框窗口的上下文中的进程相关的状态。|不要使用常规产品通知、 进程，或在特定时段内没有任何关系的内容的项。|  
|[Windows 任务栏通知](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_WindowsTray)|用于图面进程外的进程的通知或伴生应用程序。|不要使用与 IDE 相关的通知。|  
|[通知气泡](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_NotificationBubbles)|使用远程进程的通知或更改**外部**的 IDE。|请不要用于作为一种方法通知用户进程**内**IDE。|  
  
### <a name="notification-methods"></a>通知方法  
  
####  <a name="BKMK_ModalErrorMessageDialogs"></a>模式错误消息对话框  
 模式错误消息对话框用于显示错误消息，要求用户确认或操作。  
  
 ![模式错误消息](../../extensibility/ux-guidelines/media/0901-01_modalerrormessage.png "0901年 01_ModalErrorMessage")  
  
 **警报数据库无效的连接字符串的用户模式错误消息对话框**  
  
####  <a name="BKMK_IDEStatusBar"></a>IDE 状态栏会显示  
 用户注意到状态栏文本的可能性关联到其综合性计算机体验和特定 Windows 平台的体验。 Visual Studio 客户群往往是这两个方面的经验，但即使经验丰富的 Windows 用户可能缺少状态栏中的更改。 因此，状态栏最好使用用于信息说明或作为冗余提示信息的信息显示在其他位置。 在对话框中或在通知工具窗口中，应提供任何类型的用户必须立即解决的关键信息。  
  
 Visual Studio 状态栏旨在允许的几种类型的信息显示。 此方案分为反馈、 设计器、 进度栏、 动画和客户端的区域。  
  
 反馈区域与设计器区域将始终可见。 进度栏和动画区域始终是动态的、 基于用户上下文。 设计器区域具有静态宽度由从短信随附资源请求的字符串的长度确定。 这允许本地化，用于调整宽度而无需更改代码。 为英语，此字符串的宽度约为 220 像素。 设计器区域将正常工作，反馈区域将吸收剩余的空间。  
  
 状态栏也着色通过通信例如 IDE 时在调试模式下的各种 IDE 状态更改添加视觉效果和功能的值。  
  
 ![IDE 状态栏颜色更改](../../extensibility/ux-guidelines/media/0901-02_idestatusbar.png "0901年 02_IDEStatusBar")  
  
 **IDE 状态栏颜色**  
  
####  <a name="BKMK_EmbeddedInfobar"></a>嵌入式信息栏  
 可以在文档窗口或工具窗口顶部的使用信息栏，以通知状态或条件的用户。 它还可以提供命令，以便用户可以具有一方式来轻松地执行操作。 信息栏是一个标准的 shell 控件。 避免创建你自己，这将执行操作，并显示与其他人在 IDE 中不一致。 请参阅[信息栏](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars)实现详细信息和使用指南。  
  
 ![嵌入的信息栏](../../extensibility/ux-guidelines/media/0901-03_embeddedinfobar.png "0901年 03_EmbeddedInfobar")  
  
 **信息栏嵌入在文档窗口中，警报 IDE 处于历史调试模式和编辑器将不会响应方式相同方式与其在标准调试模式下的用户。**  
  
####  <a name="BKMK_MouseCursorChanges"></a>鼠标光标更改  
 当将鼠标光标更改，使用绑定到 VSColor 服务，并且已与游标关联的颜色。 光标发生变化，可用于指示正在进行的操作，以及命中的区域用户悬停的目标，可以拖动、 放置到，或用于选择的对象的位置。  
  
 仅当所有可用的 CPU 时间必须保留对于操作，防止用户表达任何进一步的输入时，请使用忙/等待鼠标光标。 在使用多线程处理的正确编写应用程序的大多数情况下，当不允许用户执行其他操作的时间应该很少见。  
  
 请记住光标发生变化，可按所提供冗余信息提示提供其他位置。 不要依赖于光标更改作为用户必须解决是非常关键的尤其是在尝试传递的内容与用户进行通信的唯一方式。  
  
####  <a name="BKMK_NotSysProgressIndicators"></a>进度指示器  
 进度指示器很重要，在需要超过几秒钟来完成的过程将用户提供反馈。 可以显示进度指示器的就地 （附近正在进行的操作的启动点），在嵌入的状态栏中、 在模式对话框中，或在 Visual Studio 的状态栏中。 请按照中的指导[进度指示器](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ProgressIndicators)有关它们的使用和实现。  
  
####  <a name="BKMK_VSNotificationsToolWindow"></a>Visual Studio 通知窗口  
 Visual Studio 通知窗口通知开发人员的有关许可、 环境 (Visual Studio)、 扩展和更新。 用户可以消除单独通知，或者可以选择忽略某些类型的通知。 在中管理忽略的通知列表**工具 > 选项**页。  
  
 通知窗口不是当前可扩展的。  
  
 ![Visual Studio 通知窗口](../../extensibility/ux-guidelines/media/0901-06_vsnotificationswindow.png "0901年 06_VSNotificationsWindow")  
  
 **Visual Studio 通知工具窗口**  
  
####  <a name="BKMK_ErrorList"></a>错误列表  
 错误列表中的通知指示错误和警告的编译过程中发生和或生成过程中，并允许用户在该特定代码错误的代码中进行导航。  
  
 ![错误列表](../../extensibility/ux-guidelines/media/0901-08_errorlist.png "0901年 08_ErrorList")  
  
 **Visual Studio 中的错误列表**  
  
####  <a name="BKMK_EmbeddedStatusBars"></a>嵌入式的状态栏  
 IDE 状态栏会显示为动态，使用其客户端区域上下文设置为活动文档窗口中，然后更新用户的上下文和/或系统响应上的信息，因为很难维护连续显示信息或为状态提供上长期异步进程。 例如，IDE 状态栏会显示不适合的多个运行和/或立即可操作的项选择的测试运行结果的通知。 请务必保留此类的上下文中的用户进行的选择或启动一个进程的文档或工具窗口的状态信息。  
  
 ![嵌入式的状态栏](../../extensibility/ux-guidelines/media/0901-09_embeddedstatusbar.png "0901年 09_EmbeddedStatusBar")  
  
 **Visual Studio 中的嵌入式的状态栏**  
  
####  <a name="BKMK_WindowsTray"></a>Windows 任务栏通知  
 Windows 通知区域为旁边系统时钟在 Windows 任务栏上。 许多实用工具和软件组件提供此区域中的图标，以便用户可以获得系统级任务，例如，更改屏幕分辨率或获取软件更新的上下文菜单。  
  
 环境级别通知应显示在 Visual Studio 通知中心，不 Windows 通知区域中。  
  
####  <a name="BKMK_NotificationBubbles"></a>通知气泡  
 通知气泡可为信息性，在编辑器/设计器中或 Windows 通知区域的一部分出现。 用户感觉这是一项优势非关键通知这些气泡为更高版本，它们可以解决的问题。 气泡有不适合于用户必须立即解决的关键信息。 如果你在 Visual Studio 中使用通知气泡，请按照[通知气泡的 Windows 桌面指南](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742472\(v=vs.85\).aspx)。  
  
 ![通知气泡](../../extensibility/ux-guidelines/media/0901-07_notificationbubbles.png "0901年 07_NotificationBubbles")  
  
 **用于 Visual Studio 的 Windows 通知区域中的通知气泡**  
  
##  <a name="BKMK_ProgressIndicators"></a>进度指示器  
  
### <a name="overview"></a>概述  
 进度指示器是一个通知系统，用于提供用户反馈的重要组成部分。 进程和操作将完成时，它们会告知用户。 熟悉的指示器类型包括进度栏、 旋转游标和动态的图标。 类型和进度指示器的位置取决于上下文，包括正在报告和多长时间的进程或操作将花费完成。  
  
#### <a name="factors"></a>因素  
 若要确定哪些指示器类型适合，你需要确定以下因素。  
  
1.  **计时：**操作所花的时间长度  
  
2.  **模式：**操作是模式适合环境 （锁 UI 过程完成之前）  
  
3.  **持续/暂时的：**是否需要在更高版本时是报告和/或可查看进度的最终结果  
  
4.  **确定/不确定：**可以计算的操作结束时间和进度  
  
5.  **图形/Textual 位置：**的进度或进程是否在一条消息或将特定的控件，如树控件的主体中捕获的内联  
  
6.  **邻近：**进度应采用较近的与相关的 UI。 （例如，可以在状态栏中，这可能是距离遥远，或不具有要启动进程的按钮附近？）  
  
#### <a name="determinate-progress"></a>确定的进度  
  
|进度类型|何时以及如何使用|说明|  
|-------------------|-------------------------|-----------|  
|（确定） 的进度栏|预期的持续时间 > 5 秒。<br /><br /> 可能包括进程详细信息的文本的说明。|**不**将文本嵌入到动画。|  
|信息栏|消息传递上下文的 UI 与相关联。 请参阅[信息栏](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars)。<br /><br /> 可能包括进程详细信息的文本的说明。|**不**需要指示多个进程时使用多个信息栏。 请改用堆积的进度栏。|  
|输出窗口|暂时性的通知： 该用户需要应用程序级别的流程**查看**完成后的详细信息。|**不**如果用户将需要更高版本引用数据使用。|  
|日志文件|与在情况下 intransient 通知成对使用时务必**保存**完成后的详细信息。||  
|状态栏|暂时性的通知： 应用程序级过程该用户将**不需要**完成后的详细信息。<br /><br /> 包括一个嵌入的进度栏。<br /><br /> 可能包括进程详细信息的文本的说明。||  
  
#### <a name="indeterminate-progress"></a>不确定的进度  
  
|进度类型|何时以及如何使用|说明|  
|-------------------|-------------------------|-----------|  
|（不确定） 的进度栏|预期的持续时间 > 5 秒。<br /><br /> 可能包括进程详细信息的文本的说明。|**不**将文本嵌入到动画。|  
|蚂蚁 （动画水平点）|到服务器的往返过程。<br /><br /> 放置在父容器的顶部的上下文的 near 点。|**不**使用如果不整个容器的父级。|  
|微调 （进度环）|关联上下文用户界面时，或其中空间是需要考虑的过程。<br /><br /> 可能包括进程详细信息的文本的说明。||  
|信息栏|消息传递上下文的 UI 与相关联。 请参阅[信息栏](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars)。|**不**需要指示多个进程时使用多个信息栏。 请改用堆积的进度栏。|  
|输出窗口|暂时性的通知： 该用户将需要应用程序级别的流程**查看**完成后的详细信息。|**不**用于需要在会话之间保持的信息。|  
|日志文件|与在情况下 intransient 通知成对使用时务必**保存**完成后的详细信息。||  
|状态栏|暂时性的通知： 应用程序级过程该用户将**不需要**完成后的详细信息。<br /><br /> 包括嵌入的进度栏。<br /><br /> 可能包括进程详细信息的文本的说明。||  
  
### <a name="progress-indicator-types"></a>进度指示器类型  
  
#### <a name="progress-bars"></a>进度栏  
  
##### <a name="indeterminate"></a>不确定  
 ![不确定的进度栏](../../extensibility/ux-guidelines/media/0901-04_indeterminate.png "0901年 04_Indeterminate")  
  
 **不确定的进度栏**  
  
 "不确定"意味着运算的总体进度，或无法确定过程。 为需要可不受限制的时间量的操作中使用不确定的进度栏或访问的对象的未知的数目。 使用的文本说明伴随发生了什么情况。 使用超时能给予基于时间的操作的边界。 不确定的进度条使用动画显示进度操作正在进行，但不提供任何其他信息。 不要选择仅根据单独的准确性可能缺少一个不确定的进度栏。  
  
##### <a name="determinate"></a>确定  
 ![确定的进度栏](../../extensibility/ux-guidelines/media/0901-05_determinate.png "0901年 05_Determinate")  
  
 **确定的进度栏**  
  
 "确定"意味着的操作或过程需要限定的大量的时间，即使无法准确预测该时间量。 清楚地指示完成。 不要让转到 100%，除非该操作已完成一个进度栏。 确定的进度栏动画移动的从左到右从 0 到 100%。  
  
 从不移动的向后执行操作的过程的进度指示器。 栏应向前移动稳定时该操作开始和结束时达到 100%。 进度栏的点是让用户了解整个操作的时间，而不考虑包括多少步骤。  
  
##### <a name="concurrent-reporting-stacked-progress-bars"></a>并发 reporting （堆积的进度栏）  
 如果操作需要很长时间-可能是可能使用几个分钟-然后两个进度栏，对于操作的总体进度和另一个用于当前步骤的前进，显示的一个。 例如，如果安装程序正在复制许多文件，然后一个进度栏可以用于指示多长时间的整个过程所需的时间第二个可以指示当前文件的百分比或正在进行复制的目录。 不能超过五个并发操作或使用堆积的进度栏的进程报告。 如果你有五个以上的并发操作或报表的进程，使用一个模式对话框的取消按钮和报表到输出窗口的进度详细信息。  
  
##### <a name="textual-descriptions"></a>文本的说明  
 使用随附发生了什么情况的文本说明和估计的完成时间。 如果无法确定操作将需要多长时间，以便于反馈更好的选择可能动画的图标而不是一个进度栏。  
  
 Visual Studio 提供可由任何产品集成到 Visual Studio 的状态栏中一个标准进度栏。 有关所发生情况的进度栏动画处理的过程的文本说明，可以更新状态栏文本。  
  
#### <a name="other-progress-indicators"></a>其他进度指示器  
  
##### <a name="ants-animated-horizontal-dots"></a>蚂蚁 （动画水平点）  
 ![进度 ant](../../extensibility/ux-guidelines/media/0903-01_ants.png "0903年 01_Ants")  
  
 "蚂蚁，"动画水平点数为单位，不确定的往返服务器进程提供的视觉参考。  
  
##### <a name="spinner-progress-ring"></a>微调 （进度环）  
 ![进度微调框](../../extensibility/ux-guidelines/media/0903-02_spinner.png "0903年 02_Spinner")  
  
 微调框 （也称为"进度环"） 是不确定的进度指示器主要用于相对于上下文的 UI。 在紧靠其相关的内容，例如文本类别标头、 消息传递，或控件中显示微调框。  
  
##### <a name="cursor-feedback"></a>光标反馈  
 对于需要 2-7 秒之间的操作，提供光标反馈。 通常情况下，这意味着使用由操作系统提供将等待光标。 有关指南，请参阅 MSDN 文章[Cursors.Wait 属性](https://msdn.microsoft.com/en-us/library/system.windows.input.cursors.wait\(v=vs.110\).aspx)。  
  
#### <a name="progress-indicator-locations"></a>进度指示器位置  
  
##### <a name="status-bar"></a>状态栏  
 状态栏提供你的应用程序向用户显示消息和有用信息但不会中断用户的工作位置。 通常显示在窗口底部，进度的状态将是一个包含有关进度的度量值的消息与进度栏指示器结合使用的工具提示窗格。  
  
 ![具有进度栏的状态栏](../../extensibility/ux-guidelines/media/0903-03_statusbarprogressbar.png "0903年 03_StatusBarProgressBar")  
  
 **具有进度栏的状态栏**  
  
 ![状态栏使用消息传送](../../extensibility/ux-guidelines/media/0903-04_statusbarmessage.png "0903年 04_StatusBarMessage")  
  
 **具有文本说明的状态栏**  
  
##### <a name="infobar"></a>信息栏  
 类似于状态栏的信息栏提供上下文的通知和消息传递，这还可以使用不确定的进度指示器，例如，进度栏或微调配对。 粒度级别的进度或确定的进度指示不应提供的信息栏。 请参阅[信息栏](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars)。  
  
 ![具有进度栏和消息传送的信息栏](../../extensibility/ux-guidelines/media/0903-05_infobar.png "0903年 05_InfoBar")  
  
 **具有进度栏和文本说明的信息栏**  
  
 ![在窗口内的信息栏](../../extensibility/ux-guidelines/media/0903-06_infobarinwindow.png "0903年 06_InfoBarInWindow")  
  
 **代码分析窗口中的信息栏**  
  
##### <a name="inline"></a>内联  
 内联进度指示可以由任何进度加载器类型表示。 通常的进度指示器配对使用消息传送，但这不是一项要求。  
  
 ![内联进度微调框](../../extensibility/ux-guidelines/media/0903-07_inlinespinner.png "0903年 07_InlineSpinner")  
  
 **微调结合文本说明**  
  
 ![内联堆积进度栏](../../extensibility/ux-guidelines/media/0903-08_inlinestackedprogress.png "0903年 08_InlineStackedProgress")  
  
 **确定堆积的进度栏**  
  
 ![内联进度消息传递](../../extensibility/ux-guidelines/media/0903-09_inlinetext.png "0903年 09_InlineText")  
  
 **服务器资源管理器内联文本： 刷新...**  
  
##### <a name="tool-windows"></a>工具窗口  
 全局进度指示由正下方的工具栏中定位一个不确定的进度栏表示。  
  
 ![全局不确定的进度栏](../../extensibility/ux-guidelines/media/0903-23_globalindeterminate.png "0903年 23_GlobalIndeterminate")  
  
 **团队资源管理器全局不确定的进度栏**  
  
##### <a name="dialogs"></a>对话框  
 对话框可以包含任何进度加载器类型。 进度指示器可以是与消息传送成对出现，以及与多个级别的到表示粒度和子进程的进度指示结合使用。  
  
 ![具有多个进度指示器类型对话框](../../extensibility/ux-guidelines/media/0903-11_dialog.png "0903年 11_Dialog")  
  
 **与并发进程和多个进度指示器类型的 visual Studio 对话框**  
  
 ![具有进度加载器和消息传送的对话框](../../extensibility/ux-guidelines/media/0903-12_dialog2.png "0903年 12_Dialog2")  
  
 **具有进度加载器和消息传送内联命令的 visual Studio 对话框**  
  
##### <a name="document-well"></a>文档井中  
 很好地，文档可以结合控件显示多个进度加载器类型。  
  
 ![进度消息传递文档中也](../../extensibility/ux-guidelines/media/0903-13_documentwell.png "0903年 13_DocumentWell")  
  
 **下方工具栏不确定的进度栏**  
  
##### <a name="output-window"></a>输出窗口  
 输出窗口适合于处理过程前进和通过内联文本消息传送的正在进行的进度状态。 你应使用以及任何输出窗口进度报告的状态栏。  
  
 ![输出窗口中的消息传送的进度](../../extensibility/ux-guidelines/media/0903-14_outputwindow.png "0903年 14_OutputWindow")  
  
 **正在进行的进程状态下的输出窗口和等待消息传送**  
  
##  <a name="BKMK_Infobars"></a>信息栏  
  
### <a name="overview"></a>概述  
 信息栏为用户提供接近其点关注指示器，并使用共享的信息栏控件确保视觉外观和交互的一致性。  
  
 ![信息栏](../../extensibility/ux-guidelines/media/0904-01_infobar.png "0904年 01_Infobar")  
  
 **Visual Studio 中的信息栏**  
  
#### <a name="appropriate-uses-for-an-infobar"></a>适当使用一个信息栏  
  
-   可以向用户授予与当前上下文相关的非阻塞但重要消息  
  
-   指示 UI 处于特定状态或条件时，会带来一些交互意义，例如历史调试  
  
-   系统检测到问题，如扩展时会引起性能问题时通知用户  
  
-   提供一种方法轻松地执行操作，如当编辑器中检测到一个文件有混合制表符和空格的用户  
  
##### <a name="do"></a>执行操作：  
  
-   简单地说并点保留的信息栏消息文本。  
  
-   保持简洁上链接和按钮的文本。  
  
-   确保向用户提供的"操作"选项操作非常简单，显示所需的操作。  
  
##### <a name="dont"></a>不要：  
  
-   使用一个信息栏提供应放在工具栏中的标准命令。  
  
-   使用一个模式对话框代替信息栏。  
  
-   创建的时段之外的浮点消息。  
  
-   在同一窗口中的多个位置中使用多个信息栏。  
  
#### <a name="can-multiple-infobars-show-at-the-same-time"></a>可以同时显示多个信息栏？  
 是的多个信息栏可以显示在同一时间。 与第一个信息栏显示上边距和其他信息栏显示以下，将按先、 先服务的顺序显示它们。  
  
 用户将看到一次的最多三个信息栏之后，如果详细的信息栏是可用的信息栏区域将变得可滚动。  
  
### <a name="creating-an-infobar"></a>创建一个信息栏  
 信息栏具有四个部分，从左到右：  
  
-   **图标：**这是你将在其中添加任何图标你想要显示的信息栏，如警告图标。  
  
-   **文本：**可以添加文本以描述方案/情况用户以及文本中的链接是在中，如果需要。 请记住要保留文本简洁。  
  
-   **操作：**本节应包含一些链接和用户可以在你的信息栏中执行的操作的按钮。  
  
-   **关闭按钮：**右侧的最后一节可以关闭按钮。  
  
#### <a name="creating-a-standard-infobar-in-managed-code"></a>在托管代码中创建标准信息栏  
 InfoBarModel 类可以用于创建一个信息栏的数据源。 使用上述四个构造函数之一：  
  
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
  
 下面是 InfoBarModel 创建带有一些文本与超链接、 一个操作按钮和图标的示例。  
  
 ![具有超链接的信息栏](../../extensibility/ux-guidelines/media/0904-02_infobarhyperlink.png "0904年 02_InfobarHyperlink")  
  
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
  
#### <a name="creating-a-standard-infobar-in-native-code"></a>在本机代码中创建标准信息栏  
 实现 IVsInfoBar 接口以便提供从本机代码的信息栏。  
  
```  
public interface IVsInfoBar  
{  
    IVsInfoBarActionItemCollection ActionItems { get; }  
    ImageMoniker Image { get; }  
    bool IsCloseButtonVisible { get; }  
    IVsInfoBarTextSpanCollection TextSpans { get; }  
}  
  
```  
  
#### <a name="getting-an-infobar-uielement-from-an-infobar"></a>从一个信息栏中获取信息栏 UIElement  
 InfoBarModel 或 IVsInfoBar 实现是必须打开到 UIElement 以便在 UI 中显示的数据模型。 UIElement 可以检索与 SVsInfoBarUIFactory/IVsInfoBarUIFactory 服务。  
  
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
 可以在一个或多个以下位置中显示信息栏：  
  
-   工具窗口  
  
-   文档选项卡内  
  
> [!IMPORTANT]
>  就可以放置一个信息栏，以提供有关全局上下文的消息。 这会显示工具栏和文档井中之间。 这不建议，因为它会导致"跳转和 jerk"出现问题的 IDE，应当避免，除非绝对必要且适用。  
  
#### <a name="placing-an-infobar-in-a-toolwindowpane"></a>置于 ToolWindowPane 信息栏  
 ToolWindowPane.AddInfoBar(IVsInfoBar) 方法可用来将一个信息栏添加到工具窗口。 此 API 可以添加 IVsInfoBar （哪些 InfoBarModel 时为默认实现），或 IVsUIElement。  
  
#### <a name="placing-an-infobar-in-a-document-or-non-toolwindowpane"></a>在文档或非 ToolWindowPane 中放置一个信息栏  
 可以将一个信息栏放置到任何 IVsWindowFrame，VSFPROPID_InfoBarHost 属性用于获取 IVsInfoBarHost 帧，并将信息栏 UIElement。  
  
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
 若要将一个信息栏放在主窗口中，使用 IVsShell 服务 VSSPROPID_MainWindowInfoBarHost 获取主窗口 IVsInfoBarHost，然后向其中添加信息栏 UIElement。  
  
### <a name="will-i-know-when-the-user-takes-action-in-my-infobar"></a>将知道如果用户在我的信息栏中执行的操作？  
 是，我们将向信息栏作者返回每个事件的操作。 然后负责执行基于信息栏中的用户选择 IDE 中的操作的信息栏作者。 信息栏将自动从主机中删除被单击其关闭按钮，但如果其他信息栏需要删除后关闭，则需要额外的工作。 遥测还将需要单独记录的每个信息栏。  
  
#### <a name="receiving-infobar-events-in-a-toolwindowpane"></a>在 ToolWindowPane 中接收信息栏事件  
 ToolWindowPane 存在两个事件的信息栏。 关闭信息栏中 ToolWindowPane 时引发 InfoBarClosed 事件。 单击超链接或按钮位于信息栏内的时，将引发 InfoBarActionItemClicked 事件。  
  
#### <a name="receiving-infobar-events-directly-from-the-uielement"></a>直接从 UIElement 接收信息栏事件  
 IVsInfoBarUIElement.Advise 可以用于直接从一个信息栏 UIElement 订阅事件。 实现 IVsInfoBarUIEvents 将允许收到关闭，此时单击事件的作者。  
  
```  
public interface IVsInfoBarUIEvents  
{  
    void OnActionItemClicked(IVsInfoBarUIElement infoBarUIElement, IVsInfoBarActionItem actionItem);  
    void OnClosed(IVsInfoBarUIElement infoBarUIElement);  
}  
  
```  
  
##  <a name="BKMK_ErrorValidation"></a>错误验证  
 当用户输入是不可接受，如已必填的字段跳过或格式不正确的数据输入的信息时，最好使用控件验证或而不是使用阻止的弹出窗口错误对话框控件附近的反馈。  
  
### <a name="field-validation"></a>字段验证  
 窗体和字段验证包括三个组件： 控件、 一个图标，图标和工具提示。 尽管几种类型的控件可以使用此，在文本框中将用作示例。  
  
 ![字段验证 &#40; 空白 &#41;] (../../extensibility/ux-guidelines/media/0905-01_fieldvalidation.png "0905年 01_FieldValidation")  
  
 如果该字段是必需的则应水印文本指出**\<必需 >**和字段后台应浅色黄色 (VSColor: `Environment.ControlEditRequiredBackground`) 和前台应为灰色 (VSColor: `Environment.ControlEditRequiredHintText`):  
  
 ![字段具有"必须"标签的验证](../../extensibility/ux-guidelines/media/0905-02_fieldvalidationrequired.png "0905年 02_FieldValidationRequired")  
  
 程序可以确定控件是否处于的状态*输入的无效内容*当焦点移动到另一个控件或当用户单击确定提交按钮，或者当用户保存文档或窗体。  
  
 在确定无效的内容状态后，在该控件内或只需旁边将显示一个图标。 对错误进行描述的工具提示应出现的悬停时的图标或控件。 此外，1 像素的边框应创建无效的状态的控件周围出现。  
  
 ![字段验证布局规范](../../extensibility/ux-guidelines/media/0905-03_layoutspecs.png "0905年 03_LayoutSpecs")  
  
 **字段验证布局规范**  
  
#### <a name="acceptable-variations-for-icon-location"></a>可接受的变体图标位置  
 有大量的独特情况，用户需要了解验证错误。 考虑到的控件类型和配置 UI 中，选择适合你的情况的图标位置。  
  
 ![图标位置的可接受位置](../../extensibility/ux-guidelines/media/0905-04_iconlocation.png "0905年 04_IconLocation")  
  
 **可接受的变体字段验证图标位置**  
  
#### <a name="validation-requiring-a-round-trip-to-a-server-or-network-connection"></a>需要服务器或网络连接到的往返行程的验证  
 在某些情况下，到服务器的往返行程需要来验证内容，并且它将会显示用户进度，验证和错误状态十分重要。 下图显示了这种情况并且建议的 UI 的示例。  
  
 ![验证涉及到服务器的往返行程](../../extensibility/ux-guidelines/media/0905-05_roundtrip.png "0905年 05_RoundTrip")  
  
 **涉及到服务器的往返行程的验证**  
  
 请注意，必须以适应"验证..."和"重试"文本提供足够的可用空间，右侧的控件。  
  
#### <a name="in-place-warning-text"></a>就地警告文本  
 如果空间可用于将控件接近的错误消息放入错误的状态，这是优于使用单独的工具提示。  
  
 ![在 &#45; 位置警告](../../extensibility/ux-guidelines/media/0905-06_inplacewarning.png "0905年 06_InPlaceWarning")  
  
 **就地警告文本**  
  
#### <a name="watermarks"></a>水印  
 有时是整个控件或窗口处于错误状态。 在此情况下，使用水印以指示错误。  
  
 ![水印](../../extensibility/ux-guidelines/media/0905-07_watermark.png "0905年 07_Watermark")  
  
 **水印字段验证**