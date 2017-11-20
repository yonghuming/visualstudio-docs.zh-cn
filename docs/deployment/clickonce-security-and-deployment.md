---
title: "ClickOnce 安全和部署 |Microsoft 文档"
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
- Windows applications, ClickOnce deployment
- deploying applications [ClickOnce]
- ClickOnce deployment
- publishing, ClickOnce
ms.assetid: abab6d34-c3c2-45c1-a8b6-43c7d3131e7a
caps.latest.revision: "32"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 7e56d596c37960ddfa548921da897f08fbfbbf5b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="clickonce-security-and-deployment"></a>ClickOnce 安全和部署
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]是一种部署技术，可用于创建自我更新的基于 Windows 的应用程序可以安装和运行最少的用户交互。 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]用于发布和更新如果您已开发您的项目与 Visual Basic 和 Visual C# 使用 ClickOnce 技术部署的应用程序提供完全支持。 有关部署 Visual c + + 应用程序的信息，请参阅[Visual c + + 应用程序的 ClickOnce 部署](/cpp/ide/clickonce-deployment-for-visual-cpp-applications)。  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]部署没有与此部署中的三个主要问题：  
  
-   **在更新应用程序的问题。** 使用 Microsoft Windows Installer 部署后，每当更新应用程序时，用户可以安装更新，msp 文件，并将其应用到已安装的产品中。与[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]部署，你可以提供更新自动。 仅这些应用程序已更改部分不下载，和从新的并排显示文件夹然后重新安装完整的更新应用程序。  
  
-   **对用户的计算机的影响。** 使用 Windows Installer 部署时，应用程序通常依赖于共享组件，可能会发生冲突;与[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]部署中，每个应用程序是自包含，不会影响的其他应用程序。  
  
-   **安全权限。** Windows Installer 部署需要管理权限，并且允许只有有限的用户安装;[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]部署，非管理用户可以安装，并仅授予这些代码访问安全性权限的应用程序需要。  
  
 在过去，这些问题有时会导致开发人员可以决定创建而不是基于 Windows 的应用程序，会牺牲丰富的用户界面，以便于安装的 Web 应用程序。 通过使用应用程序使用部署[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]，你可以两种技术的最佳。  
  
## <a name="what-is-a-clickonce-application"></a>ClickOnce 应用程序是什么？  
 A[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]应用程序是任何 Windows Presentation Foundation (.xbap)、 Windows 窗体 (.exe)、 控制台应用程序 (.exe)，还是使用发布 Office 解决方案 (.dll)[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]技术。 你可以将发布[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]三个不同的方式应用程序： 在网页上，从网络文件共享，或如 CD-ROM 的媒体。 A[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]可以某个最终用户的计算机上安装应用程序，并将其本地运行，即使计算机处于脱机状态，或者它可以在仅联机模式下运行，而无需永久最终用户计算机上安装任何内容。 有关详细信息，请参阅[选择 ClickOnce 部署策略](../deployment/choosing-a-clickonce-deployment-strategy.md)。  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]应用程序可以自我更新;它们可以检查较新版本，因为它们变得可用，并自动将任何更新的文件。 开发人员可以指定更新行为;网络管理员还可以控制更新策略，例如，将标记为必需的更新。 更新可以还将其回滚到早期版本的最终用户或管理员。 有关详细信息，请参阅[选择 ClickOnce 更新策略](../deployment/choosing-a-clickonce-update-strategy.md)。  
  
 因为[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]应用程序是独立安装或运行[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]应用程序无法破坏现有应用程序。 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]应用程序是自包含;每个[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]安装到应用程序并将其从安全每个用户，每个应用程序缓存运行。 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]在 Internet 或 Intranet 安全区域中运行应用程序。 如有必要，应用程序可以请求提升的安全权限。 有关详细信息，请参阅[保护 ClickOnce 应用程序](../deployment/securing-clickonce-applications.md)。  
  
## <a name="how-clickonce-security-works"></a>ClickOnce 安全性工作原理  
 核心[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]安全性取决于证书、 代码访问安全策略和 ClickOnce 信任提示。  
  
### <a name="certificates"></a>证书  
 使用验证码证书来验证应用程序的发布服务器的真实性。 通过为应用程序部署中使用验证码，ClickOnce 可帮助防止有害程序描绘本身作为合法程序来自建立，可信的源。 （可选） 还可以使用证书进行签名的应用程序和部署清单以证明文件未被篡改。 有关详细信息，请参阅[ClickOnce 和 Authenticode](../deployment/clickonce-and-authenticode.md)。 此外可以使用证书配置客户端计算机具有受信任的发布服务器的列表。 如果应用程序来自受信任的发布者，则可以安装无需任何用户交互。 有关详细信息，请参阅 [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md)。  
  
