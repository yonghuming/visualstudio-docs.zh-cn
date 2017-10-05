---
title: "如何： 诊断扩展性能 |Microsoft 文档"
ms.custom: 
ms.date: 11/08/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 46b0a1e3-7e69-47c9-9d8d-a1815d6c3896
caps.latest.revision: 1
author: BertanAygun
ms.author: bertaygu
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
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: b78a02b9d780b9556cbbf42fce04b1da06e22833
ms.contentlocale: zh-cn
ms.lasthandoff: 09/26/2017

---
# <a name="measuring-extension-impact-in-startup"></a>测量扩展中启动的影响

## <a name="focus-on-extension-performance-in-visual-studio-2017"></a>重点介绍在 Visual Studio 2017 扩展性能

根据客户反馈，Visual Studio 2017 版本重点区域之一已启动和解决方案负载性能。 作为 Visual Studio 平台团队，我们具有已处理时通常提高启动和解决方案负载性能，我们遥测表明已安装的扩展也可能对这些方案产生相当大的影响。

若要帮助用户了解这种影响，我们以通知用户的慢速扩展的 Visual Studio 中添加一项新功能。 在 Visual Studio 会检测速度变慢解决方案负载或启动一个新的扩展，用户将看到一个通知 IDE 指向新的"管理 Visual Studio 性能"对话框中。 此对话框还始终可以通过浏览以前检测到的扩展的帮助菜单访问。

![管理 Visual Studio 性能](media/manage-performance.png)

本文档旨在帮助扩展开发人员描述如何计算扩展影响，如何它可以进行分析本地测试如果扩展中可能显示为性能影响扩展。

## <a name="how-extensions-can-impact-startup"></a>如何扩展可能会影响启动

要影响启动性能扩展的最常见方式之一是通过选择其中一个已知的启动 UI 上下文，如 NoSolutionExists 或 ShellInitialized 自动加载。 在启动期间被激活，这些 UI 上下文，包括"ProvideAutoLoad"属性与这些上下文其定义中的任何包将加载和初始化在该时间。

当我们会度量的扩展的影响时，我们将主要专注于通过选择上面的上下文中自动加载这些扩展所花费的时间。 测量时间将包括但不是限于：

* 同步的包的扩展程序集的加载
* 同步的包的包类构造函数中所用的时间
* 在同步的包的包初始化 （或 SetSite） 方法中所用的时间
* 异步包的上述操作在后台线程上运行，并因此从监视中排除
* 在计划包初始化期间在主线程上运行任何异步工作中所花费的时间
* 所用的事件处理程序，具体而言 shell 初始化上下文激活或 shell 僵停状态更改时间
* 从 Visual Studio 2017 Update 3 开始，我们将还启动监视所花费的时间在空闲调用命令行程序初始化之前。 空闲处理程序中的长时间操作还会导致无响应的 IDE 和影响由用户感觉的启动时间。

我们还增加了从 Visual Studio 2015，以帮助删除程序包添加到自动负载的需要，将推迟到更具体的情况下，用户也将某些更，以使用扩展，或者在加载时减少扩展影响其负载的多个功能自动。

你可以在以下文档中找到有关这些功能的更多详细信息：

