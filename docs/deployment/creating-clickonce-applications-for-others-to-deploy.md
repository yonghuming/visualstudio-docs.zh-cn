---
title: "创建供其他人部署的 ClickOnce 应用程序 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "<useManifestForTrust> 元素"
  - "应用程序清单 [ClickOnce]"
  - "ClickOnce 应用程序, 他方部署"
  - "ClickOnce 应用程序, 以前的 .NET Framework"
  - "ClickOnce 应用程序, 早期 .NET Framework 版本"
  - "客户部署 [ClickOnce]"
  - "清单 [ClickOnce]"
  - "多个 ClickOnce 部署和品牌"
  - "保留的品牌信息"
  - "信任应用程序, ClickOnce"
  - "useManifestForTrust 元素"
ms.assetid: d20766c7-4ef3-45ab-8aa0-3f15b61eccaa
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 创建供其他人部署的 ClickOnce 应用程序
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

并非所有创建 ClickOnce 部署的开发人员都计划由自己部署应用程序。  其中许多人只是使用 ClickOnce 来打包他们的应用程序，然后将文件转交给客户，如一家大型企业。  在这种情况下，客户将是在其网络上承载该应用程序的负责人。  本主题讨论在 .NET Framework 3.5 版之前的版本中进行此类部署时固有的一些问题。  然后讨论通过使用 .NET Framework 3.5 中的“使用信任清单”新功能提供的新解决方案。  最后，为仍然使用早期版本的 .NET Framework 的客户推荐创建 ClickOnce 部署的策略。  
  
## 为客户创建部署所涉及的问题  
 当您计划为客户提供部署时会遇到几个问题。  第一个问题涉及代码签名。  为了能够在网络中部署，ClickOnce 部署的部署清单和应用程序清单必须同时使用数字证书进行签名。  这就引出了为清单签名时是使用开发人员证书还是使用客户证书的问题。  
  
 使用哪个证书的问题至关重要，因为 ClickOnce 应用程序的标识基于部署清单的数字签名。  如果开发人员为部署清单签名，同时客户是一家大型企业，并且该企业的多个部门部署了该应用程序的自定义版本，则可能会导致冲突。  
  
 例如，假设 Adventure Works 拥有一个财务部门和一个人力资源部门。  两个部门都从 Microsoft Corporation 获得了 ClickOnce 应用程序的许可，该应用程序根据存储在 SQL 数据库中的数据生成报告。  Microsoft 为每个部门提供了针对其数据定制的应用程序版本。  如果这些应用程序使用了相同的 Authenticode 证书进行签名，则尝试使用这两个应用程序的用户会遇到错误，因为 ClickOnce 会将第二个应用程序看作与第一个程序相同。  在这种情况下，客户会遇到不可预知且不利的负面影响，包括丢失应用程序在本地存储的任何数据。  
  
 与代码签名相关的另一个问题是部署清单中的 `deploymentProvider` 元素，该元素告诉 ClickOnce 在哪里查找应用程序更新。  必须在对部署清单签名之前将此元素添加到部署清单中。  如果在签名后添加此元素，则必须重新对部署清单签名。  
  
### 要求客户为部署清单签名  
 针对非唯一部署问题的一个解决方案是让开发人员为应用程序清单签名，同时让客户为部署清单签名。  尽管此方法会起作用，但是会引入其他问题。  由于 Authenticode 证书必须保留为受保护的资产，因此客户不应仅仅将证书提供给开发人员，让其为部署签名。  尽管客户自己可以免费使用 .NET Framework SDK 提供的工具为部署清单签名，但是所需要的技术知识可能超出客户的意愿或能力范围之外。  在这种情况下，开发人员通常创建一个应用程序、网站或其他机制，使客户可以通过这些渠道提交其应用程序版本以进行签名。  
  
