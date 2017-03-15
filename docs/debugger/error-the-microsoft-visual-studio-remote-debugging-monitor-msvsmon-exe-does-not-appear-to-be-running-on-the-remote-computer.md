---
title: "错误:“Microsoft Visual Studio 远程调试监视器”(MSVSMON.EXE) 似乎没有在远程计算机上运行。 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.error.server_machine_no_default"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 86db9931-50e3-4095-b161-802ed8ef39c9
caps.latest.revision: 21
caps.handback.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 错误:“Microsoft Visual Studio 远程调试监视器”(MSVSMON.EXE) 似乎没有在远程计算机上运行。
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

此错误消息表示 Visual Studio 未能在远程计算机上找到 Visual Studio 远程调试监视器的正确实例。 必须安装 Visual Studio 远程调试监视器以便进行远程调试。 有关下载和设置远程调试器的信息，请参阅 [在设备上安装远程工具](../Topic/Set%20Up%20the%20Remote%20Tools%20on%20the%20Device.md)。  
  
> [!IMPORTANT]
>  如果你认为你因产品 Bug 而收到此消息，请向 Visual Studio 报告此问题[发送笑脸](../Topic/Visual%20Studio%20Send%20a%20Smile%20Instructions.md)。 如果需要更多帮助，请参阅 [与我们交流](../ide/talk-to-us.md) 了解与 Microsoft 联系的方法。  
  
## 我在 Visual Studio 2010 或更早版本中进行调试时收到了此消息  
 当你使用的 Visual Studio 是 Visual Studio 2010 或更早版本时，如果文件和打印机共享未启用，则也可能收到此错误。若要了解有关此问题的详细信息，请参阅本文档的 Visual Studio 2010 版本：[错误：Microsoft Visual Studio 远程调试监视器 \(MSVSMON.EXE\) 似乎没有在远程计算机上运行。\- Visual Studio 2010](https://msdn.microsoft.com/en-us/library/ms164726\(v=vs.100\).aspx)  
  
## 我在本地调试时收到了此消息  
 如果在本地调试时收到此消息，问题可能出在你的防病毒软件或第三方防火墙。 Visual Studio 是一个 32 位应用程序，因此它使用 64 位的远程调试器版本来调试 64 位应用程序。 两个进程使用本地计算机内的本地网络进行通信。 计算机会持续进行通信，但第三方安全软件可能会阻止通信。  
  
 以下各节列出其他一些你可能收到此消息的原因，以及解决此问题的操作。  
  
## 远程计算机不可访问  
 尝试 [ping](https://technet.microsoft.com/en-us/library/ee624059\(v=ws.10\).aspx) 远程计算机。 如果它不响应 ping 操作，则远程工具也将无法连接。 请尝试重新启动远程计算机，或者确保它在网络上正确配置。  
  
## 远程调试器的版本不匹配 Visual Studio 的版本  
 在本地运行的 Visual Studio 的版本必须与远程计算机上运行的远程调试监视器的版本匹配。 若要解决此问题，请下载并安装匹配的远程调试监视器版本。 转到[下载中心](http://www.microsoft.com/en-us/download)以查找正确版本的远程调试器。  
  
## 本地和远程计算机具有不同的身份验证模式  
 本地和远程计算机需要使用相同的身份验证模式。 若要解决此问题，请确保这两台计算机使用相同的身份验证模式。 有关身份验证模式的详细信息，请参阅 [Windows 身份验证概述](https://technet.microsoft.com/en-us/library/hh831472.aspx)。  
  
## 远程调试器使用不同的用户帐户运行  
 可通过下列方法之一解决此问题：  
  
-   你可以停止远程调试器，并使用本地计算机上使用的帐户重新启动它。  
  
-   你可以使用“\/allow \<用户名\>”参数 `msvsmon /allow <username@computer>` 从命令行启动远程调试器  
  
-   你可以将此用户添加到远程调试器权限（在远程调试器窗口“工具\/权限”）。  
  
-   如果你不能使用前面步骤中的方法，可以允许任何用户进行远程调试。 在远程调试器窗口中，转到“工具\/选项”对话框。 选中“无身份验证”后，可选中“允许任何用户进行调试”。 但仅当你别无选择或在专用网络上操作时才应使用此选项。  
  
## 远程计算机上的防火墙不允许对远程调试器的传入连接  
 Visual Studio 计算机上的防火墙和远程计算机上的防火墙都必须配置为允许在 Visual Studio 和远程调试器之间进行通信。 有关远程调试器使用的端口的信息，请参阅 [远程调试器端口分配](../debugger/remote-debugger-port-assignments.md)。 有关配置 Windows 防火墙的信息，请参阅 [配置 Windows 防火墙以便进行远程调试](../debugger/configure-the-windows-firewall-for-remote-debugging.md)。  
  
## 防病毒软件正在阻止连接  
 Windows 防病毒软件允许远程调试器连接，但某些第三方防病毒软件可能会阻止它们。 查看你防病毒软件的文档以了解如何允许这些连接。  
  
## 网络安全策略阻塞远程计算机和 Visual Studio 之间的通信  
 查看网络安全以确保它没有阻止通信。 有关 Windows 网络安全策略的详细信息，请参阅[安全管理](https://msdn.microsoft.com/en-us/library/windows/desktop/ms721855\(v=vs.85\).aspx)。  
  
## 网络太忙无法支持远程调试  
 你可能需要在另一个时间进行远程调试，或重新安排另一个时间进行网络上的工作。  
  
## 更多帮助  
 若要获取更多远程调试器的帮助（包括命令行开关），请在浏览器中打开以下内容：  
  
 **res:\/\/C:\\Program%20Files\\Microsoft%20Visual%20Studio%2014.0\\Common7\\IDE\\Remote%20Debugger\\x64\\msvsmon.exe\/help.htm**  
  
## 请参阅  
 [远程调试错误和疑难解答](../debugger/remote-debugging-errors-and-troubleshooting.md)