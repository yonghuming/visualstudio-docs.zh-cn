---
title: "安全性、 版本控制和 ClickOnce 部署中的清单问题 |Microsoft 文档"
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
- versioning, ClickOnce applications
- ClickOnce applications, Windows Vista User Account Control
- ClickOnce applications, versioning issues
- security, ClickOnce applications
- Windows 7, ClickOnce deployments
- ClickOnce applications, manifest issues
- User Account Control, ClickOnce applications
- Windows Vista, ClickOnce deployments
- manifests [ClickOnce]
- ClickOnce applications, security issues
ms.assetid: d5d0c90b-ac1a-44e2-88dc-0d0ffd881624
caps.latest.revision: "21"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 603ff665e2c01abe62954e4e65e49a095d358b29
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="security-versioning-and-manifest-issues-in-clickonce-deployments"></a>ClickOnce 部署中的安全、版本控制和清单问题
还有很多问题[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]安全性、 应用程序版本控制和清单的语法和语义，可能会导致[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]部署，不能成功。  
  
## <a name="clickonce-and-windows-vista-user-account-control"></a>ClickOnce 和 Windows Vista 用户帐户控制  
 在[!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)]，默认情况下的应用程序作为标准用户运行，即使当前用户使用具有管理员权限的帐户登录。 如果应用程序必须执行需要管理员权限的操作，它会通知操作系统，然后会提示用户输入其管理员凭据。 此功能，名为用户帐户控制 (UAC) 阻止进行更改可能会影响整个操作系统中，而无需用户的显式批准应用程序。 Windows 应用程序声明它们通过指定需要此权限提升`requestedExecutionLevel`属性中`trustInfo`其应用程序清单的一部分。  
  
 由于公开给安全提升攻击，应用程序的风险[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]如果客户端启用了 UAC，应用程序不能请求权限提升。 任何[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]尝试设置应用程序，其`requestedExecutionLevel`属性设为`requireAdministrator`或`highestAvailable`安装不会[!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)]。  
  
 在某些情况下，你[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]应用程序可能会尝试使用管理员权限运行安装程序检测逻辑由于[!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)]。 在这种情况下，你可以设置`requestedExecutionLevel`到应用程序清单中的特性`asInvoker`。 这将导致应用程序本身不用提升即可运行。 [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)]自动将此属性添加到所有应用程序清单。  
  
 如果你正在开发的应用程序需要管理员权限的应用程序的整个生存期内，则应考虑部署应用程序改为使用 Windows Installer (MSI) 技术。 有关详细信息，请参阅[Windows 安装程序基础知识](../extensibility/internals/windows-installer-basics.md)。  
  
## <a name="online-application-quotas-and-partial-trust-applications"></a>联机应用程序配额和部分信任应用程序  
 如果你[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]联机而不是通过安装应用程序运行，它必须适应留出的用于联机应用程序的配额。 此外，网络运行的应用程序在部分信任中，如具有一组受限的安全权限，不能大于配额大小的一半。  
  
 有关详细信息和有关如何更改配额的联机应用程序的说明，请参阅[ClickOnce 缓存概述](../deployment/clickonce-cache-overview.md)。  
  
## <a name="versioning-issues"></a>版本控制问题  
 如果你分配给您的程序集的强名称，并递增以反映应用程序更新的程序集版本号，你可能会遇到问题。 对具有强名称程序集的引用编译的任何程序集必须本身重新编译，或程序集将尝试引用较旧版本。 程序集将尝试此操作因为程序集在其绑定请求中使用的旧版本值。  
  
 例如，假设在其自身的版本号为 1.0.0.0 的项目中有具有强名称程序集。 在编译的程序集之后, 你将其添加为对包含主应用程序的项目的引用。 如果你更新该程序集，将版本递增到 1.0.0.1，并尝试将其部署而无需重新编译应用程序，应用程序不能加载运行时程序集。  
  
 可能出现此错误，仅当你编辑你[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]清单手动; 你不应遇到此错误，如果你生成你部署使用[!INCLUDE[vsprvslong](../code-quality/includes/vsprvslong_md.md)]。  
  