### 客户签名对 ClickOnce 应用程序安全性的影响  
 即使开发人员和客户同意由客户为应用程序清单签名，这也会产生有关应用程序标识的其他问题，特别是应用于受信任应用程序部署时。  （有关此功能的更多信息，请参见[受信任的应用程序部署概述](../deployment/trusted-application-deployment-overview.md)。）假设 Adventure Works 希望配置其客户端计算机，以便 Microsoft Corporation 为其提供的任何应用程序都能以完全信任方式运行。  如果 Adventure Works 对部署清单进行了签名，则 ClickOnce 将使用 Adventure Works 的安全签名来确定该应用程序的信任级别。  
  
## 通过使用信任应用程序清单来创建客户部署  
 .NET Framework 3.5 中的 ClickOnce 包含一个新功能，针对如何为清单签名的问题为开发人员和客户提供了新的解决方案。  ClickOnce 应用程序清单支持一个名为 `<useManifestForTrust>` 的新元素，开发人员可通过此元素表明在做出信任决策时应使用应用程序清单的数字签名。  开发人员使用 ClickOnce 打包工具（如 Mage.exe、MageUI.exe 和 Visual Studio）将此元素加入到应用程序清单中，同时在清单中嵌入其发行者名称和应用程序名称。  
  
 当使用 `<useManifestForTrust>` 时，部署清单不必使用由证书颁发机构颁发的 Authenticode 证书进行签名，  而可以使用称为自签名证书的证书进行签名。  自签名证书是由客户或开发人员使用标准 .NET Framework SDK 工具生成的，然后通过使用标准 ClickOnce 部署工具应用到部署清单。  有关更多信息，请参见[Makecert.exe（证书创建工具）](../Topic/Makecert.exe%20\(Certificate%20Creation%20Tool\).md)。  
  
 为部署清单使用自签名证书具有多项优点。  由于客户不必再获取或创建自己的 Authenticode 证书，`<useManifestForTrust>` 简化了客户的部署工作，同时允许开发人员在应用程序上保持他们自己的品牌标识，  因此可以产生一组更安全且具有唯一应用程序标识的已签名部署。  这将消除向多个客户部署同一应用程序时可能发生的潜在冲突。  
  
 有关如何创建启用 `<useManifestForTrust>` 的 ClickOnce 部署的详细步骤信息，请参见[演练：手动部署不需要重新签名并且保留署名信息的 ClickOnce 应用程序](../deployment/walkthrough-manually-deploying-a-clickonce-application-that-does-not-require-re-signing-and-that-preserves-branding-information.md)。  
  
### 信任应用程序清单在运行时的工作方式  
 为了更好地理解信任应用程序清单在运行时的工作方式，请参考以下示例。  Microsoft 创建了面向 .NET Framework 3.5 的 ClickOnce 应用程序。  该应用程序清单使用 `<useManifestForTrust>` 元素并由 Microsoft 签名。  Adventure Works 使用自签名证书为部署清单签名。  Adventure Works 客户端配置为信任由 Microsoft 签名的任何应用程序。  
  
 当用户单击指向部署清单的链接时，ClickOnce 将在用户的计算机上安装该应用程序。  证书和部署信息向客户端计算机上的 ClickOnce 唯一地标识该应用程序。  如果用户尝试在不同的位置安装同一应用程序，则 ClickOnce 可以使用此标识确定客户端上已存在该应用程序。  
  
 接下来，ClickOnce 检查用于为应用程序清单签名的 Authenticode 证书，该证书决定 ClickOnce 将授予的信任级别。  由于 Adventure Works 已将其客户端配置为信任由 Microsoft 签名的任何应用程序，因此该 ClickOnce 应用程序被授予完全信任权限。  有关更多信息，请参见[受信任的应用程序部署概述](../deployment/trusted-application-deployment-overview.md)。  
  
## 针对早期版本创建客户部署  
 如果开发人员正在为使用早期版本的 .NET Framework 的客户部署 ClickOnce 应用程序，该怎么办？  以下部分总结了多个建议解决方案，以及每个解决方案的优点和缺点。  
  
