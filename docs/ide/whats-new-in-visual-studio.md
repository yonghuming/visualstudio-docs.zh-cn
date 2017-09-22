---
title: "Visual Studio 2017 中的新增功能 | Microsoft Docs"
ms.custom: 
ms.date: 08/22/2017
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
ms.technology:
- vs-acquisition
ms.translationtype: HT
ms.sourcegitcommit: 3cd705d703b3d745c502290422e29b3c6da39ee5
ms.openlocfilehash: 5bf00b7e5ed79f8679b837d0dcabf03550d2b849
ms.contentlocale: zh-cn
ms.lasthandoff: 09/06/2017

---
# <a name="what39s-new-in-visual-studio-2017"></a>Visual Studio 2017 中的新增功能
#### <a name="updated-for-the-153-release"></a>版本 15.3 的更新内容
为任何开发、应用和平台提供无与伦比的效率。 使用 Visual Studio 2017 开发适用于 Android、iOS、Windows、Linux、Web 和云的应用。 快速编码、轻松调试和诊断、时常测试，并且可以放心地进行发布。 还可通过构建自己的扩展，以便扩展和自定义 Visual Studio。 此版本发布之后，可使用版本控制、更具敏捷性且可高效协作！

以下是我们所做更改的高级扼要重述：

* **重新定义了基础知识**。 新的安装体验意味着安装速度更快，并且能够在需要时立即安装。 无论是要加载大型解决方案和项目，还是要处理代码文件夹或单个代码文件，Visual Studio 的启动速度都比以前更快。 Visual Studio 还可帮助你掌控全局，特别是对使用 DevOp 的团队而言。
* **性能和工作效率**。 我们专注于新型、现代化的移动、云和桌面开发功能。 此外，还改进了总体采集、性能和常规开发人员工作效率体验。 与以前相比，现在的 Visual Studio 启动速度更快、响应能力更强、使用的内存更少。
* **使用 Azure 开发云应用**。 通过内置的 Azure 工具套件，可以轻松地创建由 Microsoft Azure 提供支持的云优先应用。 借助 Visual Studio，可以轻松配置、构建、调试、打包和部署 Azure 上的应用和服务。
* **移动应用开发**。 在 Visual Studio 2017 中，可以使用 Xamarin 进行创新并快速得出结果。Xamarin 通过使用一个核心基本代码和技能集统一你的多平台移动需求。 利用现有的团队、技术投资和 C# 代码，在预算范围内提前实现优质的用户体验。 加速移动生命周期的每一步，提供一流的用户体验或一系列可提高员工工作效率的工作效率应用。
* 跨平台开发可向任意目标平台无缝提供软件。 通过 Redgate 数据工具将 DevOps 流程扩展到 SQL Server 中，并在 Visual Studio 中安全地自动处理数据库部署。 使用 Visual Studio Tools for Unity 开发和发布多平台游戏。 或使用 .NET Core 编写在 Windows、Linux 和 macOS 操作系统上运行的未修改的应用和库。 （15.3 中的新增功能：获取 .NET Core 2.0 SDK 的并排支持。）

