---
title: "应用程序部署必备 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, platform detection
- ClickOnce deployment, prerequisites
- ClickOnce deployment, dependencies
- prerequisites, ClickOnce
- dependencies, ClickOnce
ms.assetid: fc6e047e-ad94-44e8-8ff5-b6d1f4ca7735
caps.latest.revision: "51"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: c323e3800e98e2451a371f3ff84b3351d760a94c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="application-deployment-prerequisites"></a>应用程序部署必备
为确保应用程序成功安装和运行，必须先确保应用程序依赖的所有组件都已安装在目标计算机上。 例如，用 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)][!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 创建的大多数应用程序都会依赖 ；在安装应用程序前，目标计算机上必须存在正确版本的公共语言运行时。  
  
 你可以选择在这些系统必备组件**系统必备组件对话框**并作为安装的一部分安装.NET Framework 和其他可再发行文件。 此做法称为*引导*。 接下来，[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]生成名为 Setup.exe，也称为的 Windows 可执行程序*引导程序*。 引导程序负责在运行应用程序之前，安装这些系统必备组件。 有关选择这些系统必备组件的详细信息，请参阅[系统必备组件对话框](../ide/reference/prerequisites-dialog-box.md)。  
  
 每个系统必备组件都是一个引导程序包。 一个引导程序包是一组目录和文件，其中包含用于说明系统必备组件的安装方式的清单文件。 如果应用程序系统必备组件未列在**系统必备组件对话框**，你可以创建自定义引导程序包并将其添加到 Visual Studio。 然后你可以选择在系统必备组件**系统必备组件对话框**。 有关详细信息，请参阅[创建引导程序包](../deployment/creating-bootstrapper-packages.md)。  
  
 默认情况下，ClickOnce 部署可以使用引导。 对为 ClickOnce 部署生成的引导程序进行签名。 你可以对某个组件禁用引导，但仅当确信所有目标计算机上都已安装该组件的正确版本时，才应这么做。  
  
## <a name="bootstrapping-and-clickonce-deployment"></a>引导和 ClickOnce 部署  
 在客户端计算机上安装应用程序之前，[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 会对客户端进行检查，以确保客户端具备应用程序清单中指定的要求。 这些要求包括：  
  
-   公共语言运行时的最低要求版本（在应用程序清单中被指定为一个程序集依赖项）。  
  
-   应用程序要求的 Windows 操作系统的最低要求版本（在应用程序清单中使用 `<osVersionInfo>` 元素指定）。 (请参阅[\<依赖项 > 元素](../deployment/dependency-element-clickonce-application.md))  
  
-   必须预先安装在全局程序集缓存 (GAC) 中的任何程序集及所有程序集的最低版本（由程序集清单中的程序集依赖项声明指定）。  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]能够检测到缺少的先决条件，并可以使用引导程序来安装系统必备组件。 有关详细信息，请参阅[如何： 与 ClickOnce 应用程序的安装必备组件](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)。  
  
> [!NOTE]
>  若要更改由 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 和 MageUI.exe 之类的工具生成的清单中的默认值，你需要在文本编辑器中编辑应用程序清单，然后重新对应用程序和部署清单进行签名。 有关详细信息，请参阅[如何： 重新签名的应用程序和部署清单](../deployment/how-to-re-sign-application-and-deployment-manifests.md)。  
  
 如果你使用 Visual Studio 和 ClickOnce 来部署应用程序，则默认选中的引导程序包取决于解决方案中的 .NET Framework 版本。 但是，如果你更改目标.NET Framework 版本，则必须更新中的选项**系统必备组件对话框**手动。  
  
|目标 .NET Framework|选中的引导程序包|  
|---------------------------|------------------------------------|  
|.NET Framework 4 Client Profile|.NET Framework 4 Client Profile<br /><br /> Windows Installer 3.1|  
|.NET Framework 4|.NET Framework 4<br /><br /> Windows Installer 3.1|  
  
 通过 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)][!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署， 发布向导所生成的 Publish.htm 页指向仅安装应用程序的链接，或指向同时安装应用程序和引导组件的链接。  
  
 如果你是使用 Visual Studio 中的 ClickOnce 发布向导或发布页生成的引导程序，则会自动为 Setup.exe 签名。 但如果你希望使用客户的证书为引导程序签名，则可稍后对文件签名。  
  
## <a name="bootstrapping-and-msbuild"></a>引导和 MSBuild  
 如果不使用 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)][!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]，但是在命令行上编译应用程序，则可以使用 Microsoft Build Engine (MSBuild) 任务创建  引导应用程序。 有关详细信息，请参阅[GenerateBootstrapper 任务](../msbuild/generatebootstrapper-task.md)。  
  
 作为引导的替代方法，你可以使用电子软件分发系统（如 Microsoft Systems Management Server (SMS)）预先部署组件。  
  
## <a name="bootstrapper-setupexe-command-line-arguments"></a>引导程序 (Setup.exe) 命令行参数  
 由 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 和 MSBuild 任务生成的 Setup.exe 支持下面一小组命令行参数。 提供给引导应用程序的其他所有参数都会转发给应用程序安装程序。  
  
 如果更改了任何引导程序选项，则必须更改未签名的引导程序，稍后再对引导程序文件进行签名。  
  
|命令行参数|描述|  
|---------------------------|-----------------|  
|**-？，-h、-帮助**|显示一个“帮助”对话框。|  
|**-url，-componentsurl**|显示用于此安装的存储 URL 和组件 URL。|  
|**-url =**`location`|设置 Setup.exe 将在其中查找 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 应用程序的 URL。|  
|**-componentsurl =**`location`|设置 Setup.exe 将在其中查找依赖项（如 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]）的 URL。|  
|**-homesite =** `true` **&#124;**`false`|当`true`，从供应商的站点上的首选位置下载依赖项。 此设置将替代**-componentsurl**设置。 当`false`，从指定的 URL 下载依赖项**-componentsurl**。|  
  
## <a name="operating-system-support"></a>操作系统支持  
 Windows Server 2008 服务器核心或 Windows Server 2008 R2 服务器核心提供功能有限的低级维护服务器环境，不支持 Visual Studio 引导程序。 例如，“服务器核心”安装选项仅支持 .NET Framework 3.5 服务器核心配置文件，因此依赖于完整的 .NET Framework 的 Visual Studio 功能无法运行。  
  
## <a name="see-also"></a>另请参阅  
 [选择 ClickOnce 部署策略](../deployment/choosing-a-clickonce-deployment-strategy.md)   
 [ClickOnce 安全和部署](../deployment/clickonce-security-and-deployment.md)