---
title: "Visual Studio 2017 中的新增功能 | Microsoft Docs"
ms.custom: 
ms.date: 04/06/2017
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
ms.sourcegitcommit: ddc84f3b92d8e0febaea3d23b415bd6e703cc530
ms.openlocfilehash: e04b972187b7b7ec225b48cc9b8904d804399ff8
ms.lasthandoff: 04/07/2017

---
# <a name="what39s-new-in-visual-studio-2017"></a>Visual Studio 2017 中的新增功能
为任何开发、应用和平台提供无与伦比的效率。 使用 Visual Studio 2017 开发适用于 Android、iOS、Windows、Linux、Web 和云的应用。 快速编码、轻松调试和诊断、时常测试，并且可以放心地进行发布。 还可通过构建自己的扩展，以便扩展和自定义 Visual Studio。 此新版本发布之后，可使用版本控制、更具敏捷性且可高效协作！

> [!NOTE]
> 有关 Visual Studio 2017 中新增功能的完整列表，请参阅[发行说明](https://www.visualstudio.com/news/vs2015-vs)。

以下是我们所做更改的高级扼要重述：

* **性能和工作效率**。 我们不仅关注新式移动、云和桌面开发功能，还对获取方式、性能和一般开发人员的工作效率体验进行了整体改进。 与以前相比，现在的 Visual Studio 启动速度更快、响应能力更强、使用的内存更少。
* **重新定义了基础知识**。 新的安装体验意味着安装速度更快，并且能够在需要时立即安装。 无论是要加载大型解决方案和项目，还是要处理代码文件夹或单个代码文件，Visual Studio 的启动速度都比以前更快。 Visual Studio 还可帮助你掌控全局，特别是对使用 DevOp 的团队而言。
* **使用 Azure 开发云应用**。 通过内置的 Azure 工具套件，你可以轻松地创建由 Microsoft Azure 提供支持的云优先应用。 借助 Visual Studio，可以轻松配置、构建、调试、打包和部署 Azure 上的应用和服务。
* **移动应用开发**。 在 Visual Studio 2017 中，可以使用 Xamarin 进行创新并快速得出结果。Xamarin 通过使用一个核心基本代码和技能集统一你的多平台移动需求。 利用现有的团队、技术投资和 C# 代码，在预算范围内提前实现优质的用户体验。 加速移动生命周期的每一步，提供一流的用户体验或一系列可提高员工工作效率的工作效率应用。

下面更详细地介绍了部分最值得注意的变更。

## <a name="performance-improvements"></a>性能改进

### <a name="a-new-setup-experience"></a>新的安装体验  
[下载 Visual Studio 2017](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) 或[检查 Visual Studio 系统要求](https://www.visualstudio.com/en-us/productinfo/vs2017-system-requirements-vs)

 通过 Visual Studio，可以在需要时更轻松快速地安装所需功能。 而且，还能完全卸载干净。

 安装 Visual Studio 时，你将看到的最重要的更改是其新的安装体验。 在“工作负荷”选项卡上，你将看到表示常见框架、语言和平台的分组安装选项。 它涵盖 Windows、Linux 和 iOS 上从 .NET 桌面开发到 C++ 应用程序开发的所有内容。   

 ![Visual Studio 2017 安装对话框](../install/media/vs2017-workloads.PNG "Visual Studio 2017 安装屏幕")

选择所需的工作负载，并在需要时对其进行更改。

想要选择自己的组件而不是使用工作负载？ 只需从安装程序选择“单个组件”选项卡。 想要在不更改 Windows 语言选项的情况下立即安装语言包？ 选择安装程序的“语言包”选项卡。  

若要更深入地了解新的安装体验，包括指导你进行演练的分步说明，请参阅[安装 Visual Studio](../install/install-visual-studio.md) 页。

### <a name="start-visual-studio-faster"></a>更快地启动 Visual Studio
新的 Visual Studio 性能中心可以帮助你优化 IDE 启动速度。 性能中心列出了所有可能减缓 IDE 启动速度的扩展和工具窗口。 可用它来确定扩展何时启动，或工具窗口是否在启动时打开，从而提高启动性能。

### <a name="decrease-solution-load-time"></a>缩短解决方案加载时间
处理包含大量项目的解决方案并非意味着必须同时处理所有文件或项目。 现在，无需等待 Visual Studio 加载每个项目即可进行编辑和调试。 若要通过托管项目尝试此操作，请从“工具”->“选项”->“项目和解决方案”打开“轻型解决方案加载”。

  ![Visual Studio 2017 中的选项对话框](../ide/media/vs2017ide-LightweightSolutionLoad.PNG "Visual Studio 2017 - 选项对话框 - 轻型解决方案加载")

### <a name="faster-on-demand-loading-of-extensions"></a>按需加载扩展速度更快
Visual Studio 可以移动自身的扩展（以及第三方扩展），从而根据需要加载扩展，而不是在 IDE 启动时加载。 想了解哪些扩展会影响启动、解决方案加载和键入性能？ 可以在“帮助”->“管理 Visual Studio 性能”中查看此信息。

  ![Visual Studio 2017 中的选项对话框](../ide/media/vs2017ide-manage-vs-perf.png "Visual Studio 帮助对话框 - 性能管理")

## <a name="productivity-improvements"></a>提高工作效率

### <a name="sign-in-across-multiple-accounts"></a>使用多个帐户登录  
我们在 Visual Studio 中引入了新的标识服务，使你可在团队资源管理器、Azure 工具、Windows 应用商店发布等之间共享用户帐户。

你还能在更长的时间内保持登录状态。 Visual Studio 不会每隔 12 小时就要求你再次登录。 若要了解详细信息，请参阅 [Fewer Visual Studio Sign-in Prompts](https://blogs.msdn.microsoft.com/visualstudio/2016/08/15/fewer-visual-studio-sign-in-prompts/)（更少的 Visual Studio 登录提示）博客文章。

### <a name="manage-your-extensions-with-roaming-extensions-manager"></a>利用漫游扩展管理器管理扩展
现在登录 Visual Studio 时，能更轻松地通过你最喜爱的扩展设置每个开发环境。 通过在云中创建同步列表，新漫游扩展管理器会跟踪所有你喜欢的扩展。  

若要查看 Visual Studio 中的扩展列表，请单击“工具”>“扩展”>“更新”，再单击“漫游扩展管理器”。

![Visual Studio 2017 - 扩展和更新对话框](../ide/media/vs2017ide-extensions-and-updates.png "Visual Studio 2017-“工具”>“扩展和更新”对话框")

漫游扩展管理器会跟踪安装的所有扩展，但你可以选择要添加到漫游列表的扩展。

![Visual Studio 2017 - 扩展和更新对话框](../ide/media/vs2017ide-RoamingExtensionManager.png "Visual Studio 2017 - 漫游扩展管理器")

使用漫游扩展管理器时，列表中会出现 3 种图标类型：
* ![“漫游”图标](../ide/media/vs2017ide-roamedicon.png "“漫游”图标") ***“漫游”***：表示存在于漫游列表中，但未在计算机上安装的扩展。
  （可通过“下载”按钮安装这些扩展。）
* ![“漫游且已安装”图标](../ide/media/vs2017ide-roamedinstalledicon.png "“漫游且已安装”图标") ***“漫游且已安装”***：表示存在于漫游列表中且已在此环境中安装的所有扩展。
  （如果确定不希望漫游，可通过“停止漫游”按钮删除它们。）
* ![“已安装”图标](../ide/media/vs2017ide-installedicon.png "“已安装”图标") ***“已安装”***：表示此环境中已安装、但不属于漫游列表的所有扩展。
  （可通过“启动漫游”按钮将扩展添加到漫游列表。）

登录时下载的所有扩展都将作为“漫游且已安装”的内容添加到列表，因此将包含在漫游列表中，可从任何计算机对其进行访问。

### <a name="experience-live-architecture-dependency-validation-and-live-unit-testing"></a>体验实时体系结构依赖关系验证和实时单元测试

现在当你在代码编辑器中键入代码时，Visual Studio 可以通过使用依赖项验证图（也称为层关系图） 来实时通知你体系结构依赖项规则冲突。

“错误列表”中显示错误，文本编辑器中的波形曲线显示此违反行为的精确位置。 现在降低了引入非必需依赖关系的可能性。

![体系结构的实时验证](../ide/media/vs2017ide-LiveArchitectureDepedendencyValidation.png "体系结构依赖关系的实时验证")

#### <a name="live-unit-testing"></a>实时单元测试：

在 Visual Studio Enterprise 2017 中，当你进行编码时，实时单元测试能够在编辑器中提供实时单元测试结果和代码覆盖率。 该功能可用于适用于 .NET Framework 的 C# 和 Visual Basic 项目，并支持 MSTest xUnit 和 NUnit 这三种测试框架。

![实时单元测试](../ide/media/lut-codewindow.png "Visual Studio 的 Enterprise 版本中新增的实时单元测试功能的示例")

有关详细信息，请参阅 [Visual Studio 2017 Enterprise 中的实时单元测试](https://blogs.msdn.microsoft.com/visualstudio/2017/03/09/live-unit-testing-in-visual-studio-2017-enterprise/)博文。

### <a name="devops"></a>DevOps
#### <a name="redgate-data-tools"></a>Redgate Data Tools：
现在可以在以下版本的 Visual Studio 2017 中使用 Redgate Data Tools，将 DevOps 功能扩展到 SQL Server 数据库开发。

Visual Studio 2017 Enterprise 随附：
- [Redgate ReadyRoll Core](http://www.red-gate.com/products/sql-development/readyroll/entrypage/microsoft-and-readyroll?utm_source=microsoft&utm_medium=link&utm_campaign=readyroll&utm_term=docs-newinvs) 有助于开发迁移脚本、使用源代码管理功能来管理数据库更改，并安全地自动部署 SQL Server 数据库更改和应用更改。
- [Redgate SQL Prompt Core](http://www.red-gate.com/products/sql-development/sql-prompt/entrypage/microsoft-and-sql-prompt?utm_source=microsoft&utm_medium=link&utm_campaign=sqlprompt&utm_term=docs-newinvs) 提供智能代码填写帮助，有助于更快更准确地编写 SQL。 SQL Prompt 可自动完成数据库、系统对象和关键字，并在你键入时提供列建议。 这样一来，代码不仅更简洁，而且错误也少了，因为无需记住每个列名称或别名。

Visual Studio 2017 所有版本随附：
- [Redgate SQL Search](http://www.red-gate.com/products/sql-development/sql-search/?utm_source=microsoft&utm_medium=link&utm_campaign=sqlsearch&utm_term=docs-newinvs) 有助于跨多个数据库快速查找 SQL 片段和对象，从而提高工作效率。

若要了解详细信息，请参阅我们的 [Visual Studio 2017 中的 Redgate Data Tools](https://blogs.msdn.microsoft.com/visualstudio/2017/03/07/redgate-data-tools-in-visual-studio-2017/) 博文。

### <a name="visual-studio-ide-enhancements"></a>Visual Studio IDE 增强功能
#### <a name="interact-with-git"></a>与 Git 进行交互：
在 Visual Studio 中处理项目时，可以对代码进行设置，并将其快速提交和发布到 Git 服务。 还可以通过单击 IDE 右下角的按钮调出菜单来管理 Git 存储库。

![Visual Studio 2017 与 Git 进行交互对话框](../ide/media/vsIDE-GitInteraction.png "Visual Studio IDE 中的 Git 工具")

#### <a name="view-and-navigate-code-with-structure-visualizer"></a>通过结构可视化工具查看和导航代码：
结构可视化工具可以在代码上绘制结构参考线（也称为 缩进参考线）。 通过使用该工具，无需滚动即可将代码可视化，并随时了解你处于哪一段代码中。 悬停在行上时将显示工具提示，通过工具提示可以看到该代码段的开头及其父级。 通过 TextMate 语法以及 C#、Visual Basic 和 XAML 支持的所有语言都可以使用该工具。

![Visual Studio 2017 结构可视化工具](../ide/media/vsIDE-StructureVisualizer.png "Visual Studio 中的结构可视化工具")

#### <a name="experience-improved-navigation-controls"></a>体验经过改进的导航控件：
我们改善了导航体验，可让你更自信地从 A 导航到 B，同时减少此过程中的干扰。

* **转到** (Ctrl + F12) &ndash; 从任何基类型或成员转到其各种实现。

* **转到全部**（Ctrl+T 或 Ctrl+,）&ndash;直接导航到任何文件/类型/成员/符号声明。 可以筛选结果列表，也可以使用查询语法（例如使用“f searchTerm”导航到文件，使用“t searchTerm”导航到类型等）。

 ![改进后的“转到全部”](../ide/media/vs2017ide-navigation-go-to.png "改进后的“转到全部”功能的示例")

* **查找所有引用 (Shift+F12)** &ndash; 通过语法着色，可以按项目、定义和路径的组合对“查找所有引用”的结果进行分组。 还可以“锁定”结果，这样既可以继续查找其他引用，又不会丢失之前的结果。

 ![新的“查找所有引用”工具](../ide/media/vs2017ide-find-all-references.png "新的“查找所有引用”工具的示例")

* **缩进参考线** &ndash; 灰色的垂直虚线，作为代码中的结构参考线，可在你的可视范围内提供上下文。 可以通过热门的 Productivity Power Tool 进行识别。

若要深入了解新增的工作效率功能的详细信息，请参阅由 Mark Wilson-Thomas 发布的 [Productivity in Visual Studio 2017](https://blogs.msdn.microsoft.com/visualstudio/2016/11/28/productivity-in-visual-studio-2017-rc/)（使用 Visual Studio 2017 提高工作效率）博客文章。

### <a name="visual-c"></a>Visual C++
Visual Studio 中的若干改进包括：在 Visual Studio 中分发 C++ 核心准则、通过添加对 C++11 和 C++ 功能的增强支持更新编译器和添加和更新 C++ 库中的功能等。 我们还改进了 C++ IDE 的性能和安装工作负载等。

我们还修复了编译器和工具中的 250 多个 bug 和已报告问题，其中很多是客户通过 [Microsoft Connect](https://connect.microsoft.com/VisualStudio "Microsoft Connect") 提交的。

有关完整的详细信息，请参阅 [Visual 2017 中 Visual C++ 的新增功能](/cpp/top/what-s-new-for-visual-cpp-in-visual-studio)页。  

### <a name="debugging-and-diagnostics"></a>调试和诊断

#### <a name="run-to-click"></a>运行时单击：

现在，在调试过程中快进变得更容易，无需在要停止的行上设置断点。 若要在调试器中停止，只需将鼠标放在代码行上，然后单击出现在代码行旁边的图标即可。 下次在代码路径中命中该代码时，代码即会运行至该行并停在此处。

![Visual Studio 2017 调试 - 运行时单击](../ide/media/vs2017ide-RunToClick.png "Visual Studio 调试和诊断中的运行时单击")

#### <a name="the-new-exception-helper"></a>新的异常帮助器：

新的异常帮助程序可以帮助你一目了然地查看异常信息。 异常信息以压缩形式呈现，你可以即时访问内部异常。 诊断 NullReferenceException 时，在异常帮助程序中可以快速查看为 null 的内容。

![Visual Studio 中新的“异常帮助程序”对话框](../ide/media/vs2017ide-ExceptionHelper.png "新的“异常帮助程序”对话框")

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