> [!NOTE]
> 有关 Visual Studio 2017 中新增功能的完整列表，请参阅[发行说明](https://www.visualstudio.com/news/releasenotes/vs2017-relnotes)。

以下是关于 Visual Studio 2017 中最值得关注的改进及新增功能的详细信息。

## <a name="redefined-fundamentals"></a>重新定义了基础知识
### <a name="a-new-setup-experience"></a>新的安装体验

[下载 Visual Studio 2017](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) 或[检查 Visual Studio 系统要求](https://www.visualstudio.com/en-us/productinfo/vs2017-system-requirements-vs)

 通过 Visual Studio，可以在需要时更轻松快速地安装所需功能。 而且，还能完全卸载干净。

 安装 Visual Studio 时，可以注意到最重要的更改是全新的安装体验。 在“工作负荷”选项卡上，你将看到表示常见框架、语言和平台的分组安装选项。 它涵盖 Windows、Linux 和 iOS 上从 .NET 桌面开发到 C++ 应用程序开发的所有内容。

选择所需的工作负载，并在需要时对其进行更改。

 ![Visual Studio 2017 安装对话框](../install/media/install-visual-studio-enterprise.png "Visual Studio 2017 安装屏幕")

想要选择自己的组件而不是使用工作负载？ 请从安装程序选择“单个组件”选项卡。 想要在不更改 Windows 语言选项的情况下立即安装语言包？ 选择安装程序的“语言包”选项卡。  

若要更深入地了解新的安装体验，包括指导你进行演练的分步说明，请参阅[安装 Visual Studio](../install/install-visual-studio.md) 页。

## <a name="performance-and-productivity"></a>性能和工作效率
### <a name="sign-in-across-multiple-accounts"></a>使用多个帐户登录  
我们在 Visual Studio 中引入了新的标识服务，用户可在团队资源管理器、Azure 工具、Windows 应用商店发布等之间共享用户帐户。

你还能在更长的时间内保持登录状态。 Visual Studio 不会每隔 12 小时就要求你再次登录。 若要了解详细信息，请参阅 [Fewer Visual Studio Sign-in Prompts](https://blogs.msdn.microsoft.com/visualstudio/2016/08/15/fewer-visual-studio-sign-in-prompts/)（更少的 Visual Studio 登录提示）博客文章。

### <a name="start-visual-studio-faster"></a>更快地启动 Visual Studio
新的 Visual Studio 性能中心可以帮助你优化 IDE 启动速度。 性能中心列出了所有可能减缓 IDE 启动速度的扩展和工具窗口。 可用它来确定扩展何时启动，或工具窗口是否在启动时打开，从而提高启动性能。

### <a name="decrease-solution-load-time"></a>缩短解决方案加载时间
处理包含大量项目的解决方案并非意味着必须同时处理所有文件或项目。 现在，无需等待 Visual Studio 加载每个项目即可进行编辑和调试。 若要通过托管项目尝试此操作，请从“工具”->“选项”->“项目和解决方案”打开“轻型解决方案加载”。

  ![Visual Studio 2017 中的选项对话框](../ide/media/vs2017ide-lightweight-solution-load.png "Visual Studio 2017 - 选项对话框 - 适用于所有解决方案的轻型解决方案加载")

### <a name="faster-on-demand-loading-of-extensions"></a>按需加载扩展速度更快
Visual Studio 可以移动自身的扩展（以及第三方扩展），从而根据需要加载扩展，而不是在 IDE 启动时加载。 想了解哪些扩展会影响启动、解决方案加载和键入性能？ 可以在“帮助”->“管理 Visual Studio 性能”中查看此信息。

  ![Visual Studio 2017 中的选项对话框](../ide/media/vs2017ide-manage-vs-perf.png "Visual Studio 帮助对话框 - 性能管理")

#### <a name="manage-your-extensions-with-roaming-extensions-manager"></a>利用漫游扩展管理器管理扩展
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
在文本编辑器中键入代码时，Visual Studio 可以通过依赖项验证图（也称为层关系图） 来实时通知你体系结构依赖项规则冲突。

“错误列表”中显示错误，文本编辑器中的波形曲线显示此违反行为的精确位置。 现在降低了引入非必需依赖关系的可能性。

![体系结构的实时验证](../ide/media/vs2017ide-LiveArchitectureDepedendencyValidation.png "体系结构依赖关系的实时验证")

#### <a name="live-unit-testing"></a>Live Unit Testing
在 Visual Studio Enterprise 2017 中，当你进行编码时，实时单元测试能够在编辑器中提供实时单元测试结果和代码覆盖率。 该功能可用于 .NET Framework 及 .NET Core 的 C# 和 Visual Basic 项目，并支持 MSTest、xUnit 和 NUnit 三种测试框架。

![实时单元测试](../ide/media/lut-codewindow.png "Visual Studio 的 Enterprise 版本中新增的实时单元测试功能的示例")

有关详细信息，请参阅 [Visual Studio 2017 Enterprise 中的实时单元测试](https://blogs.msdn.microsoft.com/visualstudio/2017/03/09/live-unit-testing-in-visual-studio-2017-enterprise/)博文。

#### <a name="set-up-a-cicd-pipeline-to-run-automated-tests-efficiently"></a>设置 CI/CD 管道以高效运行自动测试
自动测试是任何 DevOps 管道的重要组成部分。 用户可以在更短的周期内，持续且可靠地测试并发布解决方案。 CI/CD（持续集成和持续交付）流有助于改善进程效率。

有关自动测试的详细信息，请参阅博文 [DevOps 中用于自动测试的 CI/CD 管道](https://blogs.msdn.microsoft.com/visualstudioalmrangers/2017/04/20/set-up-a-cicd-pipeline-to-run-automated-tests-efficiently/)。

此外，若要详细了解[用于 Visual Studio 的持续交付工具](https://marketplace.visualstudio.com/items?itemName=VSIDEDevOpsMSFT.ContinuousDeliveryToolsforVisualStudio) DevLabs 扩展中的新增功能，请参阅博文[有把握提交：提交时代码质量](https://blogs.msdn.microsoft.com/visualstudio/2017/08/21/committing-with-confidence-commit-time-code-quality-information-updated/)。

### <a name="a-focus-on-accessibility"></a>聚焦辅助功能
在 15.3 中，我们进行了超过 1,700 处目标修补，以提高 Visual Studio 与我们许多客户使用的辅助技术的兼容性。 在十几种情况下，我们提高了与屏幕阅读器、高对比度主题和其他辅助技术的兼容性，比以往更兼容。 同时，我们还对调试程序、编辑器和 shell 进行了重大改进。

有关详细信息，请参阅博文 [Visual Studio 2017 版本 15.3 中的辅助功能改进](https://blogs.msdn.microsoft.com/visualstudio/2017/08/14/accessibility-improvements-in-visual-studio-2017-version-15-3/)。

### <a name="visual-studio-ide-enhancements"></a>Visual Studio IDE 增强功能
#### <a name="use-new-refactorings"></a>使用新的重构
在 15.3 中，我们添加了几种新的重构，其中包括：
*   解决合并冲突
*   添加参数（从 CallSite 添加）
*   生成重写函数
*   添加命名参数
*   为参数添加 null 检查
*   将数字分隔符插入文本
*   更改数字文本的基数（例如，从十六进制改为二进制）
*   转换 if-to-switch
*   删除未使用的变量

有关详细信息，请参阅 [Visual Studio 中的重构、代码生成和快速操作](refactoring-code-generation-quick-actions.md)页。


#### <a name="interact-with-git"></a>与 Git 进行交互
在 Visual Studio 中处理项目时，可以对代码进行设置，并将代码快速提交和发布到 Git 服务。 还可以通过单击 IDE 右下角的按钮调出菜单来管理 Git 存储库。

![Visual Studio 2017 与 Git 进行交互对话框](../ide/media/vsIDE-GitInteraction.png "Visual Studio IDE 中的 Git 工具")

#### <a name="view-and-navigate-code-with-structure-visualizer"></a>通过结构可视化工具查看和导航代码
结构可视化工具可以在代码上绘制结构参考线（也称为 缩进参考线）。 使用该工具，无需滚动即可将代码可视化，并随时了解当前位于哪一代码块。 悬停在行上时将显示工具提示，通过工具提示可以看到该代码段的开头及其父级。 通过 TextMate 语法以及 C#、Visual Basic 和 XAML 支持的所有语言都可以使用该工具。

![Visual Studio 2017 结构可视化工具](../ide/media/vsIDE-StructureVisualizer.png "Visual Studio 中的结构可视化工具")

#### <a name="experience-improved-navigation-controls"></a>体验改进的导航控件
我们改善了导航体验，可让你更自信地从 A 导航到 B，同时减少此过程中的干扰。

* **转到** (Ctrl + F12) &ndash; 从任何基类型或成员转到其各种实现。

* **转到全部**（Ctrl+T 或 Ctrl+,）&ndash;直接导航到任何文件/类型/成员/符号声明。 可以筛选结果列表，也可以使用查询语法（例如使用“f searchTerm”导航到文件，使用“t searchTerm”导航到类型等）。

 ![改进后的“转到全部”](../ide/media/vs2017ide-navigation-go-to.png "改进后的“转到全部”功能的示例")

* **查找所有引用 (Shift+F12)** &ndash; 通过语法着色，可以按项目、定义和路径的组合对“查找所有引用”的结果进行分组。 还可以“锁定”结果，这样既可以继续查找其他引用，又不会丢失原始结果。

 ![新的“查找所有引用”工具](../ide/media/vs2017ide-find-all-references.png "新的“查找所有引用”工具的示例")

* **缩进参考线** &ndash; 灰色的垂直虚线，作为代码中的结构参考线，可在你的可视范围内提供上下文。 可以通过热门的 Productivity Power Tool 进行识别。

若要深入了解新增的工作效率功能的详细信息，请参阅由 Mark Wilson-Thomas 发布的 [Productivity in Visual Studio 2017](https://blogs.msdn.microsoft.com/visualstudio/2016/11/28/productivity-in-visual-studio-2017-rc/)（使用 Visual Studio 2017 提高工作效率）博客文章。

### <a name="visual-c"></a>Visual C++
Visual Studio 中的若干改进包括：使用 Visual Studio 分发 C++ 核心准则、通过添加对 C++11 和 C++ 功能的增强支持更新编译器以及添加和更新 C++ 库中的功能等。 我们还改进了 C++ IDE 的性能和安装工作负载等。

我们还修复了编译器和工具中的 250 多个 bug 和已报告问题，其中很多是客户通过 [Microsoft Connect](https://connect.microsoft.com/VisualStudio "Microsoft Connect") 提交的。

有关完整的详细信息，请参阅 [Visual 2017 中 Visual C++ 的新增功能](/cpp/top/what-s-new-for-visual-cpp-in-visual-studio)页。  

### <a name="debugging-and-diagnostics"></a>调试和诊断
#### <a name="run-to-click"></a>运行时单击：
现在，在调试过程中快进变得更容易，无需在要停止的行上设置断点。 在调试器中停止时，单击出现在代码行旁边的图标即可。 下次在代码路径中命中该代码时，代码即会运行至该行并停在此处。

![Visual Studio 2017 调试 - 运行时单击](../ide/media/vs2017ide-RunToClick.png "Visual Studio 调试和诊断中的运行时单击")

#### <a name="the-new-exception-helper"></a>新的异常帮助器：
新的异常帮助程序可以帮助你一目了然地查看异常信息。 异常信息以压缩形式呈现，你可以即时访问内部异常。 诊断 NullReferenceException 时，在异常帮助程序中可以快速查看为 null 的内容。

![Visual Studio 中新的“异常帮助程序”对话框](../ide/media/vs2017ide-ExceptionHelper.png "新的“异常帮助程序”对话框")

有关详细信息，请参阅 [Using the New Exception Helper in Visual Studio](https://blogs.msdn.microsoft.com/visualstudioalm/2016/03/31/using-the-new-exception-helper-in-visual-studio-15-preview/)（使用 Visual Studio 中的新异常帮助器）博客文章。

## <a name="cloud-app-development-with-azure"></a>使用 Azure 开发云应用
### <a name="azure-functions-tools"></a>Azure Functions 工具
作为“Azure 开发”工作负载的一部分，通过使用预编译的 C# 类库，我们加入了有助于开发 Azure 函数的工具。 现在，可以在自己的本地开发计算机上进行生成、运行和调试操作，并将其直接从 Visual Studio 发布至 Azure。

有关详细信息，请参阅[用于 Visual Studio 的 Azure Functions 工具](https://docs.microsoft.com/azure/azure-functions/functions-develop-vs)页。

## <a name="mobile-app-development"></a>移动应用开发
### <a name="xamarin"></a>Xamarin
作为“使用 .NET 的移动开发”工作负载的一部分，熟悉 C#、.NET 和 Visual Studio 的开发人员可使用 Xamarin 传递本地 Android、iOS 和 Windows 应用。 使用 Xamarin 开发移动应用（包括在 Android、iOS 和 Windows 设备上进行远程调试）时，开发人员同样可享受强大的功能和工作效率 &mdash; 无需学习 Objective-C 或 Java 等本机编程语言。

有关详细信息，请参阅 [Visual Studio 和 Xamarin](../cross-platform/visual-studio-and-xamarin.md) 页。

### <a name="entitlements-editor"></a>权利编辑器
15.3 中的新增功能：为满足 iOS 开发需求，我们添加了独立的权利编辑器。 它包含便于浏览、用户友好的 UI。 要启动它，请双击 entitlements.plist 文件。

![适用于 Xamarin 的权利编辑器](../ide/media/xamarin-entitlements-editor.png "适用于 Xamarin 的权利编辑器")

## <a name="cross-platform-development"></a>跨平台开发
### <a name="redgate-data-tools"></a>Redgate 数据工具
现在可以在以下版本的 Visual Studio 2017 中使用 Redgate Data Tools，将 DevOps 功能扩展到 SQL Server 数据库开发。

Visual Studio 2017 Enterprise 随附：
- [Redgate ReadyRoll Core](http://www.red-gate.com/products/sql-development/readyroll/entrypage/microsoft-and-readyroll?utm_source=microsoft&utm_medium=link&utm_campaign=readyroll&utm_term=docs-newinvs) 有助于开发迁移脚本、使用源代码管理功能来管理数据库更改，并安全地自动部署 SQL Server 数据库更改和应用更改。
- [Redgate SQL Prompt Core](http://www.red-gate.com/products/sql-development/sql-prompt/entrypage/microsoft-and-sql-prompt?utm_source=microsoft&utm_medium=link&utm_campaign=sqlprompt&utm_term=docs-newinvs) 提供智能代码填写帮助，有助于更快更准确地编写 SQL。 SQL Prompt 可自动完成数据库、系统对象和关键字，并在你键入时提供列建议。 这样一来，代码不仅更简洁，而且错误也更少，因为无需记住每个列名称或别名。

Visual Studio 2017 所有版本随附：
- [Redgate SQL Search](http://www.red-gate.com/products/sql-development/sql-search/?utm_source=microsoft&utm_medium=link&utm_campaign=sqlsearch&utm_term=docs-newinvs) 有助于跨多个数据库快速查找 SQL 片段和对象，从而提高工作效率。

若要了解详细信息，请参阅我们的 [Visual Studio 2017 中的 Redgate Data Tools](https://blogs.msdn.microsoft.com/visualstudio/2017/03/07/redgate-data-tools-in-visual-studio-2017/) 博文。

### <a name="visual-studio-tools-for-unity"></a>Visual Studio Tools for Unity
作为“适用于 Unity 的游戏开发”工作负载的一部分，我们添加了有助于跨平台开发的工具， 可用于创作 2D 和 3D 游戏及交互内容。 使用 Visual Studio 2017 和 Unity 5.6，一次创建即可发布到 21 个平台，包括所有移动平台、WebGL、Mac、PC 和 Linux 桌面、Web 或主机。

有关详细信息，请参阅 [Visual Studio Tools for Unity](../cross-platform/visual-studio-tools-for-unity.md) 页。

### <a name="net-core"></a>.NET 核心
.NET Core 是 .NET 标准的常规用途、模块化、跨平台和开放源代码实现，且包含许多与 .NET Framework 相同的 API。

.NET Core 平台由一些组件构成，其中包括托管的编译器、运行时、基类库和大量应用程序模型，如 ASP.NET 核心。 .NET Core 支持三种主要的操作系统 (OS)：Windows、 Linux 和 macOS。 可以在设备、云和嵌入式/IoT 方案中使用 .NET Core。

当前，它还包括了 Docker 支持

15.3 中的新增功能：Visual Studio 2017 版本 15.3 支持 .NET Core 2.0 开发。 （在 15.3 中，使用 .NET Core 2.0 前需分别下载并安装 .NET Core 2.0 SDK。）

有关详细信息，请参阅 [.NET Core 指南](https://docs.microsoft.com/dotnet/core/index)页。

## <a name="talk-to-us"></a>与我们交流  
 为什么将反馈发送至 Visual Studio 团队？ 因为我们认真对待客户反馈：正是它激励我们的行为。

如果有关于如何改进 Visual Studio 的建议，或想报告问题，请参阅[与我们交流](../ide/talk-to-us.md)页，了解详细信息。

### <a name="report-a-problem"></a>报告问题  
 有时，一条消息不足以说明所遇问题的总体影响。 如果遇到挂起、崩溃或其他性能问题，可利用“报告问题”工具与我们轻松共享重现步骤和支持文件（如屏幕快照以及跟踪和堆转储文件）。 有关如何使用此工具的详细信息，请参阅[如何报告问题](how-to-report-a-problem-with-visual-studio-2017.md)页。

### <a name="track-your-issue-in-connect"></a>在“连接”中跟踪你的问题  
 要跟踪 Visual Studio 反馈的状态，请转至[连接](http://connect.microsoft.com/)，并在此处报告 bug。 报告后，可返回至“连接”来跟踪其状态。

## <a name="see-also"></a>另请参阅
* [Visual Studio 2017 发行说明](https://www.visualstudio.com/news/vs2015-vs)
* [Visual C++ 中的新增功能](/cpp/top/what-s-new-for-visual-cpp-in-visual-studio)
* [C# 中的新增功能](https://docs.microsoft.com/dotnet/csharp/csharp-7)  
* [Team Foundation Server 中的新增功能](https://www.visualstudio.com/docs/whats-new)
* [Visual Studio for Mac 中的新增功能](https://www.visualstudio.com/vs/visual-studio-mac/)

