---
title: "使用针对 Visual Studio 的 R 工具的远程工作区 | Microsoft Docs"
ms.custom: 
ms.date: 4/27/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5778c9cf-564d-47b0-8d64-e5dc09162479
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
translation.priority.ht:
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 7a873df77756e5a957d327049566c8e0db1f3a8a
ms.openlocfilehash: 1016f07c0f4505f2dd652482dd4d568655565cf0
ms.contentlocale: zh-cn
ms.lasthandoff: 05/12/2017

---


# <a name="setting-up-remote-workspaces"></a>设置远程工作区

要使用针对 Visual Studio 的 R 工具 (RTVS) 的远程工作区，远程计算机上必须配置 SSL 以及本主题说所述的相应 R 服务。 

- [远程计算机要求](#remote-computer-requirements)
- [安装 SSL 证书](#install-an-ssl-certificate)
- [安装 R 服务](#install-r-services)
- [配置 R 服务](#configure-r-services)
- [疑难解答](#troubleshooting)

## <a name="remote-computer-requirements"></a>远程计算机要求

- Windows 10、Windows Server 2016 或 Windows Server 2012 R2。 RTVS 同时还要求
- [.NET Framework 4.6.1](https://www.microsoft.com/download/details.aspx?id=49981) 或更高版本

## <a name="install-an-ssl-certificate"></a>安装 SSL 证书

RTVS 要求通过 HTTP 实现所有与远程服务器的通信，这就要求服务器上必须有 SSL 证书。 可以使用受信任的证书颁发机构签名的证书（推荐），或自签名证书（连接时 RTVS 将发出警告）。 无论使用哪种证书，都需要将其安装在计算机上，并允许访问它的私钥。

### <a name="obtaining-a-trusted-certificate"></a>获取受信任的证书

受信任的证书由证书颁发机构颁发（有关背景知识，请参阅[维基百科中的证书颁发机构](https://en.wikipedia.org/wiki/Certificate_authority)）。 和获取政府身份证类似，此操作过程更多并且可能需要付费，但还是要验证请求和请求者的真实性。

证书中要求的键字段是 R 服务器计算机的完全限定域名。 证书颁发机构将要求证据，证明你已获得授权为服务器所属的域创建新服务器。

有关详细背景信息，请参阅维基百科中的[公钥证书](https://en.wikipedia.org/wiki/Public_key_certificate)。

### <a name="obtaining-a-self-signed-certificate"></a>获取自签名证书

和来自受信任证书颁发机构的证书相比，自签名证书更像是为自己创建一张身份证。 比起使用受信任的颁发机构，此操作毫无疑问简便许多，但是同样缺少强身份验证。这意味着攻击者可将自己的证书替换为未签名的证书，捕获客户端和服务器之间的所有流量。 因此，仅可在测试方案和受信任的网络中使用自签名证书，而不应在生产中使用它。

为此，在使用自签名证书连接服务器时，RTVS 总会发出下列警告：

![自签名证书警告对话框](~/rtvs/media/workspaces-remote-self-signed-certificate-warning.png)

颁发自签名证书：

1. 使用 Administrator 帐户登录到 R 服务器计算机。
1. 打开一个新的管理员 PowerShell 命令提示符，发布下列命令，将 `"remote-machine-name"` 替换为服务器计算机的完全限定域名。

    ```ps
    New-SelfSignedCertificate -CertStoreLocation Cert:\LocalMachine\My -DnsName "remote-machine-name"
    ```

1. 如果此前从未在 R 服务器计算机上运行过 PowerShell，则需运行下列命令来显式启用运行命令：

    ```ps
    Set-ExecutionPolicy -ExecutionPolicy RemoteSigned
    ```

有关背景信息，请参阅维基百科中的[自签名证书](https://en.wikipedia.org/wiki/Self-signed_certificate)。

### <a name="installing-the-certificate"></a>安装证书

要在远程计算机上安装证书，请从自命令提示符运行 `certlm.msc`（证书管理器）。 右键单击“个人”文件夹，选择“所有任务”>“导入”命令：

![导入证书命令](~/rtvs/media/workspaces-remote-certificate-import.png)


### <a name="granting-permissions-to-read-the-ssl-certificates-private-key"></a>授予读取 SSL 证书私钥的权限

导入证书后，即授予 `NETWORK SERVICE` 帐户读取私钥的权限，如下所示。 `NETWORK_SERVICE` 是用于运行 R 服务代理的帐户，也是终止服务器计算机的入站 SSL 连接的服务。

1. 从管理员命令提示符运行 `certlm.msc`（证书管理器）。
1. 展开“个人”>“证书”，右键单击证书，然后选择“所有任务”>“管理私钥”。
1. 邮件单击证书，在“所有任务”下选择“管理私钥”命令
1. 在出现的对话框中选择“添加”，然后输入 `NETWORK SERVICE` 作为帐户名：

    ![管理私钥对话框，添加 NETWORK_SERVICE](~/rtvs/media/workspaces-remote-manage-private-key-dialog.png)

1. 连续选择“确定”两次以消除对话框，并提交更改。


## <a name="install-r-services"></a>安装 R 服务

要运行 R 代码，远程计算机必须安装 R 解释器，如下所示：

1. 下载并安装下列内容之一：

    - [Microsoft R Open](https://mran.microsoft.com/open/)
    - [CRAN R for Windows](https://cran.r-project.org/bin/windows/base/)

    虽然二者功能相同，但 Microsoft R Open 另外还受益于 [Intel Math Kernel 库](https://software.intel.com/intel-mkl)的附加硬件加速线性代数库。

1. 运行 [R 服务安装程序](https://aka.ms/rtvs-services)并根据提示重启。 安装程序执行如下操作：

    -    在 `%PROGRAMFILES%\R Tools for Visual Studio\1.0\` 中创建一个文件夹，并复制所有必需的二进制文件。
    -    安装 `RHostBrokerService` 和 `RUserProfileService` 并配置为自动启动。
    -    将 `seclogon` 服务配置为自动启动。
    -    将 `Microsoft.R.Host.exe` 和 `Microsoft.R.Host.Broker.exe` 添加到默认端口 5444 上的防火墙入站规则。

重启计算机时，R 服务将自动启动：

- R 主机代理服务处理 Visual Studio 和计算机上 R 代码运行的进程之间的所有 HTTPS 流量。
- R 用户配置文件服务是处理 Windows 用户配置文件创建的特权组件。 它在新用户首次登陆 R 服务器计算机时被调用。

在服务管理控制台 (`compmgmt.msc`) 中可以看到它们。  

## <a name="configure-r-services"></a>配置 R 服务

当在远程计算机上运行 R 服务时，还需创建用户帐户、设置防火墙规则、配置 Azure 网络和配置 SSL 证书。

1. 用户帐户：为每个要访问远程计算机的用户创建帐户。 可以创建标准（非特权）本地用户帐户，也可以将 R 服务器计算机加入到域，并将相应的安全组添加到 `Users` 安全组。
1. 防火墙规则：默认情况下 `R Host Broker` 在 TCP 端口 5444 上进行侦听。 因此，请确保已同时为入站和出站流量启用 Windows 防火墙规则（对于安装包和类似的方案，出站是必需的）。  R 服务安装程序为内置的 Windows 防火墙自动设置这些规则。 但是，如果正在使用第三方防火墙，则仍需手动为 `R Host Broker` 开启端口 5444。
1. Azure 配置：如果远程计算机是 Azure 上的虚拟机，那么仍需要为 Azure 网络内的入站流量开启端口 5444，使其不受 Windows 防火墙影响。 有关详细信息，请参阅 Azure 文档中的[使用网络安全组筛选网络流量](https://docs.microsoft.com/azure/virtual-network/virtual-networks-nsg)。
1. 告知 R 主机代理要加载哪个 SSL 证书：如果正在 Intranet 服务器上安装证书，则服务器的完全限定域名与其 NETBIOS 名称有可能相同。 在这种情况下，无需进行任何操作，因为加载的是默认证书。

    但是，如果正在面向 Internet 的服务器（如 Azure VM）上安装证书，请使用服务器的完全限定域名 (FQDN)，这是因为面向 Internet 的服务器的 FQDN 不可能与其 NETBIOS 名称相同。

    要执行此操作，请导航到 R 服务的安装位置（默认为 `%PROGRAM FILES%\R Remote Service for Visual Studio\1.0`），在文本编辑器中打开 `Microsoft.R.Host.Broker.Config.json` 文件，然后将其内容替换为下列内容，将 CN 分配给任意服务器的 FQDN，例如 `foo.westus.cloudapp.azure.com`：

    ```json
    {
      "server.urls": "https://0.0.0.0:5444",
      "security": {
        "X509CertificateName": "CN=your-server-fully-qualified-domain-name"
      }
    }
    ```

    保存文件，重启计算机以应用更改。

## <a name="troubleshooting"></a>疑难解答

R 服务器计算机未响应，我该怎么办？

检查是否可以从命令行 ping 远程计算机：`ping remote-machine-name`。 如果 ping 失败，请确保计算机正在运行。

**问：R 交互窗口显示远程计算机已启动，为什么服务无法运行？**

原因可能有以下三种：

-    未在计算机上安装 [.NET Framework 4.6.1](https://www.microsoft.com/download/details.aspx?id=49981) 或更高版本。
-    未同时为端口 5444 上的入站和出站连接启用 `Microsoft.R.Host.Broker` 和 `Microsoft.R.Host` 的防火墙规则。
-    未安装具有 `CN=<remote-machine-name>` 的 SSL 证书。

执行上述更改后，重启计算机。 然后，确保 `RHostBrokerService` 和 `RUserPofileService` 通过任务管理器（服务选项卡）或 `services.msc` 运行。

**问：为什么连接到 R 服务器后，R 交互窗口显示“401 拒绝访问”？**

可能有两种原因：

- 一种很有可能的情况是 `NETWORK SERVICE` 帐户不具有对 SSL 证书私钥的访问权限。 请根据前面的指南，授予 `NETWORK SERVICE` 对私钥的访问权限。
- 请确保 `seclogon` 服务正在运行。 使用 `services.msc` 将 `seclogon` 配置为自动启动。                                                         
**问：为什么连接到 R 服务器后，R 交互窗口显示“404 未找到”？**

这可能是由于缺少 Visual C++ 可再发行库。 检查 R 交互窗口，查看是否有关于缺少库 (DLL) 的消息。 然后检查是否已安装 VS 2015 可再发行组件和 R。

**问：无法从 R 交互窗口访问 Internet/资源，我该怎么办？**

请确保 `Microsoft.R.Host.Broker` 和 `Microsoft.R.Host` 的防火墙规则允许端口 5444 上的出站访问。 应用更改后，重启计算机。

**问：我已尝试上述方法，但不起作用。现在该怎么办？**

请查看 `C:\Windows\ServiceProfiles\NetworkService\AppData\Local\Temp` 中的日志文件。 你将看到每个运行的 R 代理服务的实例都有一个单独的日志文件。 换而言之，如果出于任何原因要重新启动服务，随即将创建一个新的日志文件。 请查看拥有最新时间戳的日志文件，以寻找问题的线索。

