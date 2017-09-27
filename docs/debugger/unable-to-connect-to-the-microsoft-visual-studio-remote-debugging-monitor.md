---
title: "无法连接到 Microsoft Visual Studio 远程调试监视器 |Microsoft 文档"
ms.custom: 
ms.date: 08/24/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.debug.error.remote_debug
- vs.debug.error.firewall.remotemachine
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: a1d959fc-3817-491c-831b-e6b768a3877a
caps.latest.revision: 14
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
ms.sourcegitcommit: 1d4298d60886d8fe8b402b59b1838a4171532ab1
ms.openlocfilehash: 454e6919c2f2bcd56153eb222fbf59b1ddc1080e
ms.contentlocale: zh-cn
ms.lasthandoff: 09/26/2017

---
# <a name="unable-to-connect-to-the-microsoft-visual-studio-remote-debugging-monitor"></a>Unable to Connect to the Microsoft Visual Studio Remote Debugging Monitor
因为远程调试监视器未正确设置远程计算机上或远程计算机是由于网络问题或存在防火墙而无法访问，则可能出现此消息。
  
> [!IMPORTANT]
>  如果你认为你因产品 bug 而收到此消息，请[报告此问题](../ide/how-to-report-a-problem-with-visual-studio-2017.md)到 Visual Studio。 如果需要更多帮助，请参阅 [Talk to Us](../ide/talk-to-us.md) 了解与 Microsoft 联系的方法。

## <a name="specificerrors"></a>详细的错误消息是什么？

`Unable to Connect to the Microsoft Visual Studio Remote Debugging Monitor`消息是泛型。 通常情况下，更具体的消息包含在错误字符串，也许能够帮助你确定问题或搜索更精确的修补程序的原因。 下面是几个附加到主错误消息的更常见的错误消息：

