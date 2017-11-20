---
title: "ClickOnce 部署中的特定错误的疑难解答 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Microsoft.VisualStudio.Publish.ClickOnceProvider.ErrorPrompt.UncRequired
- Microsoft.VisualStudio.Publish.ClickOnceProvider.ErrorPrompt.NoInstallUrl
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications, ClickOnce
- troubleshooting ClickOnce deployments
- ClickOnce deployment, troubleshooting
ms.assetid: 22dfe8f1-8271-4708-9c25-6bbb13920ac8
caps.latest.revision: "13"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 40c679811f137e77909395042d91d0458c874d90
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="troubleshooting-specific-errors-in-clickonce-deployments"></a>ClickOnce 部署中的特定错误的疑难解答
本主题列出了在部署时可能发生的以下常见错误[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]应用程序，并提供解决每个问题的步骤。  
  
## <a name="general-errors"></a>常规错误  
  
#### <a name="when-you-try-to-locate-an-application-file-nothing-occurs-or-xml-renders-in-internet-explorer-or-you-receive-a-run-or-save-as-dialog-box"></a>当你尝试找到一个.application 文件，会有任何反应，或 XML 呈现在 Internet Explorer 中，或接收一个运行或另存为对话框  
 此错误可能是由不在客户端的服务器上正确注册的内容类型 （也称为 MIME 类型） 引起的。  
  
 首先，请确保服务器配置为将.application 扩展名与内容类型"应用程序/x 的 ms-应用程序"关联。  
  
 如果服务器已正确配置，确保[!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)]在计算机上安装。 如果[!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)]安装后，你仍看到此问题，请尝试卸载并重新安装和[!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)]重新注册客户端上的内容类型。  
  
#### <a name="error-message-says-unable-to-retrieve-application-files-missing-in-deployment-or-application-download-has-been-interrupted-check-for-network-errors-and-try-again-later"></a>错误消息指出，"无法检索应用程序。 在部署中缺少的文件"或"已中断应用程序下载检查是否存在网络错误，稍后重试"  
 此消息指示所引用的一个或多个文件[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]无法下载清单。 若要调试此错误的最简单方法是尝试下载 URL，[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]指出其无法下载。 下面是一些可能的原因：  
  
-   如果日志文件将显示为"(403) 禁止访问"或"(404) 未找到，"验证是否已配置 Web 服务器，以便它不会阻止下载此文件。 有关详细信息，请参阅 [ClickOnce 部署中的服务器和客户端配置问题](../deployment/server-and-client-configuration-issues-in-clickonce-deployments.md)。  
  
-   如果服务器被阻止的.config 文件，请参阅明"下载错误，当你尝试安装时[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]具有.config 文件的应用程序"本主题中更高版本。  
  
-   确定此错误出现因为`deploymentProvider`部署清单中的 URL 指向用于激活的 URL 以外的其他位置。  
  
-   确保所有文件都都存在于服务器;[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]日志应该告诉你找不到的文件。  
  
-   查看是否存在网络连接问题;如果在下载客户端计算机脱机，会收到此消息。  
  
#### <a name="download-error-when-you-try-to-install-a-clickonce-application-that-has-a-config-file"></a>下载错误，当你尝试安装具有.config 文件的 ClickOnce 应用程序  
 默认情况下，基于 Visual Basic Windows 的应用程序包括 App.config 文件。 用户尝试从使用 Windows Server 2003 的 Web 服务器安装，因为该操作系统阻止安装的.config 文件，出于安全原因时，将会出现问题。 若要启用要安装的.config 文件，请单击**使用".deploy"文件扩展名**中**发布选项**对话框。  
  
 你还必须内容类型 （也称为 MIME 类型） 正确设置为.application、.manifest 和.deploy 文件。 有关详细信息，请参阅 Web 服务器文档。  
  
 有关详细信息，请参阅"Windows Server 2003:: Locked-Down 内容类型"[服务器和 ClickOnce 部署中的客户端配置问题](../deployment/server-and-client-configuration-issues-in-clickonce-deployments.md)。  
  
#### <a name="error-message-application-is-improperly-formatted-log-file-contains-xml-signature-is-invalid"></a>错误消息:"应用程序格式不正确";日志文件包含"XML 签名无效"  
 确保你已更新的清单文件且再次对其进行签名。 将你的应用程序重新发布使用[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]或 Mage 用于签署再次将应用程序。  
  
#### <a name="you-updated-your-application-on-the-server-but-the-client-does-not-download-the-update"></a>更新你的应用程序在服务器上，但客户端不会下载更新  
 通过完成以下任务之一可能解决此问题：  
  
-   检查`deploymentProvider`部署清单中的 URL。 确保你要更新中的相同位置的位，`deploymentProvider`指向。  
  
