---
title: "ClickOnce 部署中的服务器和客户端配置问题 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "ClickOnce 部署, 疑难解答"
  - "部署应用程序, ClickOnce"
  - "ClickOnce 部署疑难解答"
  - "Windows 应用程序, ClickOnce 部署"
ms.assetid: 929e5fcc-dd56-409c-bb57-00bd9549b20b
caps.latest.revision: 33
caps.handback.revision: 33
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# ClickOnce 部署中的服务器和客户端配置问题
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

如果在 Windows Server 上使用 Internet Information Services \(IIS\)，并且部署中包含 Windows 不识别的文件类型（如 Microsoft Word 文件），则 IIS 将拒绝传输该文件，并且部署不会成功。  
  
 另外，某些 Web 服务器和 Web 应用程序软件（如 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]）中会包含一个您无法下载的文件和文件类型的列表。  例如，[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 阻止下载所有 Web.config 文件。  这些文件可能包含敏感信息，例如，用户名和密码。  
  
 尽管此限制应该不会对 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 核心文件（如清单和程序集）的下载造成任何问题，但它可能会阻止您下载作为 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 应用程序一部分而提供的数据文件。  在 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 中，从 IIS 配置管理器中移除禁止下载此类文件的处理程序可以解决此错误。  有关其他详细信息，请参见 IIS 服务器文档。  
  
 某些 Web 服务器可能会阻止扩展名为诸如 .dll、.config 和 .mdf 之类的文件。  基于 Windows 的应用程序通常包含带有其中一些扩展名的文件。  如果用户尝试运行一个访问 Web 服务器上被阻止文件的 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 应用程序，将产生一个错误。  默认情况下，[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 使用“.deploy”文件扩展名发布每个应用程序文件，而不是取消对所有文件扩展名的阻止。  因此，管理员只需将 Web 服务器配置为允许以下三种文件扩展名即可：  
  
-   .application  
  
-   .manifest  
  
-   .deploy  
  
 但是，可以禁用此选项，方法是清除[Publish Options Dialog Box](http://msdn.microsoft.com/zh-cn/fd9baa1b-7311-4f9e-8ffb-ae50cf110592)上的**“使用‘.deploy’文件扩展名”**选项，这时必须配置 Web 服务器以允许应用程序中使用的所有文件扩展名。  
  
 例如，如果在尚未安装 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 的情况下使用 IIS，或者在使用其他 Web 服务器（例如，Apache），则您必须配置 .manifest、.application 和 .deploy。  
  
## ClickOnce 和安全套接字层 \(SSL\)  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 应用程序将在 SSL 上正常工作，除非 Internet Explorer 显示一个有关 SSL 证书的提示。  该提示会在证书出问题时显示，例如，当站点名称不匹配或证书已过期时。  若要使 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 在 SSL 连接上工作，请确保证书是最新的，并且证书数据与网站数据匹配。  
  
## ClickOnce 和代理身份验证  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 为 .NET Framework 3.5 中启动的 Windows 集成代理身份验证提供支持。  不需要特定的 machine.config 指令。  [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 不支持基本身份验证和摘要式身份验证等其他身份验证协议。  
  
 您也可以对 .NET Framework 2.0 应用修补程序以启用此功能。  有关更多信息，请参见 http:\/\/go.microsoft.com\/fwlink\/?LinkId\=158730。  
  
 有关更多信息，请参见 [\<defaultProxy\> 元素（网络设置）](../Topic/%3CdefaultProxy%3E%20Element%20\(Network%20Settings\).md)。  
  
## ClickOnce 与 Web 浏览器兼容性  
 目前，只有使用 Internet Explorer 打开部署清单的 URL 时，才能启动 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 安装。  只有将 Internet Explorer 设置为默认的 Web 浏览器时，从其他应用程序（如 Microsoft Office Outlook）启动其 URL 的部署才能成功启动。  
  
> [!NOTE]
>  如果部署提供程序不为空，或者安装了 Microsoft .NET Framework Assistant 扩展，则支持 Mozilla Firefox。  此扩展与 .NET Framework 3.5 SP1 打包在一起。  对于 XBAP 支持，会在需要时激活 NPWPF 插件。  
  
## 通过浏览器脚本激活 ClickOnce 应用程序  
 如果您开发的自定义网页使用活动脚本来启动 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 应用程序，您可能发现该应用程序在某些计算机上将无法启动。  Internet Explorer 包含一项名为**“文件下载自动提示”**的设置，该设置会影响此行为。  此设置在其**“选项”**菜单中的**“安全”**选项卡上提供，它会影响此行为。  此设置称为**“文件下载自动提示”**，它在**“下载”**类别下列出。  对于 Intranet 网页，该属性默认设置为**“启用”**；对于 Internet 网页，该属性默认设置为**“禁用”**。  当此设置设为**“禁用”**时，将阻止任何以编程方式激活 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 应用程序的尝试（例如，通过将其 URL 赋给 `document.location` 属性）。  在此情况下，用户只能通过用户启动的下载来启动应用程序，例如通过单击设置为该应用程序的 URL 的超链接。  
  
## 其他服务器配置问题  
  
##### 所需的管理员权限  
 如果使用 HTTP 发布，您必须对目标服务器具有管理员权限。  IIS 需要此权限级别。  如果不使用 HTTP 发布，则只需具备目标路径上的写权限。  
  
##### 服务器身份验证问题  
 向关闭了“匿名访问”的远程服务器发布时，您将收到下面的警告：  
  
```  
"The files could not be downloaded from http://<remoteserver>/<myapplication>/.  The remote server returned an error: (401) Unauthorized."  
```  
  
> [!NOTE]
>  如果站点提示您提供默认凭据之外的凭据，可以让 NTLM（NT 质询\-响应）身份验证工作，然后在提示是否保存提供的凭据以供将来的会话使用时，在安全对话框中单击**“确定”**。  但是，此解决方法对于基本身份验证无效。  
  
## 使用第三方 Web 服务器  
 如果要从 IIS 以外的 Web 服务器部署 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 应用程序，而该服务器为关键 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 文件（如部署清单和应用程序清单）返回不正确的内容类型，则您可能会遇到问题。  若要解决这个问题，请参见 Web 服务器帮助文档中关于如何向服务器添加新内容类型的信息，并确保下表列出的所有文件扩展名映射都准备就绪。  
  
|文件扩展名|内容类型|  
|-----------|----------|  
|`.application`|`application/x-ms-application`|  
|`.manifest`|`application/x-ms-manifest`|  
|`.deploy`|`application/octet-stream`|  
|`.msu`|`application/octet-stream`|  
|`.msp`|`application/octet-stream`|  
  
## ClickOnce 和映射的驱动器  
 如果您使用 Visual Studio 发布 ClickOnce 应用程序，则无法将映射的驱动器指定为安装位置。  但是，您可以使用清单生成器和编辑器（Mage.exe 和 MageUI.exe）修改 ClickOnce 应用程序以从映射的驱动器中进行安装。  有关更多信息，请参见 [Mage.exe（清单生成和编辑工具）](../Topic/Mage.exe%20\(Manifest%20Generation%20and%20Editing%20Tool\).md)和 [MageUI.exe（图形化客户端中的清单生成和编辑工具）](../Topic/MageUI.exe%20\(Manifest%20Generation%20and%20Editing%20Tool,%20Graphical%20Client\).md)。  
  
## FTP 协议不支持安装应用程序  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 支持从任何 HTTP 1.1 Web 服务器或文件服务器上安装应用程序。  文件传输协议 \(FTP\) 不支持安装应用程序。  只能用 FTP 发布应用程序。  下表总结了这些差异：  
  
|URL 类型|说明|  
|------------|--------|  
|ftp:\/\/|可以使用此协议发布 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 应用程序。|  
|http:\/\/|可以使用此协议安装 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 应用程序。|  
|https:\/\/|可以使用此协议安装 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 应用程序。|  
|file:\/\/|可以使用此协议安装 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 应用程序。|  
  
## Windows XP SP2：Windows 防火墙  
 默认情况下，Windows XP SP2 启用 Windows 防火墙。  如果在安装了 Windows XP 的计算机上开发应用程序，您仍能从运行 IIS 的本地服务器发布和运行 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 应用程序。  但是，除非您打开 Windows 防火墙，否则您无法从其他计算机访问运行 IIS 的服务器。  有关管理 Windows 防火墙的说明，请参见“Windows 帮助”。  
  
## Windows Server：启用 FrontPage server Extensions  
 将应用程序发布到使用 HTTP 的 Windows Web 服务器需要 Microsoft 的 FrontPage Server Extensions。  
  
 默认情况下，Windows Server 不安装 FrontPage Server Extensions。  如果希望通过 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 发布到 Windows Server Web 服务器（后者对 FrontPage Server Extensions 使用 HTTP），则必须先安装 FrontPage Server Extensions。  您可以使用 Windows Server 中的“管理您的服务器”管理工具执行该安装。  
  
## Windows Server：锁定的内容类型  
 [!INCLUDE[WinXPSvr](../debugger/includes/winxpsvr_md.md)] 上的 IIS 会锁定除某些已知内容类型（例如 .htm、.html、.txt 等）以外的所有文件类型。  若要使用此服务器部署 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 应用程序，需要更改 IIS 设置以允许下载 .application、.manifest 以及应用程序使用的所有其他自定义文件类型的文件。  
  
 如果使用 IIS 服务器进行部署，请运行 inetmgr.exe 并为默认网页添加新的文件类型：  
  
-   对于 .application 和 .manifest 扩展名，MIME 类型应为“application\/x\-ms\-application”。对于其他文件类型，MIME 类型应为“application\/octet\-stream”。  
  
-   如果创建带有扩展名“\*”且 MIME 类型为“application\/octet\-stream”的 MIME 类型，将允许下载未阻止的文件类型的文件。  （但是不能下载阻止的文件类型，例如 .aspx 和 .asmx。）  
  
 有关在 Windows Server 上配置 MIME 类型的具体说明，请参见位于 [http:\/\/support.microsoft.com\/default.aspx?scid\=kb;zh\-cn;326965](http://support.microsoft.com/default.aspx?scid=kb;zh-cn;326965) 上的 Microsoft 知识库文章 KB326965“IIS 6.0 不能处理未知的 MIME 类型”。  
  
## 内容类型映射  
 在 HTTP 上发布时，.application 文件的内容类型（也称为 MIME 类型）应为“application\/x\-ms\-application”。如果服务器上已安装 [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)]，则会自动设置此类型。  如果没有安装，则需要为 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 应用程序 vroot（或整个服务器）创建 MIME 类型关联。  
  
 如果使用 IIS 服务器进行部署，请运行 inetmgr.exe 并为 .application 扩展名添加新内容类型“application\/x\-ms\-application”。  
  
## HTTP 压缩问题  
 通过 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]，可以执行使用 HTTP 压缩的下载，HTTP 压缩是一种 Web 服务器技术，它使用 GZIP 算法压缩数据流，然后将流发送到客户端。  客户端（在本例中为 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]）在读取文件之前先对数据流进行解压缩。  
  
 如果您使用 IIS，则可以轻松启用 HTTP 压缩。  但是，启用 HTTP 压缩时，它只是针对某些文件类型（即 HTML 和文本文件）启用。  若要对程序集 \(.dll\)、XML \(.xml\)、部署清单 \(.application\) 和应用程序清单 \(.manifest\) 启用压缩，必须首先将这些文件类型添加到 IIS 的压缩类型列表中。  在您将这些文件类型添加到部署前，将只压缩文本和 HTML 文件。  
  
 有关 IIS 的详细说明，请参见[如何为 HTTP 压缩指定其他文档类型](http://go.microsoft.com/fwlink/?LinkId=178459)。  
  
## 请参阅  
 [ClickOnce 部署疑难解答](../deployment/troubleshooting-clickonce-deployments.md)   
 [选择 ClickOnce 部署策略](../deployment/choosing-a-clickonce-deployment-strategy.md)   
 [应用程序部署必备](../deployment/application-deployment-prerequisites.md)