### <a name="code-access-security"></a>代码访问安全性  
 代码访问安全性帮助限制代码对受保护资源的访问权限。 在大多数情况下，你可以选择 Internet 或本地 Intranet 区域来限制权限。 使用**安全**页面**ProjectDesigner**以请求适用于应用程序的区域。 你还可以调试具有受限的权限来模拟最终用户体验的应用程序。 有关详细信息，请参阅[ClickOnce 应用程序的代码访问安全性](../deployment/code-access-security-for-clickonce-applications.md)。  
  
### <a name="clickonce-trust-prompt"></a>ClickOnce 信任提示  
 如果应用程序请求更多的权限超出区域的允许，可以提示最终用户做出信任决定。 最终用户可以决定是否信任，可以运行 ClickOnce 应用程序，如 Windows 窗体应用程序、 Windows Presentation Foundation 应用程序、 控制台应用程序、 XAML 浏览器应用程序，和 Office 解决方案。 有关详细信息，请参阅[如何： 配置 ClickOnce 信任提示行为](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md)。  
  
## <a name="how-clickonce-deployment-works"></a>ClickOnce 部署的工作原理  
 核心[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]部署体系结构基于两个 XML 清单文件： 一个应用程序清单和部署清单。 文件用于描述从何处安装 ClickOnce 应用程序、 更新的方式和更新时。  
  
### <a name="publishing-clickonce-applications"></a>发布 ClickOnce 应用程序  
 该应用程序清单将描述应用程序本身。 这包括程序集、 依赖关系和构成应用程序、 所需的权限，以及更新将在其中可用的位置的文件。 应用程序开发人员通过使用 Visual Studio 或清单生成和编辑工具 (Mage.exe) 中的发布向导中创建应用程序清单[!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)]。 有关详细信息，请参阅[如何： 发布 ClickOnce 应用程序使用发布向导](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)。  
  
 该部署清单将描述如何部署应用程序。 这包括应用程序清单的位置和客户端应运行的应用程序的版本。  
  
### <a name="deploying-clickonce-applications"></a>部署 ClickOnce 应用程序  
 它创建后，部署清单复制到部署位置。 这可以是 Web 服务器、 网络文件共享或媒体如 CD。 应用程序清单和应用程序的所有文件也将复制到部署清单中指定的部署位置。 这可以是相同的部署位置，也可以是不同的位置。 使用时**发布向导**在 Visual Studio 中，复制操作，将自动执行。  
  
### <a name="installing-clickonce-applications"></a>安装 ClickOnce 应用程序  
 部署到的部署位置后，最终用户可以下载并安装应用程序，通过单击表示部署清单文件在网页上或文件夹中的图标。 在大多数情况下，最终用户提供一个简单的对话框，要求用户确认安装，安装会继续执行，并启动应用程序无需其他干预之后。 在其中应用程序需要提升的权限，或者如果应用程序不受信任的证书进行签名的情况下，该对话框还要求用户授予权限，然后才能继续安装。 尽管 ClickOnce 安装都是每个用户，如果有一些需要管理员权限的先决条件可能需要权限提升。 有关提升的权限的详细信息，请参阅[保护 ClickOnce 应用程序](../deployment/securing-clickonce-applications.md)。  
  
 证书可以是受信任在计算机或企业级别，以便使用受信任的证书签名的 ClickOnce 应用程序可以以无提示方式安装。 有关受信任的证书的详细信息，请参阅[受信任的应用程序部署概述](../deployment/trusted-application-deployment-overview.md)。  
  
 应用程序可以添加到用户的**启动**菜单和**添加或删除程序**组中**控制面板**。 其他与部署技术不同，则不添加到**Program Files**文件夹或注册表中，并且没有管理权限所需的安装  
  
> [!NOTE]
>  还有可能阻止应用程序添加到**启动**菜单和**添加或删除程序**组中，实际上使其行为类似于 Web 应用程序。 有关详细信息，请参阅[选择 ClickOnce 部署策略](../deployment/choosing-a-clickonce-deployment-strategy.md)。  
  
