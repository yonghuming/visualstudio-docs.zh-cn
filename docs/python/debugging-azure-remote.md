---
title: "使用针对 Visual Studio 的 Python 工具进行 Azure 远程调试 | Microsoft Docs"
ms.custom: 
ms.date: 3/7/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d68fdc53-65a1-423c-8964-9815dbb3387e
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
translationtype: Human Translation
ms.sourcegitcommit: a42f5a30375192c89c9984e40ba0104da98d7253
ms.openlocfilehash: ad4cbf1305eec911aa5d6267fefc2c30f622e69a
ms.lasthandoff: 03/07/2017

---

# <a name="remotely-debugging-python-code-on-azure"></a>在 Azure 上远程调试 Python 代码

Visual Studio 中的 Python 支持包括远程调试在 Azure 应用服务上运行的 Python 代码。 与简单的远程调试不同，此方案中的目标计算机不能直接通过 TCP 访问，因此 Visual Studio 提供一个通过 HTTP 公开调试器协议的代理。 使用 Web 模板创建的项目在生成的 `web.debug.config` 文件中自动配置此代理。 如 [发布到 Azure 应用服务](template-web.md#publishing-to-azure-app-service)中所述发布项目的调试配置时，同时启用了远程调试。

由于 Azure 远程调试使用 Web 套接字，因此必须通过 [Azure 门户](https://portal.azure.com)为应用服务启用套接字，方法是转到“设置”>“应用程序设置”并将“常规设置”>“Web 套接字”切换为“打开”，然后选择“保存”应用更改。 （请注意，“调试”设置不适用于调试 Python。）

![在 Azure 门户中启用 Web 套接字](media/azure-remote-debugging-enable-web-sockets.png)

项目正确部署并启用 Web 套接字后，可以从 Visual Studio 中的“服务器资源管理器”（“视图”>“服务器资源管理器”）附加到应用服务。 在“Azure”>“应用服务”下找到站点和适用的资源组，右键单击，并选择“附加调试器(Python)”。 （请注意，“附加调试器”命令适用于 IIS 下运行的 .NET 应用程序，仅在你共同托管 .NET 代码与 Python 应用时才有用。）

Visual Studio 可能会直接转到一组用于直接附加的指令，如下面的[不使用服务器资源管理器进行附加](#attaching-without-server-explorer)中所述。 如果没有看到“附加调试器(Python)”命令或 Visual Studio 未能附加到站点，请参阅 [Azure 远程调试故障排除](debugging-azure-remote-troubleshooting.md)。

如果附加成功，Visual Studio 会切换到调试器视图；工具栏应指示正在调试的进程，例如 `wss://` URI：

![调试 Azure 应用服务 Web 站点](media/azure-remote-debugging-attached.png)

附加后，调试体验与常规远程调试体验大体相同，但受几个限制约束。 特别是，通过 FastCGI 处理传入请求并将它们委托给 Python 代码的 IIS Web 服务器具有针对处理请求的超时设置，其默认值为 90 秒。 如果处理请求花费的时间长于&90; 秒（例如，由于进程在断点处暂停），IIS 将终止该进程，这将立即结束调试会话。 

## <a name="attaching-without-server-explorer"></a>不使用服务器资源管理器进行附加

若要直接将调试器附加到应用服务，请按照 Visual Studio 部署到站点 `<site_url>/ptvsd` 的 WebSocket 代理信息页（如 `ptvsdemo.azurewebsites.net/ptvsd`）上提供的说明操作。 访问此页面还可验证代理是否已正确配置：

![Azure 远程调试代理信息页](media/azure-remote-debugging-proxy-info-page.png)

依照说明，需要使用 `web.debug.config`（每次发布项目时重新生成）中的机密构造 URL。 此文件在解决方案资源管理器中默认隐藏，并且不包括在项目中，因此需要显示所有文件或在单独的编辑器中打开它。 打开该文件后，请记下 appSetting 名为 `WSGI_PTVSD_SECRET` 的值：

![在 Azure 应用服务中确定调试器终结点](media/azure-remote-debugging-secret.png)

现在需要的 URL 采用 `wss://<secret>@<site_name>.azurewebsites.net/ptvsd` 形式，需将字符串中的 &lt;secret&gt; 和 &lt;site_name&gt; 替换为特定值。

若要附加调试器，请选择“调试”>“附加到进程”，在“传输”下拉列表中选择“Python 远程调试”，将 URL 输入到“限定符”文本框，然后按 Enter。 如果 Visual Studio 可成功连接到应用服务，它将在列表中显示单个 Python 进程。 选择它，然后选择“附加”启动调试：

![使用“附加到进程”对话框附加到 Azure 网站](media/azure-remote-debugging-manual-attach.png)