### 代表客户为部署签名  
 一种可行的部署策略是开发人员创建一种机制，即通过使用客户的自有私钥，代表客户为部署签名。  这样，开发人员不必要管理私钥或多个部署包，  而只需要为每个客户提供相同的部署。  客户将负责使用签名服务并根据环境对部署进行自定义。  
  
 此方法的一个缺点体现在实施此策略的时间和费用上。  虽然此类服务可使用 .NET Framework SDK 中提供的工具生成，但是它会给产品生命周期增加更多的开发时间。  
  
 如本主题前面所述，另一个缺点是每个客户的应用程序版本将具有相同的应用程序标识，这可能导致冲突。  如果此问题较为重要，则开发人员可以更改生成部署清单时所使用的“名称”字段，以便为每个应用程序提供唯一的名称。  这将为每个版本的应用程序创建单独的标识，从而消除任何潜在的标识冲突。  此字段对应于 Mage.exe 的 `-Name` 参数，以及 MageUI.exe 中的**“名称”**选项卡上的**“名称”**字段。  
  
 例如，假设开发人员创建了名为 Application1 的应用程序。  开发人员无需创建将“名称”字段设置为 Application1 的单个部署，而可以创建多个其名称特定于客户差异的多个部署，如 Application1\-CustomerA、Application1\-CustomerB，等等。  
  
### 使用安装包进行部署  
 第二个可行的部署策略是生成 Microsoft 安装项目，以执行 ClickOnce 应用程序的初始部署。  这可以采用多种不同的格式之一提供：作为 MSI 部署、作为安装可执行文件 \(.EXE\)，或作为压缩 \(.cab\) 文件以及批处理脚本。  
  
 使用此技术，开发人员将为客户提供包括应用程序文件、应用程序清单和用作模板的部署清单的部署。  客户将运行安装程序，该安装程序会提示客户提供部署 URL（用户将在其中安装 ClickOnce 应用程序的服务器或文件共享位置）以及数字证书。  安装应用程序还可能选择提示输入其他 ClickOnce 配置选项，如更新检查间隔。  当收集此信息之后，安装程序将生成实际的部署清单，为其签名，并将 ClickOnce 应用程序发布到指定的服务器位置。  
  
 在这种情况下，客户可以通过三种方式为部署清单签名：  
  
1.  客户可以使用由证书颁发机构 \(CA\) 颁发的有效证书。  
  
2.  作为此方法的一个变体，客户可以选择使用自签名证书为其部署清单签名。  这种方法的缺点是，当用户被询问是否进行安装时，应用程序将显示文字“未知发行者”。  而优点是使规模较小的客户不必在证书颁发机构所颁发的证书方面花费时间和资金。  
  
3.  最后，开发人员可以将自己的自签名证书加入到安装包中。  这会引入如本主题前面所述的应用程序标识方面的潜在问题。  
  
 安装部署项目方法的缺点体现在生成自定义部署应用程序所需的时间和费用。  
  
### 让客户生成部署清单  
 第三个可行的部署策略是只将应用程序文件和应用程序清单转交给客户。  在这种情况下，客户负责使用 .NET Framework SDK 生成部署清单并进行签名。  
  
 这种方法的缺点在于，要求客户安装 .NET Framework SDK 工具并拥有能熟练使用该工具的开发人员或系统管理员。  某些客户要求解决方案在技术方面不会对他们提出过高的要求，或没有技术方面的要求。  
  
## 请参阅  
 [在不重新签名的情况下为测试服务器和生产服务器部署 ClickOnce 应用程序](../deployment/deploying-clickonce-applications-for-testing-and-production-servers-without-resigning.md)   
 [演练：手动部署 ClickOnce 应用程序](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [演练：手动部署不需要重新签名并且保留署名信息的 ClickOnce 应用程序](../deployment/walkthrough-manually-deploying-a-clickonce-application-that-does-not-require-re-signing-and-that-preserves-branding-information.md)