-   验证部署清单中的更新间隔。 如果此间隔设置为定期间隔，例如一次每六个小时，[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]将不会扫描更新之前经过此时间间隔。 你可以更改要在应用程序启动每次更新的扫描的清单。 更改的更新间隔是在开发期间一个方便的选项以验证正在安装更新，但它会减慢应用程序激活。  
  
-   请尝试在开始菜单上重新启动应用程序。 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]可能具有在后台，检测到更新，但将提示你在下一步激活上安装 bits。  
  
#### <a name="during-update-you-receive-an-error-that-has-the-following-log-entry-the-reference-in-the-deployment-does-not-match-the-identity-defined-in-the-application-manifest"></a>更新期间会接收以下日志条目的错误:"部署中的引用与应用程序清单中定义的标识不匹配"  
 因为你已手动编辑部署和应用程序清单，并导致无法包含其他不同步的一个清单中标识的程序集的说明，可能出现此错误。 程序集的标识由其名称、 版本、 区域性和公钥标记组成。 检查在你的清单中的标识说明并更正任何差异。  
  
#### <a name="first-time-activation-from-local-disk-or-cd-rom-succeeds-but-subsequent-activation-from-start-menu-does-not-succeed"></a>第一次从本地磁盘或 CD-ROM 激活成功，但从开始菜单的后续激活将不会成功  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]使用部署提供程序 URL 接收更新的应用程序。 验证 URL 指向的位置正确。  
  
#### <a name="error-cannot-start-the-application"></a>错误:"无法启动应用程序"  
 此错误消息通常指示没有安装到此应用程序问题[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]存储。 应用程序出现错误，或者存储已损坏。 日志文件可能会告诉您发生错误的位置。  
  
 你应执行以下操作：  
  
-   验证部署清单的标识、 应用程序清单的标识和标识的主应用程序 EXE 凭据全部独一无二。  
  
-   验证文件路径不超过 100 个字符。 如果你的应用程序包含的文件路径太长，你可能会超过上可以存储的最大路径限制。 请尝试缩短路径并重新安装。  
  
#### <a name="privatepath-settings-in-application-config-file-are-not-honored"></a>不遵循应用程序配置文件中的 PrivatePath 设置  
 若要使用 PrivatePath （合成探测路径），应用程序必须请求完全信任权限。 请尝试更改应用程序清单以请求完全信任，然后重试。  
  
#### <a name="during-uninstall-a-message-appears-saying-failed-to-uninstall-application"></a>卸载期间一条消息出现，礚猭卸载应用程序  
 此消息通常指示已删除应用程序或存储已损坏。 单击后**确定**、**添加或删除程序**项将被删除。  
  
#### <a name="during-installation-a-message-appears-that-says-that-the-platform-dependencies-are-not-installed"></a>在安装期间，将显示消息，指出未安装平台依赖项  
 缺少应用程序运行所需 GAC （全局程序集缓存） 中的先决条件。  
  
## <a name="publishing-with-visual-studio"></a>使用 Visual Studio 进行发布  
  
#### <a name="publishing-in-visual-studio-fails"></a>如何在 Visual Studio 中的发布将失败  
 确保你有权发布到服务器的目标。 例如，如果你登录到终端服务器计算机作为普通用户，不作为管理员，则您可能没有发布到本地的 Web 服务器所需的权限。  
  
 如果您要发布的 url，请确保目标计算机具有启用 FrontPage 服务器扩展。  
  
