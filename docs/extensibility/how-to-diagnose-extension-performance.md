---
title: "如何︰ 诊断扩展性能 |Microsoft 文档"
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
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: f1226c9bd42476acc9fb57be0a6df8058174fd4d
ms.lasthandoff: 02/22/2017

---
# <a name="measuring-extension-impact-in-startup"></a>衡量启动在扩展影响

## <a name="focus-on-extension-performance-in-visual-studio-2017"></a>重点介绍 Visual Studio 2017 扩展性能

根据客户反馈，Visual Studio 2017 发行版的关注领域之一已启动和解决方案负载性能。 尽管作为 Visual Studio 平台团队，我们一直在从事通常提高启动及解决方案负载性能，我们遥测表明已安装的扩展也可能对这些方案中产生相当大的影响。

为了帮助用户了解在这种影响，我们通知用户的慢速扩展 Visual Studio 中添加一项新功能。 当 Visual Studio 会检测减缓解决方案加载或启动一个新的扩展时，用户将看到在 IDE 中指向"管理 Visual Studio 性能"新建对话框的通知。 若要浏览先前检测到的扩展的帮助菜单也始终可以访问此对话框。

![管理 Visual Studio 性能](~/docs/extensibility/media/manage-performance.png)

本文档旨在帮助扩展开发人员通过说明如何计算扩展的影响以及如何您可以在此分析本地测试是否作为一种性能影响扩展，扩展可能会显示。

## <a name="how-extensions-can-impact-startup"></a>如何扩展可能会影响启动

扩展影响启动性能的最常见方式之一是通过选择自动的负载，如 NoSolutionExists 或 ShellInitialized 已知的启动 UI 上下文中的一个。 这些 UI 上下文被激活，在启动期间，将加载和初始化在该时间在与这些上下文其定义中包含"ProvideAutoLoad"属性的任何包。

当我们度量值的扩展的影响时，我们主要精力放上通过选择在上面的上下文中自动加载这些扩展程序所花费的时间。 测量时间将包括但不是限于︰

* 加载的扩展插件程序集的同步包
* 同步的包的包类构造函数中所用的时间
* 同步的包的包初始化 （或 SetSite） 方法中花费的时间
* 异步包的上述操作在后台线程上运行，并因此从监视中排除
* 计划包初始化过程在主线程上运行任何异步工作中花费的时间
* 所用的事件处理程序，特别是外壳程序初始化上下文激活或命令行程序僵停状态更改时间

我们添加了从 Visual Studio 2015 用于帮助进行无需将程序包添加到自动负载，将推迟到更具体的情况下，用户也将更有把握，若要使用扩展或减少扩展影响时自动加载其负载的多个功能。

您可以在以下文档中找到有关这些功能的更多详细信息︰

