---
title: "调试已安装的应用程序包 (UWP) |Microsoft 文档"
ms.custom: H1Hack27Feb2017
ms.date: 07/17/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.debug.installedapppackagelauncher
- vs.debug.remote.connection
dev_langs:
- C++
- FSharp
- CSharp
- JScript
- VB
helpviewer_keywords: app package, debug
ms.assetid: 5a94ad64-100d-43ca-9779-16cb5af86f97
caps.latest.revision: "1"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 354c574a890ae0385a58594a22b3314a13b9d6b4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="debug-an-installed-app-package-in-visual-studio-uwp"></a>调试 Visual Studio (UWP) 的安装的应用包

您可以通过单击调试任何已安装的应用包**调试 > 其他调试目标 > 调试安装的应用程序包**。 此调试方法是可用的通用 Windows 应用 (UWP) 在这些设备上：

* Windows 10 （不支持在手机上）
* XBox
* HoloLens
* IoT

有关这些功能的详细信息，请参阅博客文章上更新[调试已安装的应用程序包](https://blogs.msdn.microsoft.com/visualstudioalm/2016/03/30/updates-for-debugging-installed-app-packages-in-visual-studio-2015-update-2/)和上的 post[生成通用 Windows 应用 (UWP)](https://blogs.msdn.microsoft.com/visualstudio/2016/08/02/universal-windows-apps-targeting-windows-10-anniversary-sdk/)。

## <a name="debug-an-installed-app-package-or-running-app-on-a-local-machine-or-device"></a>调试已安装的应用包或在本地计算机或设备上的运行应用

1. 使用 Visual Studio 中打开你 UWP 项目中，单击**调试 > 其他调试目标 > 调试安装的应用程序包**。

2. 选择**本地计算机**或**设备**。

     如果你选择**设备**，你的计算机必须物理连接到 Windows 10 设备。

     ![DebugInstalledAppPackage](../debugger/media/debug-installed-app-pkg.png "DebugInstalledAppPackage")

     当前正在运行安装应用包的显示下**运行**节点。 安装应用程序包都不会在下显示运行向上**未运行**。

3. 选择你想要调试在应用的名称**运行**或**未运行**选择**启动**或者，如果已在运行应用程序，选择**附加**.

     如果你选择**不启动，但在启动时调试我的代码**，这将导致 Visual Studio 调试器附加到你的应用程序，当你在自定义时启动。 这是一种可以调试从的控制路径有效[不同的启动方法](/windows/uwp/xbox-apps/automate-launching-uwp-apps)，如使用自定义参数的协议激活。

> [!NOTE]
> Visual Studio 也可以通过选择附加到任何运行的 UWP 应用进程**调试**，，然后**附加到进程**。 将附加到正在运行的进程不需要原始的 Visual Studio 项目中，但加载进程的符号将帮助显著调试你没有的原始代码的进程。
  
## <a name="remote"></a>调试远程计算机上的安装或运行应用程序 

当第一次调试远程计算机上安装的应用包时，Visual Studio 安装你的目标设备的远程工具的正确版本。 Windows 10 计算机、 XBox、 HoloLens 或 IoT 设备，必须是你的目标设备。

1. 在 Windows 10 设备上，启用[开发者模式](/windows/uwp/get-started/enable-your-device-for-development)。

2. 如果你连接到远程 PC 上手动首先运行前的创建者的更新版本的 Windows 10[安装并启动远程调试器](../debugger/remote-debugging.md)。

     对于 XBox、 HoloLens 或 IoT 设备，在运行 Windows 10 Creator 更新的 Windows 设备，你不必手动安装远程调试器。 当你部署应用时，将自动安装远程工具。

3. 单击**调试 > 其他调试目标 > 调试安装的应用程序包**。

4. 从第一个下拉列表中，选择**远程计算机**。

5. 键入的名称或你想要将附加到的计算机的 IP 地址。

     ![ChooseRemoteComputer](../debugger/media/debug-remote-app-pkg.png "ChooseRemoteComputer")

     如果您不能将使用计算机名称 (在选择后，**启动**)，改为使用的 IP 地址。 对于 XBox、 HoloLens 或 IoT 设备使用的 IP 地址。

5. 选择如何进行身份验证通过选择中的一个选项**身份验证模式**。

    对于大多数应用程序，请保留默认值，**世界 （未加密的协议）**。

6. 选择你想要调试在应用的名称**运行**或**未运行**选择**启动**或 （对于运行的应用）**附加**。

     如果你选择**不启动，但在启动时调试我的代码**，这将导致 Visual Studio 调试器附加到你的应用包，当你在自定义时启动。 这是一种可以调试从的控制路径有效[不同的启动方法](/windows/uwp/xbox-apps/automate-launching-uwp-apps)，如使用自定义参数的协议激活。

     当第一次调试连接的 XBox、 HoloLens 或 IoT 设备上安装的应用包时，Visual Studio 安装的目标设备的远程调试器的正确版本。 这可能需要很少的时间，你将看到一条消息``Starting remote debugger``时发生这种情况。

     > [!NOTE]
> 在呈现，XBox 或 HoloLens 设备将在附有如果它已在运行调试器的情况下重新启动应用。

> [!NOTE]
> UWP 应用可以进行开发和编译的 Windows 8.1 或更高版本，但要求运行 Windows 10。 如果你正在开发 Windows 8.1 PC 上的 UWP 应用，可以远程调试在另一台 Windows 10 设备上，运行的 UWP 应用，前提是主机和目标计算机位于同一 LAN。 若要执行此操作，请下载并在两台计算机上安装 Visual Studio 远程工具。 安装的版本必须匹配现有的已安装的 Visual Studio 版本，并且选择 (x86、 x64) 的体系结构还必须匹配的目标应用程序。
  
## <a name="see-also"></a>另请参阅  
 [在 Visual Studio 中进行调试](../debugger/index.md)  
 [调试器功能简介](../debugger/debugger-feature-tour.md)  
 [远程调试](../debugger/remote-debugging.md)  
 [配置 Windows 防火墙以便进行远程调试](../debugger/configure-the-windows-firewall-for-remote-debugging.md)  
 [远程调试器端口分配](../debugger/remote-debugger-port-assignments.md)  
 [远程调试错误和疑难解答](../debugger/remote-debugging-errors-and-troubleshooting.md)