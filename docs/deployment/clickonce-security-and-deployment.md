---
title: "ClickOnce 安全和部署 | Microsoft Docs"
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
  - "ClickOnce 部署"
  - "部署应用程序 [ClickOnce]"
  - "发布, ClickOnce"
  - "Windows 应用程序, ClickOnce 部署"
ms.assetid: abab6d34-c3c2-45c1-a8b6-43c7d3131e7a
caps.latest.revision: 32
caps.handback.revision: 32
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# ClickOnce 安全和部署
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 是一项部署技术，您可以利用这项技术来创建基于 Windows 的自行更新的应用程序，并且安装和运行这类应用程序所需的用户交互最少。如果您已使用 Visual Basic 和 Visual C\# 部署您的项目，则 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 完全支持发布和更新使用 ClickOnce 技术部署的应用程序。  有关部署 Visual C\+\+ 应用程序的信息，请参见 [Visual C\+\+ 应用程序的 ClickOnce 部署](/visual-cpp/ide/clickonce-deployment-for-visual-cpp-applications)。  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署解决了部署中的三个主要问题：  
  
-   **更新应用程序困难。**使用 Microsoft Windows Installer 部署，每次更新应用程序时，用户都可以安装更新（msp 文件）并将其应用到已安装的产品中；使用 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署，可自动提供更新。  只有更改过的应用程序部分才会被下载，然后会从新的并行文件夹重新安装完整的、更新后的应用程序。  
  
-   **对用户的计算机的影响。**使用 Windows Installer 部署时，应用程序通常依赖于共享组件，这便有可能发生版本冲突；而使用 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署时，每个应用程序都是独立的，不会干扰其他应用程序。  
  
-   **安全权限。**Windows Installer 部署要求管理员权限并且只允许受限制的用户安装；而 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署允许非管理用户安装应用程序并仅授予应用程序所需要的那些代码访问安全性权限。  
  
 过去，这些问题有时会导致开发人员决定创建 Web 应用程序而不是基于 Windows 的应用程序，从而牺牲丰富的用户界面来换取安装的便利。  通过使用利用 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署的应用程序，您可以集这两种技术的优势于一身。  
  
