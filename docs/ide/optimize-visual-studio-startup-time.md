---
title: "优化 Visual Studio 启动时间 | Microsoft Docs"
ms.custom: 
ms.date: 8/31/2017
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
author: mikejo
ms.author: mikejo
manager: ghogen
f1_keywords:
- vs.performancecenter
ms.translationtype: HT
ms.sourcegitcommit: 4306111cd49a5299bfa5d4e5e22b212bc7799fe2
ms.openlocfilehash: 8e419de02104d30344b32e28174bd7de41f91677
ms.contentlocale: zh-cn
ms.lasthandoff: 09/06/2017

---

# <a name="optimize-visual-studio-startup-time"></a>优化 Visual Studio 启动时间
理想情况下，Visual Studio 应总是尽可能快地启动。 但是，Visual Studio 扩展和开启工具窗口会对启动时间产生负面影响，因为在启动时会自动加载它们。 在“管理 Visual Studio 性能”窗口中，用户可以看到影响 Visual Studio 启动时间的扩展和功能，并可以控制这些扩展和功能的加载行为。

有关提升性能的更多提示，请参阅 [Visual Studio 性能提示和技巧](../ide/visual-studio-performance-tips-and-tricks.md)。

## <a name="control-startup-behavior"></a>控制启动行为

为了避免延长启动时间，Visual Studio 2017 使用按需加载方法以避免在启动时加载扩展。 该行为意味着不会在 Visual Studio 启动后立即打开扩展，而是在启动后根据需要打开。 此外，由于在之前的 Visual Studio 会话中保持工具窗口的打开状态会使启动时间变慢，因此 Visual Studio 以更智能的方式打开工具窗口，从而避免影响启动时间。

如果 Visual Studio 检测到启动速度较慢，则会弹出一条消息，提示你导致速度变慢的扩展或工具窗口。 此消息还提供了指向“管理 Visual Studio 性能”对话框的链接。 也可以使用“帮助”>“管理 Visual Studio 性能”菜单命令，打开此窗口。

![“管理 Visual Studio 性能”- 弹出窗口显示“我们注意到扩展 ... 正在拖慢 Visual Studio”](../ide/media/vside_perfdialog_popup.png)

该对话框会列出影响启动性能的扩展和工具窗口。 通过此对话框可以更改扩展和工具窗口的设置以提高启动性能。

### <a name="change-extension-settings"></a>更改扩展设置

如果某个扩展使 Visual Studio 的启动变慢，那么选择它的一个扩展类型时，此扩展将显示在“管理 Visual Studio 性能”对话框中。 此对话框显示哪些扩展在启动时影响性能、何时加载解决方案以及何时在编辑器中键入内容。

![管理 Visual Studio 性能 - 扩展视图](../ide/media/vside_perfdialog_extensions.png)

如果对启动、解决方案加载或键入时间的影响严重到令人无法接受，请通过选择“禁用”按钮禁用该方案的扩展。 可以始终使用“扩展管理器”或“管理 Visual Studio 性能”对话框重新启用扩展，以用于以后的会话。

### <a name="change-tool-window-settings"></a>更改工具窗口设置

如果工具窗口使 Visual Studio 的启动变慢，而且你想更改此影响，则可以通过选择以下两个选项之一而不是“使用默认行为”来替代其行为：

- **启动时不显示窗口：**下一次打开 Visual Studio 时指定的工具窗口将始终关闭，即使它在上一个会话中保留打开状态。 可以从相应的菜单中打开工具窗口。
- **启动时自动隐藏窗口：**如果工具窗口在上一个会话中保留打开状态，则此选项将在启动时折叠工具窗口组，以避免初始化工具窗口。 如果经常使用工具窗口，那么这是一个不错的选择。因为工具窗口仍然可用，但不会再对 Visual Studio 启动时间产生负面影响。

![管理 Visual Studio 性能 - 工具窗口视图](../ide/media/vside_perfdialog_toolwindows.png)

可以随时返回到此对话框，更改任何给定工具窗口的设置。

## <a name="speed_up_solution_load"></a>在 Visual Studio 2017 中更快加载大型解决方案

Visual Studio 2017 引入了新功能“轻型解决方案加载”，可减少在 IDE 中加载大型解决方案所需的时间和内存。 如果你有包含多个 C#、VB 或 C++ 项目的大型解决方案，则启用轻型解决方案加载可能会看到显著的性能优势。 若要详细了解如何使用此功能从中受益，请参阅[优化解决方案加载](../ide/optimize-solution-loading-in-visual-studio)。

> [!NOTE]
> 此内容适用于 Visual Studio 2017 Update 3。

### <a name="enable-or-disable-lightweight-solution-load"></a>启用或禁用轻型解决方案加载

可以右键单击“解决方案资源管理器”中的解决方案名称，并选择“启用轻型解决方案加载”。 选择此选项后，需要关闭并重新打开解决方案，才能激活轻型解决方案加载。

![“解决方案资源管理器”](../ide/media/VSIDE_LSL_Solution_Setting.png)

若要配置轻型解决方案加载的全局设置，请参阅[优化解决方案加载](../ide/optimize-solution-loading-in-visual-studio.md#global_solution_load_settings)。

## <a name="see-also"></a>另请参阅
[Visual Studio 性能提示和技巧](../ide/visual-studio-performance-tips-and-tricks.md)

