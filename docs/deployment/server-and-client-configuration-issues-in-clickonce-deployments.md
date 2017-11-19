---
title: "服务器和 ClickOnce 部署中的客户端配置问题 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications, ClickOnce
- troubleshooting ClickOnce deployments
- ClickOnce deployment, troubleshooting
- Windows applications, ClickOnce deployments
ms.assetid: 929e5fcc-dd56-409c-bb57-00bd9549b20b
caps.latest.revision: "33"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 4b7153b0a20c10e7dbdb31ac943f150f72cb39d8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="server-and-client-configuration-issues-in-clickonce-deployments"></a>ClickOnce 部署中的服务器和客户端配置问题
如果你在 Windows Server 上使用 Internet 信息服务 (IIS)，而你的部署包含 Windows 无法识别的文件类型，如 Microsoft Word 文件，IIS 将拒绝传输该文件中，并且你的部署将不会成功。  
  
 此外，某些 Web 服务器和 Web 应用程序软件，如[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]，包含的文件的列表，并且无法下载的文件类型。 例如，[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]可防止所有的 Web.config 文件的下载。 这些文件可能包含敏感信息，例如用户名和密码。  
  
 尽管此限制应没有引起问题下载核心[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]文件，如清单和程序集，此限制可能会阻止你下载数据文件作为的一部分包括你[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]应用程序。 在[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]，可以通过删除禁止从 IIS 配置管理器这类文件的下载的处理程序来解决此错误。 请参阅 IIS 服务器文档，了解更多详细信息。  
  
 某些 Web 服务器可能会阻止具有扩展名.dll、.config，等.mdf 文件。 基于 Windows 的应用程序通常包括具有一些具有这些扩展名的文件。 如果用户尝试运行[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]访问 Web 服务器上被阻止的文件的应用程序，将产生一个错误。 而不是取消阻止所有的文件扩展名，[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]默认情况下发布".deploy"文件扩展名的每个应用程序文件。 因此，管理员仅需要配置 Web 服务器，以取消阻止以下三个文件扩展名：  
  
-   .application  
  
-   .manifest  
  