[基于规则的 UI 上下文](how-to-use-rule-based-ui-context-for-visual-studio-extensions.md)： 围绕 UI 上下文的更丰富的基于规则引擎允许你创建基于项目类型、 版本和功能的自定义上下文。 这些自定义上下文可用于在更具体的方案，例如具有而不是启动; 某项特定功能的项目存在期间加载的包或允许[命令可见性，以将绑定到自定义上下文](https://msdn.microsoft.com/en-us/library/bb166512.aspx)基于项目功能或其他可用的搜索词，因此不再需要加载的包，以注册命令状态查询处理程序。

[异步包支持](how-to-use-asyncpackage-to-load-vspackages-in-the-background.md): Visual Studio 2015 中的新 AsyncPackage 基类允许 Visual Studio 包要加载在后台以异步方式如果包加载请求了自动负载特性或异步服务查询. 此后台加载允许 IDE 以始终保持响应时在后台中初始化该扩展，并且不会影响启动和解决方案的负载等关键方案。

[异步服务](how-to-provide-an-asynchronous-visual-studio-service.md)： 有了异步包支持，我们还增加了对支持异步查询服务，并且能够注册异步服务。 更重要的我们正在处理转换核心 Visual Studio 服务以支持异步查询，以便在后台线程中出现的大部分异步查询中的工作。 SComponentModel （Visual Studio MEF 主机） 是现在支持异步查询，以允许扩展以支持异步加载完全的主要服务之一。

## <a name="reducing-impact-of-auto-loaded-extensions"></a>减少影响自动加载扩展

如果包仍需要将自动在启动加载，务必最大程度减少在包初始化以减少的可能性会影响启动扩展过程完成的工作。

可能会导致包初始化的成本要高一些示例包括：

### <a name="use-of-synchronous-package-load-instead-of-asynchronous-package-load"></a>使用同步包负载而非异步包负载

因为默认情况下，同步的包加载到主线程上，我们鼓励具有自动加载包，如前面所述改为使用异步包基类的扩展所有者。 更改自动加载的包，以支持异步加载将也更加轻松地解决下面的其他问题。

### <a name="synchronous-filenetwork-io-requests"></a>同步的文件/网络 IO 请求

理想情况下任何同步的文件或网络 IO 请求应在主线程中避免因为它们的影响将取决于机状态和较长时间的时间在某些情况下可以阻止。

使用异步包加载和异步 IO Api 应确保包初始化不会阻止这种情况下中的主线程和用户可以继续使用 Visual Studio 进行交互，而在后台发生输入/输出请求。

### <a name="early-initialization-of-services-components"></a>服务，组件的早期初始化

在包初始化的常见模式之一是初始化由或提供的该包在包构造函数或初始化方法中的服务。 虽然这可确保服务可供使用，它还可以添加不必要的成本打包加载如果不立即使用这些服务。 而是应按需尽量减小在包初始化完成的工作初始化此类服务。

对于由包的全局服务，你可以使用采用延迟初始化的服务，仅当请求的组件时的函数的 AddService 方法。 为了在包中使用的服务，你可以利用 Lazy<T>或 AsyncLazy<T>以确保在首次使用初始化/查询服务。

## <a name="measuring-impact-of-auto-loaded-extensions-using-activity-log"></a>测量影响自动加载扩展使用活动日志

从 Visual Studio 2017 Update 3 开始，Visual Studio 活动日志将现在包含的条目的包的性能影响在启动和解决方案加载过程。 若要查看这些度量值，你必须使用 /log 开关启动 Visual Studio 并打开 ActivityLog.xml 文件。

在活动日志中，该项目将在"管理 Visual Studio 性能"源下，和将看起来类似下面：

```Component: 3cd7f5bf-6662-4ff0-ade8-97b5ff12f39c, Inclusive Cost: 2008.9381, Exclusive Cost: 2008.9381, Top Level Inclusive Cost: 2008.9381```

这意味着该包处理 GUID"3cd7f5bf-6662-4ff0-ade8-97b5ff12f39c"所用的 Visual Studio 中启动 2008 ms。 请注意当计算的包的影响，会出现 savigs 用户看到时它们会禁用该包的扩展时，Visual Studio，考虑为主号码顶部级别成本。

## <a name="measuring-impact-of-auto-loaded-extensions-using-perfview"></a>测量影响自动加载使用 PerfView 的扩展

尽管代码分析可帮助标识可能会降低包初始化的代码路径，则还可以通过使用 PerfView 等应用程序以了解在 Visual Studio 启动包负载的影响利用跟踪。

PerfView 是一个系统宽跟踪工具，将帮助你了解应用程序由于 CPU 使用率或阻止系统调用中的热路径。 下面是上分析一个使用 PerfView 在可用扩展示例的一个快速示例[Microsoft Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=28567)。

**示例代码：**

此示例基于示例下面代码中，旨在显示这种情况下，一些常见的延迟原因：

```csharp
protected override void Initialize()
{
    // Initialize a class from another assembly as an example
    MakeVsSlowServiceImpl service = new MakeVsSlowServiceImpl();

    // Costly work in main thread involving file IO
    string systemPath = Environment.GetFolderPath(Environment.SpecialFolder.Windows);
    foreach (string file in Directory.GetFiles(systemPath))
    {
        DateTime creationDate = File.GetCreationTime(file);
    }

    // Costly work after shell is initialized. This callback executes on main thread
    KnownUIContexts.ShellInitializedContext.WhenActivated(() =>
    {
        DoMoreWork();
    });

    // Start async work on background thread
    DoAsyncWork().Forget();
}

private async Task DoAsyncWork()
{
    // Switch to background thread to do expensive work
    await TaskScheduler.Default;
    System.Threading.Thread.Sleep(500);
}

private void DoMoreWork()
{
    // Costly work
    System.Threading.Thread.Sleep(500);
    // Blocking call to an asynchronous work.
    ThreadHelper.JoinableTaskFactory.Run(async () => { await DoAsyncWork(); });
}
```

**记录使用 PerfView 跟踪：**

一旦你设置你的 Visual Studio 环境与您安装的扩展，你可以通过打开 PerfView 收集对话框从菜单并打开"收集"记录启动的跟踪。

![perfview 收集菜单](media/perfview-collect-menu.png)

默认选项将为 CPU 占用率提供调用堆栈，但由于我们感兴趣以及阻塞时间，你还应启用"线程时间"堆栈。 设置准备就绪后，可单击"开始收集"，启动 Visual Studio，一旦开始录制。

停止收集之前，你想要确保完全初始化 Visual Studio、 完全可见的主窗口，如果你扩展具有自动显示任何 UI 块，它们都是可见的。 Visual Studio 将会完全加载并初始化你的扩展后，你可以停止录制分析跟踪。

**分析跟踪与 PerfView:**

完成记录后 PerfView 将自动打开跟踪，并展开选项。

为此示例的目的，我们关注的是主要的"线程时间堆栈"视图，其中你可以在"高级组"下找到。 该视图将显示通过包括 CPU 时间和阻塞的时间，例如磁盘 IO 或等待句柄的方法在一个线程上所花费的总时间。

 ![线程时间堆栈](media/perfview-thread-time-stacks.png)

 时打开"时间堆栈线程"视图，则应选择"devenv"进程开始分析。

PerfView 详细介绍了如何阅读更详细的分析自己帮助菜单下的时间堆栈的线程的指导。 对于此示例的目的，我们想要通过仅包括与我们包模块名称和启动线程的堆栈筛选进一步此视图。

1. 将"GroupPats"设置为要删除按默认添加任何分组的空文本。
2. 除了现有进程筛选器的组"IncPats"来包括程序集名称的一部分和启动线程。 在这种情况下，它应为"devenv;启动线程;MakeVsSlowExtension"。

现在视图将仅显示使用与扩展相关的程序集关联的成本。 在此视图中，随时下列出的启动线程的"Inc"（非独占成本） 列与我们筛选扩展，并将会影响启动。

对于一些有趣调用上面的示例将为堆栈：

1. IO 使用 System.IO 类： 而非独占成本的这些帧可能不是在跟踪中代价很高，它们是问题的可能的原因，由于文件 IO 速度将会相差计算机到计算机。

  ![系统 io 帧](media/perfview-system-io-frames.png)

2. 阻止调用在其他异步工作等待： 非独占时间将在此情况下表示主线程阻止对完成的异步工作的时间。

  ![阻止调用帧](media/perfview-blocking-call-frames.png)

另一种视图中将很有用，以确定的影响的跟踪中将"图像负载堆栈"。 你可以应用相同的筛选器应用于"线程时间堆栈"视图并找出所有的程序集加载，因为你自动加载的包执行的代码。

请务必为每个其他程序集将涉及额外的磁盘 I/O，从而可能会降低显著上较慢的计算机的启动加载程序集内的包初始化例程的数量降至最低。

## <a name="summary"></a>摘要

启动 Visual Studio 已我们不断获得的反馈区域之一。 我们如上文所述的目标是使所有用户能够以一致方式启动而不考虑组件和它们已安装的扩展体验，我们想要使用扩展所有者以帮助他们帮助我们实现该目标。 上述指南应有助于了解启动扩展影响和可以避免需要自动负载或加载它以异步方式对用户工作效率的影响降至最低。