#### <a name="error-message-unable-to-create-the-web-site-site-the-components-for-communicating-with-frontpage-server-extensions-are-not-installed"></a>错误消息： 无法创建网站\<站点 >。 未安装用于与 FrontPage 服务器扩展进行通信的组件。  
 确保你有 Microsoft Visual Studio Web 创作组件安装在你发布从计算机上。 对于 Express 用户，默认情况下未安装此组件。 有关详细信息，请参阅[http://go.microsoft.com/fwlink/?LinkId=102310](http://go.microsoft.com/fwlink/?LinkId=102310)。  
  
#### <a name="error-message-could-not-find-file-microsoftwindowscommon-controls-version6000-culture-publickeytoken6595b64144ccf1df-processorarchitecture-typewin32"></a>错误消息： 找不到文件 Microsoft.Windows.Common 的控件，版本 = 6.0.0.0，区域性 = *，PublicKeyToken = 6595b64144ccf1df，ProcessorArchitecture =\*，类型 = win32  
 当你尝试发布启用了视觉样式的 WPF 应用程序时，会出现此错误消息。 若要解决此问题，请参阅[如何： 发布具有启用视觉样式的 WPF 应用程序](../deployment/how-to-publish-a-wpf-application-with-visual-styles-enabled.md)。  
  
## <a name="using-mage"></a>使用 Mage  
  
#### <a name="you-tried-to-sign-with-a-certificate-in-your-certificate-store-and-a-received-blank-message-box"></a>尝试使用你的证书存储和接收到的空消息框中的证书进行签名  
 在**签名**对话框中，你必须：  
  
-   选择**使用存储的证书进行签名**，和  
  
-   从列表; 选择一个证书第一个证书不是默认选项。  
  
#### <a name="clicking-the-dont-sign-button-causes-an-exception"></a>单击"不登录"按钮时导致异常  
 此问题是一个已知的 bug。 所有[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]清单所需进行签名。 只需选择其中一个签名的选项，并依次**确定**。  
  
## <a name="additional-errors"></a>其他错误  
 下表显示了一些常见的错误消息，用户安装时，可能会收到客户端计算机用户[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]应用程序。 最可能原因的错误说明旁边列出每个错误消息。  
  
|错误消息|描述|  
|-------------------|-----------------|  
|无法启动应用程序。 请联系应用程序发行者。<br /><br /> 无法启动应用程序。 应用程序供应商联系以获取帮助。|这些是无法启动应用，以及可找到任何其他特定原因时出现一般错误消息。 通常，该应用程序以某种方式损坏，这意味着或[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]存储已损坏。|  
|无法继续。 应用程序的格式不正确。 应用程序发布者联系以获取帮助。<br /><br /> 应用程序验证未成功。 无法继续。<br /><br /> 无法检索应用程序文件。 在部署中损坏的文件。|部署中的清单文件之一无效语法，或包含不能为与相应的文件进行对帐哈希。 此错误也可能表示在程序集中嵌入的清单已损坏。 重新创建你的部署和重新编译你的应用程序，或找到并在清单中手动修复错误。|  
|无法检索应用程序。 身份验证错误。<br /><br /> 应用程序安装未成功。 找不到服务器上的应用程序文件。 联系的应用程序发行者或管理员联系以获取帮助。|无法下载部署中的一个或多个文件，因为您没有权限来访问它们。 这可能引起所返回的 Web 服务器，如果你在部署中的文件之一结尾扩展，可将其视为受保护的文件的 Web 服务器可能会出现一个 403 禁止访问错误。 此外，包含一个或多个应用程序的文件的目录可能需要用户名和密码才能访问。|  
|无法下载应用程序。 应用程序缺少必需的文件。 与应用程序供应商或你的系统管理员联系以获取帮助。|在服务器上找不到一个或多个应用程序清单中列出的文件。 验证你已上载部署的所有依赖文件，然后重试。|  
|应用程序下载未成功。 检查网络连接，或与系统管理员或网络服务提供商。|[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]无法建立网络连接到服务器。 检查服务器的可用性和你网络的状态。|  
|URLDownloadToCacheFile 失败，HRESULT\<编号 >。 尝试下载时出错\<文件 >。|如果用户具有 Internet 资源管理器高级安全选项"如果之间安全的更改，则发出警告和非安全模式"的计算机上设置部署目标，并且安装程序正在安装 ClickOnce 应用程序的重定向 URL 从非安全到安全站点 （或反之亦然），则安装将失败，因为 Internet Explorer 警告中断它。<br /><br /> 若要解决此问题，你可以执行下列其中一项：<br /><br /> -清除安全选项。<br />-请确保不使用这种方式来更改安全模式重定向设置 URL。<br />-完全删除重定向，并指向实际设置 URL。|  
|出现错误写入到硬盘。 可能有足够的空间，可用磁盘上。 与应用程序供应商或你的系统管理员联系以获取帮助。|这可能表示没有足够的磁盘空间来存储应用程序，但当你尝试将应用程序文件保存到驱动器时，它还可指示更多常规的 I/O 错误。|  
|无法启动应用程序。 磁盘上没有足够的可用空间。|硬盘已满。 清理空间并尝试再次运行应用程序。|  
|过多的已部署的激活尝试一次加载。|[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]限制可以在同一时间开始的不同应用程序的数量。 这主要是为了帮助防止恶意发起拒绝服务攻击尝试针对本地[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]服务; 请尝试以相同的应用程序启动重复，快速进行后续、 仅最终将得到的单个实例的用户应用程序。|  
|无法通过网络激活快捷方式。|快捷方式[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]仅可以在本地硬盘上启动应用程序。 它们不能通过打开指向远程服务器上的快捷方式文件的 URL 来启动。|  
|太大而无法联机在部分信任环境中运行应用程序。 与应用程序供应商或你的系统管理员联系以获取帮助。|在部分信任环境中运行的应用程序不能大于联机应用程序配额，它们的默认值为 250 MB 的大小的一半。|  
  
## <a name="see-also"></a>另请参阅  
 [ClickOnce 安全和部署](../deployment/clickonce-security-and-deployment.md)   
 [ClickOnce 部署疑难解答](../deployment/troubleshooting-clickonce-deployments.md)