### <a name="updating-clickonce-applications"></a>更新 ClickOnce 应用程序  
 当应用程序开发人员创建的应用程序的更新的版本时，它们生成一个新的应用程序清单，并将文件复制到部署位置-通常是原始的应用程序部署文件夹的同级文件夹。 管理员会更新部署清单来指向新版本的应用程序的位置。  
  
> [!NOTE]
>  **发布向导**在 Visual Studio 中可用来执行这些步骤。  
  
 除了部署位置中，部署清单还包含应用程序检查更新版本的其中一个更新位置 （网页或网络文件共享）。 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]**发布**属性用于指定应用程序时间和频率应检查更新。 更新行为可以指定在部署清单中，或者它可以为通过应用程序的用户界面中的用户选项提供[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]Api。 此外，**发布**属性还可以应用以强制进行更新或回滚到早期版本。 有关详细信息，请参阅[选择 ClickOnce 更新策略](../deployment/choosing-a-clickonce-update-strategy.md)。  
  
### <a name="third-party-installers"></a>第三方安装程序  
 你可以自定义 ClickOnce 安装程序，以安装第三方组件以及你的应用程序。 你必须具有可再发行组件包 （.exe 或.msi 文件），并描述一个非特定于语言的产品清单和特定于语言的包清单的包。 有关详细信息，请参阅[创建引导程序包](../deployment/creating-bootstrapper-packages.md)。  
  
## <a name="clickonce-tools"></a>ClickOnce 工具  
 下表显示的工具可用于生成、 编辑、 签署和对应用程序和部署清单进行重新签名。  
  
|工具|描述|  
|----------|-----------------|  
|[“项目设计器”->“安全”页](../ide/reference/security-page-project-designer.md)|迹象应用程序和部署清单。|  
|[“项目设计器”->“发布”页](../ide/reference/publish-page-project-designer.md)|生成和编辑 Visual Basic 和 Visual C# 应用程序的应用程序和部署清单。|  
|[Mage.exe（清单生成和编辑工具）](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)|生成 Visual Basic、 Visual C# 和 Visual c + + 应用程序的应用程序和部署清单。<br /><br /> 签名和重新签名的应用程序和部署清单。<br /><br /> 可以从批处理脚本和命令提示符下运行。|  
|[MageUI.exe（图形化客户端中的清单生成和编辑工具）](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)|生成和编辑应用程序和部署清单。<br /><br /> 签名和重新签名的应用程序和部署清单。|  
|[GenerateApplicationManifest 任务](../msbuild/generateapplicationmanifest-task.md)|生成应用程序清单。<br /><br /> 可以从 MSBuild 运行。 有关详细信息，请参阅[MSBuild 参考](../msbuild/msbuild-reference.md)。|  
|[GenerateDeploymentManifest 任务](../msbuild/generatedeploymentmanifest-task.md)|生成部署清单。<br /><br /> 可以从 MSBuild 运行。 有关详细信息，请参阅[MSBuild 参考](../msbuild/msbuild-reference.md)。|  
|[SignFile 任务](../msbuild/signfile-task.md)|迹象应用程序和部署清单。<br /><br /> 可以从 MSBuild 运行。 有关详细信息，请参阅[MSBuild 参考](../msbuild/msbuild-reference.md)。|  
|<xref:Microsoft.Build.Tasks.Deployment.ManifestUtilities>|开发你自己的应用程序来生成应用程序和部署清单。|  
  
 下表显示支持在这些浏览器中的 ClickOnce 应用程序所需的.NET Framework 版本。  
  
|浏览者|.NET Framework 版本|  
|-------------|----------------------------|  
|Internet Explorer|2.0、 3.0、 3.5、 3.5 SP1、 4|  
|Firefox|2.0 SP1、 3.5 SP1、 4|  
  
## <a name="see-also"></a>另请参阅  
 [在 Windows Vista 上的 ClickOnce 部署](../deployment/clickonce-deployment-on-windows-vista.md)   
 [发布 ClickOnce 应用程序](../deployment/publishing-clickonce-applications.md)   
 [保护 ClickOnce 应用程序](../deployment/securing-clickonce-applications.md)   
 [使用 ClickOnce 部署 COM 组件](../deployment/deploying-com-components-with-clickonce.md)   
 [从命令行生成 ClickOnce 应用程序](../deployment/building-clickonce-applications-from-the-command-line.md)   
 [调试使用 System.Deployment.Application 的 ClickOnce 应用程序](../deployment/debugging-clickonce-applications-that-use-system-deployment-application.md)