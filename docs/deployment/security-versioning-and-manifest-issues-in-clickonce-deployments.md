---
title: "ClickOnce 部署中的安全、版本控制和清单问题 | Microsoft Docs"
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
  - "ClickOnce 应用程序, 清单问题"
  - "ClickOnce 应用程序, 安全性问题"
  - "ClickOnce 应用程序, 版本问题"
  - "ClickOnce 应用程序, Windows Vista 用户帐户控制"
  - "清单 [ClickOnce]"
  - "安全性, ClickOnce 应用程序"
  - "用户帐户控制, ClickOnce 应用程序"
  - "版本, ClickOnce 应用程序"
  - "Windows 7, ClickOnce 部署"
  - "Windows Vista, ClickOnce 部署"
ms.assetid: d5d0c90b-ac1a-44e2-88dc-0d0ffd881624
caps.latest.revision: 21
caps.handback.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# ClickOnce 部署中的安全、版本控制和清单问题
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 安全性、应用程序版本控制以及清单语法和语义方面存在许多问题，这些问题可导致 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署失败。  
  
## ClickOnce 和 Windows Vista 用户帐户控制  
 在 [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)] 中，应用程序默认以标准用户的身份运行，即使当前用户用拥有管理员权限的帐户登录也是如此。  如果应用程序必须执行需要管理员权限的操作，它会告诉操作系统，操作系统随后会提示用户输入其管理员凭据。  此功能称为用户帐户控制 \(UAC\)，它可以防止应用程序在没有得到用户明确批准的情况下做出可能会影响整个操作系统的更改。  Windows 应用程序通过在应用程序清单的 `trustInfo` 部分指定 `requestedExecutionLevel` 特性来声明它们需要此权限提升。  
  
 考虑到将应用程序公开给安全提升攻击所带来的风险，如果已为客户端启用 UAC，[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 应用程序将无法请求权限提升。  任何尝试将 `requestedExecutionLevel` 特性设置为 `requireAdministrator` 或 `highestAvailable` 的 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 应用程序都不会在 [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)] 上安装。  
  
 有些情况下，[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 应用程序可能由于 [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)] 上的安装程序检测逻辑而尝试用管理员权限运行。  在这种情况下，您可以将应用程序清单中的 `requestedExecutionLevel` 特性设置为 `asInvoker`。  这样将使应用程序本身不用提升即可运行。[!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)] 自动将此特性添加到所有应用程序清单。  
  
 如果开发在整个生存期都需要管理员权限的应用程序，则应考虑改用 Windows Installer \(MSI\) 技术来部署应用程序。  有关更多信息，请参见 [Windows 安装程序基础知识](../extensibility/internals/windows-installer-basics.md)。  
  
## 联机应用程序配额和部分信任应用程序  
 如果 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 应用程序联机运行而不是通过安装运行，则它必须在为联机应用程序预留的配额范围之内。  此外，以部分信任的方式（如具有受限制的安全权限集）运行的网络应用程序不能大于配额大小的一半。  
  
 有关更多信息和如何更改联机应用程序配额的说明，请参见 [ClickOnce 缓存概述](../deployment/clickonce-cache-overview.md)。  
  
## 版本问题  
 如果将强名称指定给程序集，并递增程序集版本号以反映应用程序更新，则可能会遇到问题。  使用对强名称程序集的引用进行编译的任何程序集本身必须被重新编译，否则它会尝试引用旧版本。  程序集之所以将尝试此操作，是因为它在其绑定请求中使用旧版本值。  
  
 举例来说，假定您有一个强名称程序集，该程序集在自己的项目中的版本号为 1.0.0.0。  在编译该程序集之后，您将它作为引用添加到包含主应用程序的项目中。  如果更新该程序集，将版本递增到 1.0.0.1，并尝试在不重新编译应用程序的情况下进行部署，则应用程序将无法在运行时加载该程序集。  
  
 只有在手动编辑 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 清单时才会发生此错误；如果使用 [!INCLUDE[vsprvslong](../code-quality/includes/vsprvslong_md.md)] 生成部署，则不会遇到此错误。  
  
