---
title: "Visual Studio 2017 RC 中的新增功能 | Microsoft Docs"
ms.custom: 
ms.date: 12/13/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.StartPage.WhatsNew
helpviewer_keywords:
- Visual Studio, what's new
- what's new [Visual Studio]
ms.assetid: 7307e180-ba28-4774-8a43-cbb980085a71
author: TerryGLee
ms.author: tglee
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: 4fb097ab0ee0d45fd5727e3170db3393392abf23
ms.openlocfilehash: dc1941fd755c28039560b608733067b1da365c3a

---
# <a name="what39s-new-in-visual-studio-2017"></a>Visual Studio 2017 中的新增功能
欢迎使用 Visual Studio 2017 RC，这是一款由开发者工作效率工具、云服务和扩展组成的集成套件，让你和你的团队可以创建适用于 Web、Windows 商店、桌面、Android 和 iOS 的强大的应用程序和游戏。  

在此 Visual Studio 最新版本的候选发布 (RC) 中，我们一直专注于性能和工作效率改进。 在性能方面，我们让 Visual Studio 的启动速度更快、响应性更强，而且使用的内存也比以往更少。 在工作效率方面，我们已添加或更新功能，帮助用户更高效地使用 Visual Studio。

> [!TIP]
> 若要查看新 RC 的实际操作，请观看第 9 频道的 [Visual Studio 中的新增功能](https://channel9.msdn.com/events/connect/2016/159)视频。   

以下是我们所做更改的高级扼要重述：

* **提升了工作效率**。 代码导航、IntelliSense、重构、代码修复和调试的增强功能，无论使用哪种语言或平台，都能节省你在日常任务上花费的时间和精力。 此外，对于采用 DevOps 的团队，Visual Studio 2017 简化了开发者的内部循环，并通过全新的实时功能（如实时单元测试和实时架构依赖关系验证）加快了代码流。
* **重新定义了基础知识**。  进一步强调了提高开发人员每天遇到的基本任务的效率。 从根据开发人员需求定制的全新轻量级和模块化安装以及从启动到关闭更快的 IDE，到无需项目和解决方案也能查看、编辑和调试任何代码的新方式，Visual Studio 2017 让开发人员更加专注于大局。
* **简化了 Azure 开发**。 通过内置的 Azure 工具套件，开发人员可以轻松创建由 Microsoft Azure 提供支持的云优先应用程序。 借助 Visual Studio，可以轻松从 IDE 直接配置、构建、调试、打包和部署 Microsoft Azure 上的应用程序和服务。
* **五星级移动开发**。 借助高级调试和分析工具以及单元测试生成功能，通过带有 Xamarin 的 Visual Studio 2017，与以往相比开发人员可以更快、更轻松地构建、连接和调整适用于 Android、iOS 和 Windows 的移动应用。 开发人员还可以选择在 Visual Studio 中使用 Apache Cordova 或 Visual C ++ 跨平台库开发来开发移动应用。  

以下是重大更改的更多详细信息。

> [!NOTE]
> 有关 Visual Studio 2017 RC 以及后续 RC 刷新中新特性和功能的完整列表，请参阅[发行说明](https://www.visualstudio.com/news/vs2015-vs)。 有关问题和解决方法的列表，请参阅发行说明中的[已知问题](https://www.visualstudio.com/news/vs2015-vs#knownissues)部分。   

## <a name="performance-improvements"></a>性能改进

### <a name="a-new-setup-experience"></a>新的安装体验  
[下载 Visual Studio Enterprise 2017 RC](https://aka.ms/vs/15/preview/vs_enterprise) 或[检查 Visual Studio 系统要求](https://www.visualstudio.com/en-us/productinfo/vs2017-system-requirements-vs)

 我们重新设计了 Visual Studio 的安装体验，使用户在需要时只需安装所需功能，让安装更加简单。 此外，我们还减少了最小内存需求量，使 Visual Studio 系统安装速度更快，对系统的影响更小。 而且，还能完全卸载干净。

 安装 Visual Studio 时所看到的最重要的更改就是其新的安装体验。 在“工作负载”选项卡上，可看见已分组的安装选项，它们代表常见框架、语言和平台 - 涵盖了从 .NET 桌面开发到使用 R、Python 和 F# 的数据科学。  

 ![Visual Studio 2017 RC 安装对话框](../ide/media/willow1.png "VS2017RC_Setup_screen")

选择所需的工作负载，并在需要时对其上调。 最小的安装仅为数百兆字节，但仍然支持针对&20; 多种语言和源代码管理的基本代码编辑。

我们还添加了不同的方式来安装 Visual Studio。 想要选择自己的组件而不是使用工作负载？ 只需从安装程序选择“单个组件”选项卡。 想要在不更改 Windows 语言选项的情况下立即安装语言包？ 选择安装程序的“语言包”选项卡。  

若要更加深入地了解新的安装体验，包括指导你进行演练的分步说明，请参阅[安装 Visual Studio](../install/install-visual-studio.md)页。


### <a name="start-visual-studio-faster"></a>更快地启动 Visual Studio
如果 Visual Studio 检测到 IDE 启动速度变慢，则会提供新的 Visual Studio 性能中心帮助加快速度。 性能中心列出了所有减缓 IDE 启动速度的扩展和工具窗口。 可用它来确定扩展何时启动，或工具窗口是否在启动时打开，从而提高启动性能。

### <a name="decrease-solution-load-time"></a>缩短解决方案加载时间
处理包含多达 100 个项目的解决方案并非意味着要一次性处理所有文件或项目。 现在，无需等待 Visual Studio 加载每个项目即可进行编辑和调试。 若要通过托管项目尝试此操作，请从“工具”->“选项”->“项目和解决方案”打开“轻型解决方案加载”。

  ![Visual Studio 2017 RC 中的选项对话框](../ide/media/vs2017ide-LightweightSolutionLoad.PNG "VS2017RC 选项对话框 - 轻型解决方案加载")

### <a name="faster-on-demand-loading-of-extensions"></a>按需加载扩展速度更快
原理很简单：在需要时（而不是在启动 Visual Studio 时）加载扩展。 首先，我们移动了要按需加载的 Python 和 Xamarin 扩展，接下来，我们将致力于将 Visual Studio 随附的所有扩展以及第三方供应商提供的所有扩展都移动到此模型。 想了解哪些扩展会影响启动、解决方案加载和键入性能？ 可以在“帮助”->“管理 Visual Studio 性能”中查看此信息。

  ![Visual Studio 2017 RC 中的选项对话框](../ide/media/vs2017ide-ManageVSperf.png "VS2017RC 帮助对话框 - 性能管理")

## <a name="productivity-improvements"></a>提高工作效率

### <a name="sign-in-across-multiple-accounts"></a>使用多个帐户登录  
我们在 Visual Studio 2017 RC 中引入了新的标识服务，使你可在 Microsoft 开发人员工具（如团队资源管理器、Azure 工具、Windows 应用商店发布等）之间共享用户帐户。

而且，你可以保持更久的登录状态；每 12 小时内不会要求你再次登录。 若要了解详细信息，请参阅 [Fewer Visual Studio Sign-in Prompts](https://blogs.msdn.microsoft.com/visualstudio/2016/08/15/fewer-visual-studio-sign-in-prompts/)（更少的 Visual Studio 登录提示）博客文章。

### <a name="manage-your-extensions-with-roaming-extensions-manager"></a>利用漫游扩展管理器管理扩展
现在登录 Visual Studio 时，能更轻松地通过你最喜爱的扩展设置每个开发环境。 通过在云中创建同步列表，新漫游扩展管理器会跟踪所有你喜欢的扩展。  

若要查看 Visual Studio 中的扩展列表，请单击“工具”>“扩展”>“更新”，再单击“漫游扩展管理器”。

![Visual Studio 2017 - 扩展和更新对话框](../ide/media/vs2017ide-ExtensionsAndUpdates.png "Visual Studio 2017-“工具”>“扩展和更新”对话框")

漫游扩展管理器会跟踪安装的所有扩展，但你可以选择要添加到漫游列表的扩展。

![Visual Studio 2017 - 扩展和更新对话框](../ide/media/vs2017ide-RoamingExtensionManager.png "Visual Studio 2017 - 漫游扩展管理器")

使用漫游扩展管理器时，列表中会出现 3 种图标类型：
* ![“漫游”图标](../ide/media/vs2017ide-roamedicon.png "“漫游”图标") ***“漫游”图标***：表示存在于漫游列表中、但未在计算机上安装的扩展。
  （可通过“下载”按钮安装这些扩展。）
* ![“漫游且已安装”图标](../ide/media/vs2017ide-roamedinstalledicon.png "“漫游且已安装”图标") ***“漫游且已安装”图标***：表示存在于漫游列表中且已在此环境中安装的所有扩展。
  （如果确定不希望漫游，可通过“停止漫游”按钮删除它们。）
* ![“已安装”图标](../ide/media/vs2017ide-installedicon.png "“已安装”图标") ***“已安装”图标***：表示此环境中已安装、但不属于漫游列表的所有扩展。
  （可通过“启动漫游”按钮将扩展添加到漫游列表。）

这些图标显示列表当前的状态。 可使用处于任何状态的任何扩展，因此可自定义你心中所想的内容！ 或者，让我们为你代劳！ 登录时下载的所有扩展都将作为“漫游且已安装”的内容添加到列表，因此将包含在漫游列表中，可从任何计算机对其进行访问！

### <a name="experience-live-architecture-dependency-validation-and-live-unit-testing"></a>体验实时体系结构依赖关系验证和实时单元测试

在 Visual Studio Enterprise 2017 RC 中，如果已经设置了依赖关系验证关系图（也称为 层关系图），当你在代码编辑器中键入代码时，现在会实时通知你体系结构依赖项规则冲突。

并在错误列表中显示错误，在文本编辑器中用波浪线标出冲突的精确位置。 这样就降低了引入非必需依赖关系的可能性。

![体系结构的实时验证](../ide/media/vs2017ide-LiveArchitectureDepedendencyValidation.png "体系结构依赖关系的实时验证")

#### <a name="live-unit-testing"></a>实时单元测试：

实时单元测试是我们引入的一个新功能，仅在 Visual Studio 企业版中提供。 此功能能够可视化单元测试结果和在编辑器中进行编码时的实时代码覆盖情况。 该功能可用于适用于 .NET Framework 的 C#/VB 项目，并支持 MSTest xUnit 和 NUnit 这三种测试框架。

### <a name="visual-studio-ide-enhancements"></a>Visual Studio IDE 增强功能
#### <a name="interact-with-git"></a>与 Git 进行交互：
使用 Visual Studio IDE 右下角的控件可以快速将项目提交和发布到 Git，管理 Git 存储库。

![Visual Studio 2017 RC 安装对话框](../ide/media/vsIDE-GitInteraction.png "Git-tools-in-the-VS2017RC-IDE")

#### <a name="view-and-navigate-code-with-structure-visualizer"></a>通过结构可视化工具查看和导航代码：
Visual Studio 代码编辑器现提供名为“结构可视化工具”的新功能。 此功能在代码嵌套区域之间显示垂直指南，让你可以更轻松地查看和浏览代码。 此功能可用于所有支持 TextMate 的语言以及 Visual C#、Visual Basic 和 XAML。

![Visual Studio 2017 RC 设置对话框](../ide/media/vsIDE-StructureVisualizer.png "Structure-Visualizer-in-VS2017RC")

#### <a name="experience-an-improved-navigate-to"></a>体验改进的“导航到”：
改进了“导航到”功能。 简化了“导航到”窗口，并添加了对其他能缩小代码搜索范围的筛选器字符的支持。

#### <a name="create-apps-in-even-more-programming-languages"></a>以更多编程语言创建应用：
与以前版本比较，可在 Visual Studio 中以更多编程语言创建应用，且不再需要解决方案和项目。 代码可获取语法着色、基本语句完成以及（在某些情况下）“导航到”和其他支持。 如果你喜爱的语言不受支持，可使用 TextMate 语法创建对它的支持。

### <a name="visual-c"></a>Visual C++
Visual Studio 2017 向 Visual C++ 环境引入了许多更新和修补程序。 我们修复了编译器和工具中的 250 多个 bug 和已报告问题，其中很多是客户通过 [Microsoft Connect](https://connect.microsoft.com/VisualStudio "Microsoft Connect") 提交的。

我们还进行了几项改进：在 Visual Studio 中包括分发 C++ 核心准则，通过添加对 C++11 和 C++ 功能的增强支持更新编译器，添加和更新 C++ 库中的功能，改进 C++ IDE、安装工作负载等的性能。

有关完整的详细信息，请参阅 [Visual 2017 RC 中 Visual C++ 的新增功能](/cpp/top/what-s-new-for-visual-cpp-in-visual-studio)页。  


### <a name="debugging-and-diagnostics"></a>调试和诊断
现在调试速度更快，并且在编辑时不会产生延迟。

例如：在 Visual Studio 的早期版本中，我们引入了所谓的 WPF、Windows 窗体和托管控制台项目的宿主进程，通过加快在下一个调试会话中使用的后台进程速度，提高调试速度。 当停止调试或调试会话结束后使用 Visual Studio 时，这一善意功能却会导致 Visual Studio 暂停响应几秒钟。

在 Visual Studio 2017 中，我们关闭了宿主进程并优化了调试，无需宿主进程也能达到同样速度，对于从未使用宿主进程（如 ASP.NET、通用 Windows 和 C++ 项目）的项目而言，甚至更快。

#### <a name="run-to-click"></a>运行时单击：
现在，在调试时只需单击代码行旁边的图标即可运行此代码行。 无需再设置临时断点，也不必再执行多个步骤来执行代码和在所需行停止。

![Visual Studio 2017 RC 调试 - 运行时单击](../ide/media/vs2017ide-RunToClick.png "Visual Studio 2017 调试和诊断中的运行时单击")

#### <a name="the-new-exception-helper"></a>新的异常帮助器：

新的“异常帮助窗口”可用于查看异常信息，该信息显示在非模式对话框中，可对内部异常进行即时访问。

在诊断 NullReferenceException 时快速查看异常帮助器中为 null 的内容。

现可在引发的异常处停止时单击复选框添加条件，排除特定模块引发的异常类型。

![新的“异常帮助器”对话框](../ide/media/vs2017ide-ExceptionHelper.png "新的“异常帮助器”对话框")

有关详细信息，请参阅 [Using the New Exception Helper in Visual Studio](https://blogs.msdn.microsoft.com/visualstudioalm/2016/03/31/using-the-new-exception-helper-in-visual-studio-15-preview/)（使用 Visual Studio 中的新异常帮助器）博客文章。

## <a name="talk-to-us"></a>与我们交流  
 为什么将反馈发送至 Visual Studio 团队？ 因为我们严肃对待客户反馈。 这会给予我们巨大的行事动力。  

如果有关于如何改进 Visual Studio 的建议，或想报告问题，请参阅[与我们交流](../ide/talk-to-us.md)页，获取更多详细信息。  

### <a name="report-a-problem"></a>报告问题  
 有时，一条消息不足以说明所遇问题的总体影响。 如果遇到挂起、崩溃或其他性能问题，可利用“报告问题”工具与我们轻松共享重现步骤和支持文件（如屏幕快照以及跟踪和堆转储文件）。 有关如何使用此工具的详细信息，请参阅[如何报告问题](how-to-report-a-problem-with-visual-studio-2017.md)页。  

### <a name="track-your-issue-in-connect"></a>在“连接”中跟踪你的问题  
 如果要跟踪 Visual Studio 反馈状态，请转至[“连接”](http://connect.microsoft.com/)并在那里报告 Bug。 报告后，可返回至“连接”来跟踪其状态。  

## <a name="see-also"></a>另请参阅  
* [Visual C++ 中的新增功能](/cpp/top/what-s-new-for-visual-cpp-in-visual-studio)
* [C# 中的新增功能](https://docs.microsoft.com/en-us/dotnet/articles/csharp/csharp-7)  
* [Team Foundation Server 中的新增功能](https://www.visualstudio.com/en-us/docs/whats-new)
* [Visual Studio 发行说明](https://www.visualstudio.com/news/vs2015-vs)



<!--HONumber=Feb17_HO4-->