[基于 UI 上下文规则](how-to-use-rule-based-ui-context-for-visual-studio-extensions.md)︰ 围绕 UI 上下文的更丰富的基于规则引擎允许您创建基于项目类型、 特点和功能的自定义上下文。 这些自定义上下文可用来在更具体的方案，例如某项特定功能而不是启动; 具有的项目存在期间加载的包或允许[命令可见性，以绑定到自定义上下文](https://msdn.microsoft.com/en-us/library/bb166512.aspx)基于项目功能或其他可用的搜索词，因此无需加载的包，以注册命令状态查询处理程序。

[异步程序包支持](how-to-use-asyncpackage-to-load-vspackages-in-the-background.md)︰ 在 Visual Studio 2015 AsyncPackage 基类新允许 Visual Studio 包要加载在后台以异步方式如果包加载所请求的自动负载特性或异步服务查询。 此后台加载允许 IDE 以在后台中初始化扩展而不会影响关键方案，如启动和解决方案的负载始终保持响应。

[异步服务](how-to-provide-an-asynchronous-visual-studio-service.md)︰ 有了异步包支持，我们还添加了对以异步方式查询服务并能够注册异步服务的支持。 更重要的我们正在转换核心 Visual Studio 服务，以支持异步查询，以便在后台线程中出现的大部分异步查询中的工作。 SComponentModel （Visual Studio MEF 主机） 是现在支持异步查询，以允许扩展来支持异步加载完全的主要服务之一。

## <a name="reducing-impact-of-auto-loaded-extensions"></a>减少影响自动加载扩展

如果包仍需要将自动在启动时加载，务必减少包初始化要减少的机会影响启动扩展过程中完成的工作量。

可能会导致包初始化非常昂贵的一些示例包括︰

### <a name="use-of-synchronous-package-load-instead-of-asynchronous-package-load"></a>使用同步包负载，而不是异步的包加载

因为默认情况下，可将同步包加载到主线程上，所以我们建议将自动加载的程序包都如前面所述改为使用异步数据包基类的扩展所有者。 更改自动加载的包，以支持异步加载将也更加轻松地解决下面的其他问题。

### <a name="synchronous-filenetwork-io-requests"></a>同步文件/网络 IO 请求

理想情况下的任何同步文件或网络 IO 请求应避免在主线程因为它们的影响将取决于机器状态且为很长一段时间，在某些情况下可以阻止。

使用异步包加载和异步 IO Api，应确保包初始化不会阻塞主线程中这种情况下，用户可以继续使用 Visual Studio 进行交互，而在后台发生的 I/O 请求。

### <a name="early-initialization-of-services-components"></a>早期初始化的服务，组件

一个包初始化中的常见模式是初始化服务使用或由该包在包构造函数或 initialize 方法中提供。 虽然这可确保服务可供使用，它还可以添加不必要的成本进行打包加载如果不立即使用这些服务。 而是应该点播尽量减少中包初始化完成的工作初始化此类服务。

全局提供的服务包，您可以使用采用一个函数为仅在请求的组件时延迟初始化该服务的 AddService 方法。 对于包内所使用的服务，您可以利用 Lazy<T>或 AsyncLazy<T>以确保服务是在首次使用初始化/查询。

## <a name="measuring-impact-of-auto-loaded-extensions-using-perfview"></a>衡量影响自动加载使用 PerfView 扩展名

代码分析可帮助识别可能会拖慢包初始化的代码路径，而您也可以通过使用应用程序，如 PerfView 以了解在 Visual Studio 启动的包负载的影响利用跟踪。

PerfView 是将帮助您了解应用程序由于 CPU 使用率或阻止系统调用中的热路径的系统范围的跟踪工具。 下面是一个简单的示例在分析一个扩展插件示例使用 PerfView 网址[Microsoft Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=28567)。

**示例代码︰**

此示例基于示例下面代码中，旨在显示这种情况下，延迟导致一些常见原因︰

```c#
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

**记录使用 PerfView 跟踪︰**

一旦您安装 Visual Studio 环境与您安装的扩展，您可以通过打开 PerfView 收集对话框从菜单并打开"收集"记录启动的跟踪。

![perfview 收集菜单](~/docs/extensibility/media/perfview-collect-menu.png)

默认选项将为 CPU 占用率提供调用堆栈，但由于我们感兴趣以及阻塞时间，您还应启用"线程时间"堆栈。 准备好设置后可以单击"开始收集"并启动 Visual Studio 时，一旦开始录制。

停止收集之前，您想要确保完全初始化 Visual Studio，主窗口是完全可见，并且如果您的扩展有自动显示任何用户界面部分，它们都是可见的。 Visual Studio 已完全加载并初始化您的扩展后，你可以停止录制以分析该跟踪。

**分析使用 PerfView 跟踪︰**

一旦完成录制 PerfView 将自动打开跟踪并展开选项。

对于此示例的目的，我们是主要感兴趣的是"线程时间堆栈"视图可在"高级组"下找到。 此视图将显示由方法包括 CPU 时间和阻塞的时间，如磁盘 IO 或等待句柄的线程上所花费的总时间。

 ![线程时间堆栈](~/docs/extensibility/media/perfview-thread-time-stacks.png)

 当打开"时间堆栈线程"视图，您应选择"devenv"过程，以启动分析。

PerfView 提供了详细指导如何阅读更详细的分析自己帮助菜单下的时间堆栈的线程。 对于此示例中，我们想要通过仅包括与我们的包的模块名称和启动线程的堆栈筛选进一步此视图。

1. 将"GroupPats"设置为空的文本，若要删除默认情况下添加任何分组。
2. 除了现有进程筛选器的组"IncPats"来包括程序集名称的一部分并且启动线程。 在这种情况下，它应为"devenv;启动线程;MakeVsSlowExtension"。

现在该视图只显示与扩展相关的程序集与关联的成本。 在此视图中，在启动线程的"Inc"（非独占成本） 列下列出任何时候我们筛选扩展到相关，它将影响启动。

一些有趣的调用上面的示例将为堆栈︰

1. IO 使用 System.IO 类︰ 尽管这些框架中的非独占成本可能不在跟踪中开销非常大，它们是问题的可能的原因，由于文件 IO 速度将会在计算机之间相差。

  ![系统 io 帧](~/docs/extensibility/media/perfview-system-io-frames.png)

2. 阻塞等待其他异步工作的调用︰ 非独占时间将在这种情况下表示主线程受阻时在异步工作完成的时间。

  ![阻止调用框架](~/docs/extensibility/media/perfview-blocking-call-frames.png)

另一种视图将用于确定影响的跟踪中将"图像加载堆栈"。 可以将应用相同的筛选器应用到"时间堆栈线程"视图，并找出所有程序集加载，因为您自动加载的包执行的代码。

请务必为每个其他程序集将涉及额外的磁盘 I/O，从而可能会拖慢得多上较慢的计算机的启动加载的程序集内包初始化例程的数量降至最低。

## <a name="summary"></a>摘要

启动 Visual Studio 已成为我们不断地获得的反馈的领域之一。 我们正如前文所述的目标是所有用户都可以以一致方式启动体验而不考虑组件和已安装的扩展，我们想要使用扩展所有者能够帮助他们帮助我们实现这一目标。 上述指南应有助于了解扩展在启动时影响并也无需自动负载或将数据加载以异步方式来对用户工作效率的影响降至最低。