## 在清单中指定个别 .NET Framework 程序集  
 如果手动将 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署编辑为引用 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 程序集的某个较早版本，则应用程序将无法加载。  例如，如果添加了对清单中指定版本之前版本的 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 的 System.Net 程序集引用，则会出现错误。  由于在其上运行应用程序的 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 的版本被指定为应用程序清单中的依赖项，因此，通常不应尝试指定对个别 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 程序集的引用。  
  
## 清单分析问题  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 使用的清单文件为 XML 文件，这些文件必须格式良好且有效，即必须遵守 XML 语法规则，而且仅使用在相关 XML 架构中定义的元素和特性。  
  
 导致清单文件中出现问题的可能原因是为应用程序选择的名称包含特殊字符，例如单引号或双引号。  应用程序的名称是其 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 标识的一部分。  [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 目前不分析包含特殊字符的标识。  如果应用程序无法激活，请确保其名称只使用了字母和数字字符，并尝试重新部署它。  
  
 如果手动编辑过部署或应用程序清单，您可能会在无意中损坏它们。  如果清单损坏，则无法进行正确的 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 安装。  您可以通过单击**“ClickOnce 错误”**对话框中的**“详细信息”**，然后阅读日志中的错误信息，在运行时调试此类错误。  日志将列出下列消息之一：  
  
-   语法错误的说明，以及错误发生的行号和字符位置。  
  
-   违反清单架构的元素或特性的名称。  如果已向清单中手动添加了 XML，则需要将添加内容与清单架构进行比较。  有关更多信息，请参见 [ClickOnce 部署清单](../deployment/clickonce-deployment-manifest.md)和 [ClickOnce 应用程序清单](../deployment/clickonce-application-manifest.md)。  
  
-   ID 冲突。  部署清单和应用程序清单中的依赖项引用在 `name` 和 `publicKeyToken` 特性上必须保持唯一。  如果一个清单内任何两个元素间的这两个特性匹配，清单分析将会失败。  
  
## 手动更改清单或应用程序时的注意事项  
 更新应用程序清单时，必须重新对应用程序清单和部署清单进行签名。  部署清单包含一个对应用程序清单的引用，该清单中包含该文件的哈希数据和数字签名。  
  
### 使用部署提供程序的注意事项  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署清单具有一个 `deploymentProvider` 属性，该属性指向安装应用程序和为应用程序提供服务的源位置的完整路径：  
  
```  
<deploymentProvider codebase="http://myserver/myapp.application" />  
```  
  
 此路径是在 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 创建应用程序时设置的，并且对于安装的应用程序是必需的。  该路径指向一个标准位置，[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 安装程序将从该位置安装应用程序并搜索更新。  如果使用 **xcopy** 命令将 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 应用程序复制到其他位置，但不更改 `deploymentProvider` 属性，则当 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 尝试下载应用程序时，它仍将引用原始位置。  
  
 如果希望移动或复制应用程序，还必须更新 `deploymentProvider` 路径，这样客户端才能真正从新位置安装。  如果已安装了应用程序，则更新此路径在很多时候会成为一个问题。  对于始终通过原始 URL 启动的联机应用程序，`deploymentProvider` 为可选设置。  如果设置了 `deploymentProvider`，则使用该属性，否则将使用用于启动应用程序的 URL 作为基 URL 来下载应用程序文件。  
  
> [!NOTE]
>  每次更新清单时，还必须重新对其进行签名。  
  
## 请参阅  
 [ClickOnce 部署疑难解答](../deployment/troubleshooting-clickonce-deployments.md)   
 [保护 ClickOnce 应用程序](../deployment/securing-clickonce-applications.md)   
 [选择 ClickOnce 部署策略](../deployment/choosing-a-clickonce-deployment-strategy.md)