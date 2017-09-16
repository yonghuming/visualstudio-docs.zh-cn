---
title: "Visual Studio 性能提示和技巧 | Microsoft Docs"
ms.date: 08/31/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugger
ms.assetid: 2fbcb59e-e981-4b40-8b7a-c1140d31ec4b
caps.latest.revision: 1
author: mikejo5000
ms.author: mikejo
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
ms.translationtype: HT
ms.sourcegitcommit: 4306111cd49a5299bfa5d4e5e22b212bc7799fe2
ms.openlocfilehash: fbaa543564506a99d3ed6833ec4d1f692fae43f7
ms.contentlocale: zh-cn
ms.lasthandoff: 09/06/2017

---
# <a name="visual-studio-performance-tips-and-tricks"></a>Visual Studio 性能提示和技巧

Visual Studio 性能建议适用于内存不足的情况，这种情况极少出现。 出现这种情况时，可优化某些未使用的 Visual Studio 功能。 以下提示不作为一般性建议。

> [!NOTE]
> 如果因为内存问题而在使用产品时遇到困难，请通过反馈工具告知我们。

## <a name="optimize-your-environment"></a>优化环境

- **使用 64 位操作系统**

    如果将系统从 Windows 32 位版本升级到 64 位版本，那么 Visual Studio 的可用虚拟内存量会从 2 GB 扩展到 4 GB。 这样，即使 Visual Studio 是 32 位进程，也可以处理更大的工作负荷。

    有关详细信息，请参阅[内存限制](https://msdn.microsoft.com/en-us/library/windows/desktop/aa366778(v=vs.85).aspx#memory_limits)和 [Using /LARGEADDRESSAWARE on 64-bit Windows](https://blogs.msdn.microsoft.com/oldnewthing/20050601-24/?p=35483/)（在 64 位 Windows 上使用 /LARGEADDRESSAWARE）。

## <a name="configure-solution-and-projects"></a>配置解决方案和项目

如果你的超大型解决方案中包含多个项目，可通过进行以下优化受益：

- **启用轻型解决方案加载**

    使用“轻型解决方案加载”可以延迟解决方案中某些项目的加载，从而提升内存和 CPU 性能。 还可对每个解决方案启用此功能。 默认情况下，此选项处于关闭状态。

    要启动“轻型解决方案加载”，请选择“工具”>“选项”>“项目和解决方案”>“轻型解决方案加载”。

    在此模式下，没有启用某些 IDE 功能。 若要确定此选择是否有所帮助，请参阅[缩短解决方案加载时间](https://blogs.msdn.microsoft.com/visualstudio/2016/10/11/shorter-solution-load-time-in-visual-studio-15/)和[优化解决方案加载](../ide/optimize-solution-loading-in-visual-studio)。

- **卸载项目**

    可通过使用右键单击上下文菜单，从解决方案资源管理器中卸载很少使用的各个项目。

- **重构解决方案**

    可以将解决方案拆分为多个较小的解决方案文件，并在这些文件中包含常用的项目。 此重构可大幅减少工作流的内存使用率。 此外，解决方案越小，加载速度越快。

## <a name="configure-debugging-options"></a>配置调试选项
如果经常在调试会话期间遇到内存不足的情况，可以通过更改一项或多项配置来优化性能。

- **启用“仅我的代码”**

    最简单的优化是启用“仅我的代码” 功能，启用此功能后只会加载你项目的符号。 启用此功能后，调试托管的应用程序 (.NET) 时可节省大量内存。 对于某些项目类型，此选项默认为启用状态。

    要启用“仅我的代码”，请选择“工具”>“选项”>“调试”>“常规”，然后选择“启用仅我的代码”。

- **指定要加载的符号**

    对于本机调试，加载符号文件 (.pdb) 会占用很多内存资源。 可通过配置调试程序符号设置来节省内存。 通常情况下，将解决方案配置为仅加载你项目中的模块。

    要指定符号加载，请选择“工具”>“选项”>“调试”>“符号”。

    将选项设置为“仅指定模块”，而不是“所有模块”，然后指定要加载的负载。 调试时，还可以在“模块”窗口中右键单击特定模块，将其显示包含在系统加载中。 （要在调试时打开窗口，请选择“调试”>“窗口”>“模块”。）

    有关详细信息，请参阅 [Understanding symbol files](https://blogs.msdn.microsoft.com/visualstudioalm/2015/01/05/understanding-symbol-files-and-visual-studios-symbol-settings/)（了解符号文件）。

- **禁用诊断工具**

    建议在使用 CPU 分析后将其禁用。 此功能可能会占用大量资源。 CPU 分析处于启用状态后，后续调试会话中会一直保持启用状态，因此可在其完成时将其显示关闭。 如果不需要提供的功能，可以通过在调试时禁用诊断工具节省一些资源。

    要禁用“诊断工具”，请启动一个调试会话，并选择“工具”>“选项”>“启用诊断工具”，然后取消选择该选项。

    有关详细信息，请参阅[分析工具](https://docs.microsoft.com/en-us/visualstudio/profiling/profiling-tools)。

## <a name="disable-tools-and-extensions"></a>禁用工具和扩展
某些工具或扩展可能会关闭以提高性能。

> [!TIP]
> 通常可以通过一次关闭一个扩展并重新检查性能来隔离性能问题。

### <a name="managed-language-services-roslyn"></a>托管的语言服务 (Roslyn)

有关 Roslyn 性能注意事项的信息，请参阅 [Performance considerations for large solutions] (https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions)（大型解决方案的性能注意事项）。

- **禁用完整解决方案分析**

    Visual Studio 对整个解决方案执行分析，以在调用生成前提供关于错误的丰富体验。 此功能可用于尽快速识别错误。 但是，对于超大型解决方案，这一功能可能会占用大量内存资源。 如果遇到内存不足或类似问题，可以禁用此体验并释放这些资源。 默认情况下，Visual Basic 启用此选项，而 C# 禁用此选项。

    要禁用“完整解决方案分析”，请选择“工具”>“选项”>“文本编辑器”>“<Visual Basic 或 C#>”。 然后选择“高级”，并取消选择“启用完整解决方案分析”。

- **禁用 CodeLens**

    Visual Studio 对显示的每个方法执行“查找所有引用”任务。 CodeLens 提供内联显示引用数目等功能。 工作在单独的进程（例如，ServiceHub.RoslynCodeAnalysisService32）中执行。 在超大型解决方案或资源受限的系统中，此功能对性能有显著影响，即使它的运行优先级较低。 如果在这过程中（例如，当在 4 GB 计算机上加载大型解决方案时）遇到高 CPU 或内存问题，可以尝试禁用此功能以释放资源。

    要禁用 CodeLens，请选择“工具”>“选项”>“文本编辑器”>“所有语言”>“CodeLens”，然后取消选择该功能。

    此功能在 Visual Studio Professional 和 Visual Studio Enterprise 中可用。

### <a name="other-tools-and-extensions"></a>其他工具和扩展

- **禁用扩展**

    扩展是添加到 Visual Studio 的附加软件组件，用于提供新功能或扩展现有功能。 扩展通常可能导致内存资源问题。 如果遇到内存资源问题，请尝试一次禁用一个扩展，并查看这将如何影响方案或工作流。

    要禁用扩展，请转到“工具”|“扩展和更新”，然后禁用特定扩展。

- **禁用 XAML 设计器**

    默认情况下，XAML 设计器处于启用状态，但是只会在打开 .XAML 文件时占用资源。 如果使用 XAML 文件，但不希望使用设计器功能，请禁用此功能以释放内存。

    要禁用 XAML 设计器，请转到“工具”>“选项”>“XAML 设计器”>“启用 XAML 设计器”，然后取消选择该选项。

- **删除工作负载**

    可以使用 Visual Studio 安装程序删除不再使用的工作负载。 此操作可以跳过不再使用的包和程序集，从而优化启动和运行时的资源占用。

## <a name="force-a-garbage-collection"></a>强制垃圾回收

CLR 使用垃圾回收内存管理系统。 在此系统中，内存有时会被不再需要的对象占用。 这一状态是临时的，垃圾回收器会基于其性能和资源使用情况试探法释放此内存。 可通过在 Visual Studio 中使用热键强制 CLR 回收任何未使用的内存。 如果有大量垃圾等待回收并已强制垃圾回收，可在任务管理器中看到 devenv.exe 进程的内存使用率降低。 很少需要使用此方法。 但是，在完成一个资源占用较高的操作（如完整生成、调试会话或解决方案打开事件）后，此方法有助于确定进程实际在使用的内存量。 由于 Visual Studio 属于混合型（托管和本机），因此本机分配器和垃圾回收器有时可能会竞争有限的内存资源。 在内存使用率较高的情况下，这可能有助于强制垃圾回收器运行。

要强制垃圾回收，请使用热键：Ctrl+Alt+Shift+F12、Ctrl+Alt+Shift+F12（按两次）。

如果强制垃圾回收确实可让方案正常工作，请通过 Visual Studio 反馈工具提交报告，因为这一行为可能是一个 Bug。

有关 CLR 垃圾回收器的详细描述，请参阅 [Fundamental of Garbage Collection](https://msdn.microsoft.com/en-us/library/ee787088(v=vs.110).aspx)（垃圾回收的基本原理）。

## <a name="see-also"></a>另请参阅  
 [Visual Studio IDE](../ide/index.md)