-   .deploy  
  
 但是，你可以通过清除禁用此选项**使用".deploy"文件扩展名**选项[发布选项对话框](http://msdn.microsoft.com/en-us/fd9baa1b-7311-4f9e-8ffb-ae50cf110592)，在这种情况下，你必须配置 Web 服务器为允许所有文件扩展名在应用程序中使用。  
  
 你将需要配置.manifest、.application 和.deploy，例如，如果你使用的不具有安装的 IIS [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]，或者如果你在使用另一台 Web 服务器 (例如，Apache)。  
  
## <a name="clickonce-and-secure-sockets-layer-ssl"></a>ClickOnce 和安全套接字层 (SSL)  
 A[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]应用程序可以正常工作通过 SSL，除 Internet 资源管理器时引发有关 SSL 证书提示。 出现错误证书，如当站点名称不匹配的证书或证书已过期时，可以引发提示符。 若要使[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]工作通过 SSL 连接，请确保该证书是最新的且证书数据是否匹配的站点数据。  
  
## <a name="clickonce-and-proxy-authentication"></a>ClickOnce 和代理身份验证  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]从.NET Framework 3.5 的 Windows 集成代理身份验证提供支持。 没有特定 machine.config 指令是必需的。 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]不提供其他身份验证协议，如基本或摘要式所需的支持。  
  
 你也可以适用于.NET Framework 2.0，以启用此功能的修补程序。 有关详细信息，请参阅 http://go.microsoft.com/fwlink/?LinkId=158730。  
  
 有关详细信息，请参阅[ \<defaultProxy > 元素 （网络设置）](/dotnet/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings)。  
  
## <a name="clickonce-and-web-browser-compatibility"></a>ClickOnce 和 Web 浏览器兼容性  
 目前，[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]仅当使用 Internet Explorer 打开部署清单的 URL，将启动安装。 仅当 Internet Explorer 设置为默认 Web 浏览器，其 URL 启动从另一个应用程序，如 Microsoft Office Outlook 的部署将成功启动。  
  
> [!NOTE]
>  如果部署提供程序不为空或安装 MICROSOFT.NET Framework 助手扩展后，则支持 Mozilla Firefox。 此扩展是与.NET Framework 3.5 SP1 打包在一起。 有关 XBAP 支持，在需要时激活 NPWPF 插件。  
  
## <a name="activating-clickonce-applications-through-browser-scripting"></a>激活 ClickOnce 应用程序可以通过浏览器脚本  
 如果你已开发一个自定义网页，将启动[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]使用活动脚本应用程序可能会发现在某些计算机上将不启动应用程序。 Internet 资源管理器包含一个叫做设置**文件下载自动提示**，这将影响此行为。 此设置位于**安全**选项卡中其**选项**会影响此行为的菜单。 它称为**文件下载自动提示**，，下列出**下载**类别。 属性设置为**启用**默认情况下，intranet 网页，以及**禁用**默认情况下，对 Internet Web 页。 当此设置设置为**禁用**，任何尝试激活[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]应用程序以编程方式 (例如，通过将分配到其 URL`document.location`属性) 将被阻止。 在此情况下，用户可以启动应用程序只能通过用户启动的下载，例如，通过单击超链接设置为应用程序的 URL。  
  
## <a name="additional-server-configuration-issues"></a>其他服务器配置问题  
  
##### <a name="administrator-permissions-required"></a>所需的管理员权限  
 如果您要发布使用 HTTP，必须在目标服务器上具有管理员权限。 IIS 需要此权限级别。 如果你没有将发布使用 HTTP，则只需要写入权限的目标路径。  
  
##### <a name="server-authentication-issues"></a>服务器身份验证问题  
 当你将发布到已关闭"匿名访问"的远程服务器时，你将收到以下警告：  
  
```  
"The files could not be downloaded from http://<remoteserver>/<myapplication>/.  The remote server returned an error: (401) Unauthorized."  
```  
  
> [!NOTE]
>  你可以让 NTLM （NT 质询-响应） 身份验证工作如果站点提示您提供默认凭据，不同的凭据，然后在安全对话框中，单击**确定**在提示你时如果你想要保存提供进行将来会话的凭据。 但是，此解决方法对于基本身份验证无效。  
  
## <a name="using-third-party-web-servers"></a>使用第三方 Web 服务器  
 如果你要部署[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]从非 IIS Web 服务器的应用程序，你可能会遇到问题如果服务器返回密钥不正确的内容类型[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]文件，如部署清单和应用程序清单。 若要解决此问题，请参阅有关如何将新内容类型添加到服务器，并确保所有的文件名称扩展映射列下表中的文档位于的位置的 Web 服务器的帮助。  
  
|文件扩展名|内容类型|  
|-------------------------|------------------|  
|`.application`|`application/x-ms-application`|  
|`.manifest`|`application/x-ms-manifest`|  
|`.deploy`|`application/octet-stream`|  
|`.msu`|`application/octet-stream`|  
|`.msp`|`application/octet-stream`|  
  
## <a name="clickonce-and-mapped-drives"></a>ClickOnce 和映射的驱动器  
 如果使用 Visual Studio 发布 ClickOnce 应用程序，你不能作为安装位置指定映射的驱动器。 但是，你可以修改 ClickOnce 应用程序使用的清单生成器和编辑器 （Mage.exe 和 MageUI.exe） 从映射的驱动器安装。 有关详细信息，请参阅[Mage.exe （清单生成和编辑工具）](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)和[MageUI.exe （清单生成和编辑工具，图形化客户端）](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)。  
  
## <a name="ftp-protocol-not-supported-for-installing-applications"></a>FTP 协议不支持用于安装应用程序  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]从任何 HTTP 1.1 Web 服务器或文件服务器中安装应用程序的支持。 FTP 文件传输协议不支持用于安装应用程序。 你可以使用 FTP 发布仅限于应用程序。 下表总结了这些差异：  
  
|URL 类型|描述|  
|--------------|-----------------|  
|ftp: / /|你可以将发布[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]应用程序使用此协议。|  
|http://|你可以安装[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]应用程序使用此协议。|  
|https://|你可以安装[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]应用程序使用此协议。|  
|file://|你可以安装[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]应用程序使用此协议。|  
  
## <a name="windows-xp-sp2-windows-firewall"></a>Windows XP SP2: Windows 防火墙  
 默认情况下，Windows XP SP2 启用 Windows 防火墙。 如果你正在开发你的应用程序已安装的 Windows XP 的计算机上，你将仍然能够发布和运行[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]从本地服务器正在运行 IIS 的应用程序。 但是，你无法访问该运行时，IIS 从另一台计算机除非打开 Windows 防火墙的服务器。 有关管理 Windows 防火墙的说明，请参阅 Windows 帮助。  
  
## <a name="windows-server-enable-frontpage-server-extensions"></a>Windows Server： 启用 FrontPage 服务器扩展  
 从 Microsoft 的 FrontPage 服务器扩展是必需的应用程序发布到使用 HTTP 的 Windows Web 服务器。  
  
 默认情况下，Windows 服务器不具有安装的 FrontPage 服务器扩展。 如果你想要使用[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]要发布到 HTTP 使用 FrontPage 服务器扩展的 Windows Server Web 服务器，必须先安装 FrontPage 服务器扩展。 可以通过使用 Windows Server 中管理您的服务器管理工具来执行安装。  
  
## <a name="windows-server-locked-down-content-types"></a>Windows Server： 锁定的内容类型  
 上的 IIS[!INCLUDE[WinXPSvr](../debugger/includes/winxpsvr_md.md)]锁定了除某些已知的内容类型 （例如，.htm、.html、.txt，等） 之外的所有文件类型。 若要启用的部署[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]使用此服务器应用程序，你需要更改 IIS 设置，以允许下载类型.application、.manifest 和使用你的应用程序的任何其他自定义文件类型的文件。  
  
 如果你部署使用 IIS 服务器，运行 inetmgr.exe 并添加新的默认 Web 页的文件类型：  
  
-   有关.application 和.manifest 扩展，该 MIME 类型应为"应用程序/x 的 ms-应用程序。" 对于其他文件类型，MIME 类型应为"应用程序/八进制数流。"  
  
-   如果你创建带扩展名的 MIME 类型"*"和"应用程序/八进制数流"的 MIME 类型，它将允许取消阻止的文件类型，要下载的文件。 （但是，阻止不能下载类型如.aspx 和.asmx 文件。）  
  
 有关 Windows Server 上配置 MIME 类型的特定说明，请参阅 Microsoft 知识库文章 KB326965，"IIS 6.0 不提供未知 MIME 类型"在[http://support.microsoft.com/default.aspx?scid=kb;en-us;326965](http://support.microsoft.com/default.aspx?scid=kb;en-us;326965).  
  
## <a name="content-type-mappings"></a>内容类型映射  
 .Application 文件的内容类型 （也称为 MIME 类型） 在通过 HTTP 发布时，应为"应用程序/x 的 ms-应用程序。" 如果你有[!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)]服务器上安装，这将设置为你自动。 如果未安装，则你需要创建的 MIME 类型关联[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]应用程序虚拟根目录 （或整个服务器）。  
  
 如果你部署使用 IIS 服务器，运行 inetmgr.exe 并添加新的内容类型的"应用程序/x 的 ms-应用程序"的.application 扩展名。  
  
## <a name="http-compression-issues"></a>HTTP 压缩问题  
 与[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]，你可以执行使用 HTTP 压缩的下载，使用 GZIP 算法以在将流发送到客户端前压缩数据流的 Web 服务器技术。 客户端-在这种情况下， [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]-解压缩流读取的文件之前。  
  
 如果你正在使用 IIS，你可以轻松地启用 HTTP 压缩。 但是，当你启用 HTTP 压缩，它会仅启用对某些文件类型 — 也就是说，HTML 和文本的文件。 若要启用程序集 (.dll) 的压缩，XML (.xml)、 部署清单 (.application) 和应用程序清单 (.manifest)，你必须将添加这些文件类型到 IIS 压缩的类型的列表。 将文件类型添加到你的部署中时之前, 仅文本和 HTML 文件都将被压缩。  
  
 有关 IIS 的详细说明，请参阅[如何指定 HTTP 压缩的附加文档类型](http://go.microsoft.com/fwlink/?LinkId=178459)。  
  
## <a name="see-also"></a>另请参阅  
 [ClickOnce 部署疑难解答](../deployment/troubleshooting-clickonce-deployments.md)   
 [选择 ClickOnce 部署策略](../deployment/choosing-a-clickonce-deployment-strategy.md)   
 [应用程序部署必备](../deployment/application-deployment-prerequisites.md)