## <a name="specifying-individual-net-framework-assemblies-in-the-manifest"></a>在清单中指定单个.NET Framework 程序集  
 你的应用程序将无法加载如果你已手动编辑[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]部署引用较旧版本的[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]程序集。 例如，如果你添加到的版本的 System.Net 程序集的引用[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]之前在清单中指定的版本，然后会出现错误。 一般情况下，不应尝试指定对单个引用[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]程序集，作为版本[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]针对运行应用程序被指定为应用程序清单中的依赖项。  
  
## <a name="manifest-parsing-issues"></a>清单分析问题  
 通过使用清单文件[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]是 XML 文件，并且它们必须是格式正确且有效： 必须遵循 XML 语法规则，并且只能使用元素和相关的 XML 架构中定义的属性。  
  
 这会导致在清单文件中的问题选择包含一个特殊字符，例如单引号或双引号引号你应用程序的名称。 应用程序的名称是的一部分其[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]标识。 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]当前不会分析包含特殊字符的标识。 如果你的应用程序激活失败，请确保你的名称，使用仅字母和数字字符，并且尝试重新部署它。  
  
 如果你手动编辑你的部署或应用程序清单，你可能会无意中损坏它们。 损坏的清单将无法进行正确[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]安装。 可以通过单击来在运行时调试此类错误**详细信息**上**ClickOnce 错误**对话框中，并将读取日志中的错误消息。 日志将列出以下消息之一：  
  
-   语法错误的行号和字符的说明发生错误的位置。  
  
-   元素或在违反该清单的架构中使用的属性的名称。 如果你已手动添加 XML，到你的清单，你将需要比较你添加到清单架构。 有关详细信息，请参阅[ClickOnce 部署清单](../deployment/clickonce-deployment-manifest.md)和[ClickOnce 应用程序清单](../deployment/clickonce-application-manifest.md)。  
  
-   ID 冲突。 在部署和应用程序清单中的依赖项引用必须是唯一在其`name`和`publicKeyToken`属性。 如果这两个特性匹配在清单中任何两个元素间，清单分析将不会成功。  
  
## <a name="precautions-when-manually-changing-manifests-or-applications"></a>手动更改清单或应用程序时的注意事项  
 在更新应用程序清单时，你必须重新登录应用程序清单和部署清单。 部署清单包含对包括该文件的哈希和其数字签名的应用程序清单的引用。  
  
### <a name="precautions-with-deployment-provider-usage"></a>使用部署提供程序的注意事项  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]部署清单具有`deploymentProvider`属性用于从应安装和维护应用程序指向的位置的完整路径：  
  
```  
<deploymentProvider codebase="http://myserver/myapp.application" />  
```  
  
 此路径设置时[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]创建应用程序和已安装的应用程序强制性。 路径指向的标准位置其中[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]安装程序将安装的应用程序和更新的搜索。 如果你使用**xcopy**命令以便将复制[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]应用程序到另一个位置，但不要更改`deploymentProvider`属性，[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]仍将引用返回到原始位置时尝试下载应用程序。  
  
 如果你想要移动或复制应用程序，则还必须更新`deploymentProvider`路径，以便在客户端实际安装从新位置。 更新此路径是普遍问题，如果你已安装应用程序。 对于联机应用程序通过设置的原始 URL 始终启动`deploymentProvider`是可选的。 如果`deploymentProvider`设置，则将遵守它; 否则，用于启动应用程序的 URL 将使用用作基 URL，若要下载应用程序文件。  
  
> [!NOTE]
>  将清单更新每次你必须还对其签名试。  
  
## <a name="see-also"></a>另请参阅  
 [ClickOnce 部署疑难解答](../deployment/troubleshooting-clickonce-deployments.md)   
 [保护 ClickOnce 应用程序](../deployment/securing-clickonce-applications.md)   
 [选择 ClickOnce 部署策略](../deployment/choosing-a-clickonce-deployment-strategy.md)