- [调试器无法连接到远程计算机。调试器无法解析指定的计算机名](#cannot_connect)
- [连接请求被拒绝的远程调试器](#rejected)
- [无效访问内存位置](#invalid_access)
- [由远程计算机上运行指定的名称没有服务器](#no_server)
- [请求的名称是有效的但未找到请求的类型的任何数据](#valid_name)
- [目标计算机上的 Visual Studio 远程调试器无法重新连接到此计算机](#cant_connect_back)
- [访问被拒绝](#access_denied)
- [发生安全程序包特定错误](#security_package)

## <a name="cannot_connect"></a>调试器无法连接到远程计算机。 调试器无法解析指定的计算机名

尝试以下步骤：

1. 请确保您输入有效的计算机名称和端口号在**附加到进程**对话框中或在项目属性 (若要设置属性，请参阅[这些步骤](#server_incorrect))。 计算机名必须是以下格式：

    `computername:port`

    > [!NOTE]
    > 端口号必须与匹配[端口号的远程调试器](../debugger/remote-debugger-port-assignments.md)，后者*必须运行*目标计算机上。

2. 如果计算机名称不起作用，请尝试 IP 地址，然后改为端口号。

3. 请确保在目标计算机上运行远程调试器的版本匹配你的 Visual Studio 版本。 若要获取远程调试器的正确版本，请参阅[远程调试](../debugger/remote-debugging.md)。

    > [!TIP]
    > 如果你附加到进程，而且成功连接，但看不到所需的过程，选择**显示所有用户复选框的进程**。 如果你已连接在不同的用户帐户下，这将显示进程。

4. 如果这些步骤未解决此错误，请参阅[远程计算机不可访问](#dns)。

## <a name="rejected"></a>连接请求被拒绝的远程调试器

在**附加到进程**对话框框中，或在项目属性中，请确保远程计算机名称和端口号匹配远程调试器窗口中显示的名称和端口号。 如果不正确，修复，然后重试。

如果这些值是否正确，并且该消息指出了**Windows 身份验证**模式下，远程调试器处于正确的身份验证模式的检查 (**工具 > 选项**)。

## <a name="invalid_access"></a>无效访问内存位置

出现内部错误。 重新启动 Visual Studio，然后重试。

## <a name="no_server"></a>由远程计算机上运行指定的名称没有服务器

Visual Studio 无法连接到远程调试器。 出现此消息可能的原因：

- 可能在不同的用户帐户下运行远程调试器。 请参阅[这些步骤](#user_accounts)

- 在防火墙上阻止端口。 请确保防火墙是[不会阻止您的请求](#firewall)，特别是当你使用第三方防火墙。

- 远程调试器版本与 Visual Studio 不匹配。 若要获取远程调试器的正确版本，请参阅[远程调试](../debugger/remote-debugging.md)


## <a name="#valid_name"></a>请求的名称是有效的但未找到请求的类型的任何数据

远程计算机存在，但 Visual Studio 无法连接到远程调试器。 出现此消息可能的原因：

- DNS 问题正在阻止连接。 请参阅[这些步骤](#dns)。

- 可能在不同的用户帐户下运行远程调试器。 请按照[这些步骤](#user_accounts)。

- 在防火墙上阻止端口。 请确保防火墙是[不会阻止您的请求](#firewall)，特别是当你使用第三方防火墙。

- 远程调试器版本与 Visual Studio 不匹配。 若要获取远程调试器的正确版本，请参阅[远程调试](../debugger/remote-debugging.md)。

## <a name="cant_connect_back"></a>目标计算机上的 Visual Studio 远程调试器无法重新连接到此计算机

可能在不同的用户帐户下运行远程调试器。 在远程调试器中，打开**工具 > 权限**将用户添加到远程调试器权限。 有关详细信息，请参阅[使用不同的用户帐户运行远程调试器](#user_accounts)。

如果该错误消息还指出了防火墙，本地计算机上的防火墙可能阻止从远程计算机返回到 Visual Studio 的通信。 请参阅[这些步骤](#firewall)。

## <a name="access_denied"></a>访问被拒绝

如果你尝试在从 32 位计算机 （不支持） 的 64 位远程计算机上进行调试，你可能会看到此错误。

## <a name="security_package"></a>发生安全程序包特定错误

这可能是特定于 Windows XP 和 Windows 7 的旧问题。 请参阅此[信息](https://stackoverflow.com/questions/4786016/unable-to-connect-to-the-microsoft-remote-debugging-monitor-a-security-package)。 

## <a name="causes-and-recommendations"></a>原因和建议

### <a name="dns"></a>远程计算机不可访问 

如果你不能使用远程计算机名称进行连接，请尝试改为使用的 IP 地址。 你可以使用`ipconfig`要获取的 IPv4 地址的远程计算机上的命令行中。 如果你使用的主机文件，请验证已正确配置。

如果失败，请验证远程计算机可以访问网络上 ([ping](https://technet.microsoft.com/en-us/library/cc732509(v=ws.10).aspx)远程计算机)。 不支持通过 Internet 的远程调试，除非在某些 Microsoft Azure 方案。
  
### <a name="server_incorrect"></a>服务器名称不正确或第三方软件干扰远程调试器

在 Visual Studio 中，查看项目属性，并确保服务器名称正确。 请参阅主题[C# 和 Visual Basic](../debugger/remote-debugging-csharp.md#remote_csharp)和[c + +](../debugger/remote-debugging-cpp.md#remote_cplusplus)。 对于 ASP.NET，打开**属性 / Web / 服务器**或**属性 / 调试**具体取决于你的项目类型。

> [!NOTE]
> 如果你附加到进程，不使用项目属性中的远程设置。

如果服务器名称是否正确，则你的防病毒软件或第三方防火墙可能阻止远程调试器。 在本地调试时，这可能是因为 Visual Studio 是一个 32 位应用程序中，因此它使用 64 位版远程调试器来调试 64 位应用程序。 32 位和 64 位进程使用本地计算机内的本地网络进行通信。 计算机会持续进行网络通信，但第三方安全软件可能会阻止通信。

### <a name="user_accounts"></a>使用不同的用户帐户运行远程调试器 

远程调试器将默认情况下，仅接受来自连接启动的远程调试器和 Administrators 组的成员的用户。 其他用户必须显式授予权限。 
 
可通过下列方法之一解决此问题：  

-   将 Visual Studio 用户添加到远程调试器权限 (在远程调试器窗口中，选择**工具 > 权限**)。

-   在远程计算机，重新启动远程调试器下的相同用户帐户和你使用 Visual Studio 计算机的密码。

    > [!NOTE]
    > 如果你远程服务器上运行远程调试器，右键单击远程调试器应用，然后选择**以管理员身份运行**（或者，你可以运行远程调试器作为服务）。 如果你不远程服务器上运行它，只是它正常启动。
  
-   你可以使用从命令行启动远程调试器**/ 允许\<用户名 >**参数： `msvsmon /allow <username@computer>`。 
  
-   或者，你可以允许任何用户进行远程调试。 在远程调试器窗口中，转到**工具 > 选项**对话框。 选中“无身份验证”   后，可选中 “允许任何用户进行调试”。 但是，你应该尝试此选项，仅当其他选项失败，或如果您在专用网络上。

### <a name="firewall"></a>远程计算机上的防火墙不允许传入连接到远程调试器  
 Visual Studio 计算机上的防火墙和远程计算机上的防火墙都必须配置为允许在 Visual Studio 和远程调试器之间进行通信。 有关远程调试器使用的端口的信息，请参阅 [Remote Debugger Port Assignments](../debugger/remote-debugger-port-assignments.md)。 有关配置 Windows 防火墙的信息，请参阅 [Configure the Windows Firewall for Remote Debugging](../debugger/configure-the-windows-firewall-for-remote-debugging.md)。
  
### <a name="the-version-of-the-remote-debugger-doesnt-match-the-version-of-visual-studio"></a>远程调试器的版本的 Visual Studio 的版本不匹配  
 在本地运行的 Visual Studio 的版本必须与远程计算机上运行的远程调试监视器的版本匹配。 若要解决此问题，请下载并安装匹配的远程调试监视器版本。 若要获取远程调试器的正确版本，请参阅[远程调试](../debugger/remote-debugging.md)。
  
### <a name="the-local-and-remote-machines-have-different-authentication-modes"></a>本地和远程计算机具有不同的身份验证模式  
 本地和远程计算机需要使用相同的身份验证模式。 若要解决此问题，请确保这两台计算机使用相同的身份验证模式。 您可以更改身份验证模式。 在远程调试器窗口中，转到**工具 > 选项**对话框。
  
 有关身份验证模式的详细信息，请参阅 [Windows 身份验证概述](https://technet.microsoft.com/en-us/library/hh831472.aspx)。   
  
### <a name="anti-virus-software-is-blocking-the-connections"></a>防病毒软件正在阻止连接  
 Windows 防病毒软件允许远程调试器连接，但某些第三方防病毒软件可能会阻止它们。 查看你防病毒软件的文档以了解如何允许这些连接。  
  
### <a name="network-security-policy-is-blocking-communication-between-the-remote-machine-and-visual-studio"></a>网络安全策略阻塞远程计算机和 Visual Studio 之间的通信  
 查看网络安全以确保它没有阻止通信。 有关 Windows 网络安全策略的详细信息，请参阅[安全策略设置](/windows/device-security/security-policy-settings/security-policy-settings)。  
  
### <a name="the-network-is-too-busy-to-support-remote-debugging"></a>网络太忙无法支持远程调试  
 你可能需要在另一个时间进行远程调试，或重新安排另一个时间进行网络上的工作。  
  
## <a name="more-help"></a>更多帮助  
 若要获取更多远程调试器的帮助，请打开远程调试器的帮助页 (**帮助 > 用法**在远程调试器中)。
  
## <a name="see-also"></a>另请参阅  
 [远程调试](../debugger/remote-debugging.md)
