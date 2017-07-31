---
title: "优化 Visual Studio 启动时间 | Microsoft Docs"
ms.custom: 
ms.date: 7/20/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- startup time [Visual Studio]
- optimizing startup time [Visual Studio]
- speed up start time [Visual Studio]
ms.assetid: d1508121-8499-4084-8eb5-fa89fa7b17d3
caps.latest.revision: 4
author: kempb
ms.author: kempb
manager: ghogen
f1_keywords:
- vs.performancecenter
ms.translationtype: HT
ms.sourcegitcommit: c3521e1de25854db012cb91bbe09d9463ecb42c7
ms.openlocfilehash: af1ff0dbeeb30e6b3169c6a94dab8da50085bf20
ms.contentlocale: zh-cn
ms.lasthandoff: 07/21/2017

---

# <a name="optimize-visual-studio-startup-time"></a>优化 Visual Studio 启动时间
理想情况下，Visual Studio 应总是尽可能快地启动。 但是，Visual Studio 扩展和开启工具窗口会对启动时间产生负面影响，因为在启动时会自动加载它们。 在“管理 Visual Studio 性能”窗口中，用户可以看到影响 Visual Studio 启动时间的扩展和功能，并可以控制这些扩展和功能的加载行为。

## <a name="control-startup-behavior"></a>控制启动行为

为了避免延长启动时间，Visual Studio 2017 使用按需加载方法以避免在启动时加载扩展。 该行为意味着不会在 Visual Studio 启动后立即打开扩展，而是在启动后根据需要打开。 此外，由于在之前的 Visual Studio 会话中保持工具窗口的打开状态会使启动时间变慢，因此 Visual Studio 以更智能的方式打开工具窗口，从而避免影响启动时间。

如果 Visual Studio 检测到启动速度较慢，则会弹出一条消息，提示你导致速度变慢的扩展或工具窗口。 该消息还提供了“管理 Visual Studio 性能”对话框的链接，该对话框还可以使用“帮助 > 管理 Visual Studio 性能”菜单命令打开。

![“管理 Visual Studio 性能”- 弹出窗口显示“我们注意到扩展 ... 正在拖慢 Visual Studio”](../ide/media/vside_perfdialog_popup.png)

该对话框会列出影响启动性能的扩展和工具窗口。 通过此对话框可以更改扩展和工具窗口的设置以提高启动性能。

### <a name="change-extension-settings"></a>更改扩展设置

如果某个扩展使 Visual Studio 的启动变慢，那么选择它的一个扩展类型时，此扩展将显示在“管理 Visual Studio 性能”对话框中。 该对话框会显示启动时影响性能的扩展、加载解决方案的时间以及在编辑器中键入的时间。

![管理 Visual Studio 性能 - 扩展视图](../ide/media/vside_perfdialog_extensions.png)

如果对启动、解决方案加载或键入时间的影响严重到令人无法接受，请通过选择“禁用”按钮禁用该方案的扩展。 可以始终使用“扩展管理器”或“管理 Visual Studio 性能”对话框重新启用扩展，以用于以后的会话。

### <a name="change-tool-window-settings"></a>更改工具窗口设置

如果工具窗口使 Visual Studio 的启动变慢，而且你想更改此影响，则可以通过选择以下两个选项之一而不是“使用默认行为”来替代其行为：

- **启动时不显示窗口：**下一次打开 Visual Studio 时指定的工具窗口将始终关闭，即使它在上一个会话中保留打开状态。 可以从相应的菜单中打开工具窗口。
- **启动时自动隐藏窗口：**如果工具窗口在上一个会话中保留打开状态，则此选项将在启动时折叠工具窗口组，以避免初始化工具窗口。 如果经常使用工具窗口，那么这是一个不错的选择。因为工具窗口仍然可用，但不会再对 Visual Studio 启动时间产生负面影响。

![管理 Visual Studio 性能 - 工具窗口视图](../ide/media/vside_perfdialog_toolwindows.png)

可以随时返回到此对话框，更改任何给定工具窗口的设置。

## <a name="speed-up-solution-load"></a>加速解决方案的加载

Visual Studio 2017 支持“轻型解决方案加载”的新功能，可减少在 IDE 中加载大型解决方案所需的时间和内存。 如果有包含多个 C#、VB 和/或 C++ 项目的大型解决方案，则启用轻型解决方案加载可能会看到显著的性能优势。

由于启用轻型解决方案加载时某些 IDE 功能不是完全可用的，因此默认情况下此功能处于关闭状态。 以下各节可帮助你决定是否启用此功能。

### <a name="enable-lightweight-solution-load"></a>启用轻型解决方案加载

可以针对整个 IDE 或单个解决方案启用轻型解决方案加载。

若要更改为所有项目和解决方案设置的轻型解决方案加载，请转到“工具 > 选项 > 项目和解决方案 > 常规”，并选择以下三个加载选项之一：

![“工具选项”对话框](../ide/media/VSIDE_LightweightSolutionLoad.png)

- **让 Visual Studio 选择最适合我的解决方案的内容：**Visual Studio 通过在打开每个解决方案时对其进行分析来确定是否应用轻型解决方案加载。 
- **启用：**为此解决方案启用轻型解决方案加载，而不考虑 IDE 范围的设置。
- **禁用：**为此解决方案禁用轻型解决方案加载，而不考虑 IDE 范围的设置。

若要对单个解决方案启用轻型解决方案加载，请选择“解决方案资源管理器”中的顶层解决方案节点。 在“属性”窗口中，为“轻型加载”属性选择“默认”、“启用”或“禁用”。

![“解决方案资源管理器”](../ide/media/VSIDE_LSL Solution Setting.png)

还可以右键单击“解决方案资源管理器”中的顶层解决方案节点，并选择“启用轻型解决方案加载”（如果该功能目前已禁用）或“禁用轻型解决方案加载”（如果该功能目前已启用）：

更改轻型解决方案加载设置后，此更改将在下次加载解决方案时生效。 不需要重新启动 IDE。

### <a name="automatically-enable-lightweight-solution-load"></a>自动启用轻型解决方案加载

在 Visual Studio 2017 中打开大型解决方案时，你可能会看到一个弹出消息，提示你启用轻型解决方案加载。 仅针对包含多个 C#、VB 或 C++ 项目的解决方案显示此消息。 选择启用仅对此解决方案激活的轻型解决方案加载。 IDE 范围的设置不会更改。

![弹出窗口](../ide/media/VSIDE_LSL Popup.png)

可以稍后在解决方案的“属性”窗口中禁用轻型解决方案加载。

### <a name="limitations"></a>限制

启用轻型解决方案加载后，IDE 的大多数功能都完全可用。 但是，某些 IDE 功能和第三方扩展可能不完全兼容。  启用轻型解决方案加载后以下功能无法使用：

- 启用轻型解决方案加载后，某些第三方扩展可能会发生意外行为。
- 开始调试后“编辑并继续”功能在未加载的项目中不起作用。 在此类项目中包含的文件为只读文件，如果尝试编辑则会报告项目未加载的错误。
- 启用轻量级解决方案加载后，F# 项目可能无法正确生成，且符号在“转到”中可能不完全可用。