## 什么是 ClickOnce 应用程序？  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 应用程序是使用 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 技术发布的任何 Windows Presentation Foundation \(.xbap\)、Windows 窗体 \(.exe\)、控制台应用程序 \(.exe\) 或 Office 解决方案 \(.dll\)。  可以采用三种不同的方式发布 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 应用程序：从网页发布、从网络文件共享发布或者从媒体（如 CD\-ROM）发布。  [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 应用程序可以安装在最终用户的计算机上并在本地运行（即使该计算机处于脱机状态），或者也可以在仅限联机模式下运行，而不用在最终用户的计算机上永久性安装任何内容。  有关更多信息，请参见[选择 ClickOnce 部署策略](../deployment/choosing-a-clickonce-deployment-strategy.md)。  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 应用程序可以自行更新；这些应用程序可以在较新版本可用时检查是否存在较新版本，并自动替换所有更新后的文件。  开发人员可以指定更新行为；网络管理员也可以控制更新策略，如将更新标记为强制性的。  最终用户或管理员还可以对更新进行回滚，使应用程序恢复到早期的版本。  有关更多信息，请参见[选择 ClickOnce 更新策略](../deployment/choosing-a-clickonce-update-strategy.md)。  
  
 因为 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 应用程序是独立的，所以安装或运行 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 应用程序不会破坏现有的应用程序。  [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 应用程序是自包含的；每个 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 应用程序都会安装到一个安全的、基于每个用户和每个应用程序的缓存中，并从中运行。  [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 应用程序在 Internet 或 Intranet 安全区域中运行。  如果有必要，应用程序可以请求提升的安全权限。  有关更多信息，请参见 [保护 ClickOnce 应用程序](../deployment/securing-clickonce-applications.md)。  
  
## ClickOnce 安全的工作方式  
 核心 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 安全基于证书、代码访问安全性策略和 ClickOnce 信任提示。  
  
### 证书  
 Authenticode 证书用于验证应用程序发布者的真实性。  通过将 Authenticode 用于应用程序部署，ClickOnce 可帮助防止有害程序将自己伪装成来自已确定的可信任源的合法程序。  （可选）证书也可以用于为应用程序和部署清单签名，以证明文件未被篡改。  有关更多信息，请参见 [ClickOnce 和 Authenticode](../deployment/clickonce-and-authenticode.md)。  证书还可以用于为客户端计算机配置一个受信任的发布者的列表。  如果某个应用程序来自受信任的发布者，则可以在无需任何用户交互的情况下安装该应用程序。  有关更多信息，请参见[受信任的应用程序部署概述](../deployment/trusted-application-deployment-overview.md)。  
  
### 代码访问安全性  
 代码访问安全性可帮助限制代码对受保护资源的访问。  大多数情况下，您可以选择 Internet 区域和本地 Intranet 区域来限制权限。  使用**“项目设计器”**中的**“安全性”**页可以请求适合于应用程序的区域。  您也可以使用受限权限调试应用程序来模拟最终用户的体验。  有关更多信息，请参见 [ClickOnce 应用程序的代码访问安全性](../deployment/code-access-security-for-clickonce-applications.md)。  
  
### ClickOnce 信任提示  
 如果应用程序请求的权限超出区域的允许范围，则会提示最终用户做出信任决定。  最终用户可以决定是否信任 ClickOnce 应用程序（如 Windows Forms 应用程序、Windows Presentation Foundation 应用程序、控制台应用程序、XAML 浏览器应用程序和 Office 解决方案）以允许其运行。  有关更多信息，请参见[如何：配置 ClickOnce 信任提示行为](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md)。  
  
## ClickOnce 部署的工作方式  
 核心 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署体系结构基于两个 XML 清单文件：一个应用程序清单和一个部署清单。  这两个文件用于描述安装 ClickOnce 应用程序的源、这些应用程序的更新方式和更新时间。  
  
### 发布 ClickOnce 应用程序  
 应用程序清单描述应用程序本身。  这包括程序集、组成应用程序的依赖项和文件、所需的权限以及提供更新的位置。  应用程序开发人员使用 Visual Studio 中的“发布向导”或 [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)] 中的清单生成和编辑工具 \(Mage.exe\) 来创作应用程序清单。  有关更多信息，请参见[如何：使用发布向导发布 ClickOnce 应用程序](../Topic/How%20to:%20Publish%20a%20ClickOnce%20Application%20using%20the%20Publish%20Wizard.md)。  
  
 部署清单描述应用程序的部署方式。  其中包括应用程序清单的位置和客户端应运行的应用程序的版本。  
  
### 部署 ClickOnce 应用程序  
 部署清单在创建后会被复制到部署位置。  部署位置可以是 Web 服务器、网络文件共享或媒体（如 CD）。  应用程序清单和所有应用程序文件也都被复制到部署清单中指定的一个部署位置。  此位置可以与部署清单的部署位置相同，也可以不同。  使用 Visual Studio 中的**“发布向导”**时，将自动执行复制操作。  
  
### 安装 ClickOnce 应用程序  
 当部署清单被部署到部署位置后，最终用户可以在网页上或文件夹中单击表示部署清单文件的图标，从而下载和安装应用程序。  大多数情况下，会向最终用户提供一个简单的对话框，让用户确认安装，此后不需要进一步的用户干预，安装会继续执行且应用程序会被启动。  在应用程序要求提升的权限或应用程序未经可信证书签名的情况下，该对话框还会要求用户在安装继续进行之前授予相应权限。  尽管 ClickOnce 安装是基于用户的，但是，如果存在需要管理员特权的系统必备组件，则可能要求提升权限。  有关提升的权限的更多信息，请参见[保护 ClickOnce 应用程序](../deployment/securing-clickonce-applications.md)。  
  
 可以在计算机或企业级别信任证书，以便能够在无提示的情况下安装经可信证书签名的 ClickOnce 应用程序。  有关可信证书的更多信息，请参见[受信任的应用程序部署概述](../deployment/trusted-application-deployment-overview.md)。  
  
 可以将应用程序添加到用户的**“开始”**菜单和**“控制面板”**中的**“添加\/删除程序”**组中。  与其他部署技术不同，此部署技术不会向**“Program Files”**文件夹或注册表添加任何内容，且安装无需任何管理员权限。  
  
> [!NOTE]
>  也可以阻止将应用程序添加到**“开始”**菜单和**“添加\/删除程序”**组中，实际上是使应用程序的行为与 Web 应用程序类似。  有关更多信息，请参见[选择 ClickOnce 部署策略](../deployment/choosing-a-clickonce-deployment-strategy.md)。  
  
### 更新 ClickOnce 应用程序  
 当应用程序开发人员创建更新版本的应用程序时，开发人员会生成新的应用程序清单，并将文件复制到一个部署位置（通常是原始应用程序部署文件夹的同级文件夹）。  管理员会更新部署清单，使之指向新版本的应用程序所在的位置。  
  
> [!NOTE]
>  可以使用 Visual Studio 中的**“发布向导”**执行这些步骤。  
  
 除了部署位置外，部署清单还包含一个应用程序在其中检查有无已更新版本的更新位置（网页或网络文件共享）。  [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 的**“发布”**属性可用来指定应用程序应检查是否存在更新的时间与频率。  更新行为可以在部署清单中指定，也可以通过 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] API 在应用程序的用户界面中以用户选项的形式提供。  此外，**“发布”**属性还可以用于将更新设置为强制性的，或是用于将应用程序回滚到较早版本。  有关更多信息，请参见[选择 ClickOnce 更新策略](../deployment/choosing-a-clickonce-update-strategy.md)。  
  
### 第三方安装程序  
 可以自定义 ClickOnce 安装程序，以将第三方组件随您的应用程序一起安装。  您必须具备可再发行组件包（.exe 或 .msi 文件），并使用一个非特定语言产品清单和一个特定语言程序包清单描述该组件包。  有关更多信息，请参见[创建引导程序包](../deployment/creating-bootstrapper-packages.md)。  
  
## ClickOnce 工具  
 下表显示可用于生成、编辑、签名和重新签名应用程序清单和部署清单的工具。  
  
|工具|说明|  
|--------|--------|  
|[”项目设计器“ \-\>“安全”页](../ide/reference/security-page-project-designer.md)|对应用程序清单和部署清单进行签名。|  
|[“项目设计器”\-\>“发布”页](../ide/reference/publish-page-project-designer.md)|生成并编辑 Visual Basic 和 Visual C\# 应用程序的应用程序清单和部署清单。|  
|[Mage.exe（清单生成和编辑工具）](../Topic/Mage.exe%20\(Manifest%20Generation%20and%20Editing%20Tool\).md)|生成 Visual Basic、Visual C\# 和 Visual C\+\+ 应用程序的应用程序清单和部署清单。<br /><br /> 对应用程序清单和部署清单进行签名和重新签名。<br /><br /> 可从批处理脚本和命令提示符处运行。|  
|[MageUI.exe（图形化客户端中的清单生成和编辑工具）](../Topic/MageUI.exe%20\(Manifest%20Generation%20and%20Editing%20Tool,%20Graphical%20Client\).md)|生成并编辑应用程序清单和部署清单。<br /><br /> 对应用程序清单和部署清单进行签名和重新签名。|  
|[GenerateApplicationManifest 任务](../msbuild/generateapplicationmanifest-task.md)|生成应用程序清单。<br /><br /> 可从 MSBuild 中运行。  有关更多信息，请参见 [MSBuild 参考](../msbuild/msbuild-reference.md)。|  
|[GenerateDeploymentManifest 任务](../msbuild/generatedeploymentmanifest-task.md)|生成部署清单。<br /><br /> 可从 MSBuild 中运行。  有关更多信息，请参见 [MSBuild 参考](../msbuild/msbuild-reference.md)。|  
|[SignFile 任务](../msbuild/signfile-task.md)|对应用程序清单和部署清单进行签名。<br /><br /> 可从 MSBuild 中运行。  有关更多信息，请参见 [MSBuild 参考](../msbuild/msbuild-reference.md)。|  
|<xref:Microsoft.Build.Tasks.Deployment.ManifestUtilities>|开发您自己的应用程序以生成应用程序清单和部署清单。|  
  
 下表显示在各浏览器中支持 ClickOnce 应用程序所必需的 .NET Framework 版本。  
  
|浏览器|.NET Framework 版本|  
|---------|-----------------------|  
|Internet Explorer|2.0、3.0、3.5、3.5 SP1、4|  
|Firefox|2.0 SP1、3.5 SP1、4|  
  
## 请参阅  
 [Windows Vista 上的 ClickOnce 部署](../deployment/clickonce-deployment-on-windows-vista.md)   
 [发布 ClickOnce 应用程序](../deployment/publishing-clickonce-applications.md)   
 [保护 ClickOnce 应用程序](../deployment/securing-clickonce-applications.md)   
 [使用 ClickOnce 部署 COM 组件](../deployment/deploying-com-components-with-clickonce.md)   
 [从命令行生成 ClickOnce 应用程序](../deployment/building-clickonce-applications-from-the-command-line.md)   
 [调试使用 System.Deployment.Application 的 ClickOnce 应用程序](../deployment/debugging-clickonce-applications-that-use-system-deployment-application.md)