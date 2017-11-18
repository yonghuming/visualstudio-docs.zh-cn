---
title: "创建 ClickOnce 部署应用程序供其他 |Microsoft 文档"
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
- preserved branding information
- useManifestForTrust element
- customer deployments [ClickOnce]
- multiple ClickOnce deployment and branding
- ClickOnce applications, previous .NET Framework versions
- application manifests [ClickOnce]
- <useManifestForTrust> element
- manifests [ClickOnce]
- trust applications, ClickOnce
- ClickOnce applications, deployed by others
- ClickOnce applications, previous .NET Framework
ms.assetid: d20766c7-4ef3-45ab-8aa0-3f15b61eccaa
caps.latest.revision: "10"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 0ca5bb824cbe4e37db241aba956f9f6bf91d18cd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="creating-clickonce-applications-for-others-to-deploy"></a>创建供其他人部署的 ClickOnce 应用程序
并非所有开发人员正在使用 ClickOnce 部署都计划部署应用程序本身。 许多它们只需将其应用程序打包使用 ClickOnce，然后将文件提交给客户，例如大型公司。 客户成为一个负责承载其网络上的应用程序。 本主题讨论一些.NET Framework 3.5 版之前的版本中的这种部署中固有的问题。 然后，它将介绍通过使用.NET Framework 3.5 中的新的"使用信任的清单"功能提供一个新的解决方案。 最后，则可以确定创建仍使用较旧版本.NET Framework 的客户的 ClickOnce 部署的建议策略。  
  
## <a name="issues-involved-in-creating-deployments-for-customers"></a>涉及的创建的客户的部署问题  
 当您打算提供给客户的部署，会出现几个问题。 第一个问题涉及代码签名。 为了能够在网络中部署，部署清单和 ClickOnce 部署的应用程序清单必须同时使用数字证书进行签名。 这就提高了这一问题时是否使用开发人员的证书或客户的证书对清单进行签名。  
  
 要使用的证书问题至关重要，因为 ClickOnce 应用程序的标识基于部署清单的数字签名。 如果开发人员对部署清单进行签名，它可能导致冲突，如果客户是大型公司，并且多个部门的公司部署应用程序的自定义的版本。  
  
 例如，假设 Adventure Works 具有财务部门和人力资源部门。 这两个部门许可证 ClickOnce 应用程序的 SQL 数据库中存储的数据生成报告的 Microsoft Corporation。 Microsoft 提供了每个部门为其数据自定义应用程序的版本。 如果使用相同的验证码证书进行签名的应用程序，尝试使用两个应用程序的用户会遇到错误，如 ClickOnce 将考虑第二个应用程序为与第一个完全相同。 在这种情况下，客户可能会遇到不可预测的不需要负面影响，包括本地存储应用程序的任何数据丢失。  
  
 另一个问题相关的代码签名是否`deploymentProvider`告诉 ClickOnce 在哪里查找应用程序更新的部署清单中的元素。 此元素具有要添加到部署清单之前对它的签名。 如果以后添加此元素，则必须重新签名的部署清单。  
  
### <a name="requiring-the-customer-to-sign-the-deployment-manifest"></a>要求客户为部署清单签名  
 非唯一部署此问题的一种解决方案是具有开发人员的符号应用程序清单中，并且客户对部署清单进行签名。 在这种方法，它引入了其他问题。 由于验证码证书必须保持受保护的资产，则客户无法只需指定证书向开发人员对部署进行签名。 尽管客户可以部署清单签名本身使用随.NET Framework SDK 免费提供的工具，这可能需要更多技术知识大于客户愿意或能够提供。 在这种情况下，开发人员通常创建应用程序、 Web 站点或通过其客户可以提交其版本进行签名的应用程序的其他机制。  
  
### <a name="the-impact-of-customer-signing-on-clickonce-application-security"></a>在 ClickOnce 应用程序安全性上签名的客户的影响  
 即使开发人员和客户同意客户应登录应用程序清单，这会引发环绕应用程序的标识，其他问题，尤其是当它适用于受信任的应用程序部署。 (有关此功能的详细信息，请参阅[受信任的应用程序部署概述](../deployment/trusted-application-deployment-overview.md)。)假设 Adventure Works 想要配置其客户端计算机，以便由 Microsoft Corporation 向它们提供任何应用程序运行以完全信任。 如果 Adventure Works 对部署清单进行签名，则 ClickOnce 将使用 Adventure 工作安全签名以确定应用程序的信任级别。  
  
## <a name="creating-customer-deployments-by-using-application-manifest-for-trust"></a>使用 for 信任的应用程序清单创建客户部署  
 在.NET Framework 3.5 的 ClickOnce 包含一项新功能，让开发人员和客户的新解决方案应如何对清单进行签名的方案。 ClickOnce 应用程序清单支持名为的新元素`<useManifestForTrust>`，它使开发人员可以表示应用程序清单的数字签名是什么应该用于做出信任决定。 开发人员使用 ClickOnce 打包工具 — 例如 Mage.exe 和 MageUI.exe 中，Visual Studio-若要在应用程序清单中包含此元素，以及若要将其发布者名称和应用程序的名称嵌入在清单中。  
  
 使用时`<useManifestForTrust>`，部署清单不需要使用证书颁发机构颁发的验证码证书进行签名。 相反，它可以与所谓的自签名证书进行签名。 自签名的证书是由客户或开发人员生成通过使用标准.NET Framework SDK 工具，并通过使用标准的 ClickOnce 部署工具然后对部署清单中应用。 有关详细信息，请参阅[MakeCert](https://msdn.microsoft.com/library/windows/desktop/aa386968.aspx)。  
  
 对于部署清单中使用自签名的证书具有多项优点。 通过消除客户获取或创建自己的验证码证书，需`<useManifestForTrust>`简化了对于客户，同时允许开发人员来维护自己的品牌标识应用程序的部署。 结果是一套更安全且具有唯一的应用程序标识的已签名的部署。 这将消除可能来自同一应用程序部署到多个客户的潜在冲突。  
  
 有关如何创建使用 ClickOnce 部署的分步信息`<useManifestForTrust>`启用，请参阅[演练： 手动部署 ClickOnce 应用程序，不会不需要重新签名并且该保留的品牌信息](../deployment/walkthrough-manually-deploying-a-clickonce-application-that-does-not-require-re-signing-and-that-preserves-branding-information.md).  
  
### <a name="how-application-manifest-for-trust-works-at-runtime"></a>如何应用程序清单信任在运行时的工作原理  
 若要获取更好地理解使用信任的应用程序清单的工作原理在运行时，请考虑下面的示例。 由 Microsoft 创建面向.NET Framework 3.5 ClickOnce 应用程序。 应用程序清单使用`<useManifestForTrust>`元素和由 Microsoft 签名。 Adventure Works 使用自签名的证书进行签名的部署清单。 Adventure 的 Works 客户端配置为信任经过 Microsoft 签名的任何应用程序。  
  
 当用户单击时向部署清单的链接时，ClickOnce 将安装在用户的计算机上的应用程序。 证书和部署信息标识唯一到客户端计算机上的 ClickOnce 应用程序。 如果用户尝试从不同的位置重新安装相同的应用程序，ClickOnce 可以使用此标识来确定应用程序已在客户端上存在。  
  
 接下来，ClickOnce 检查验证码证书用于签署应用程序清单，确定所 ClickOnce 将授予的信任级别。 Adventure Works 已配置其客户端信任经过 Microsoft 签名的任何应用程序，因为此 ClickOnce 应用程序被授予完全信任。 有关详细信息，请参阅 [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md)。  
  
## <a name="creating-customer-deployments-for-earlier-versions"></a>创建早期版本的客户部署  
 如果开发人员正在部署到使用较旧版本.NET Framework 的客户的 ClickOnce 应用程序？ 以下部分汇总了多个建议的解决方案，以及每个优缺点。  
  
### <a name="sign-deployments-on-behalf-of-customer"></a>代表客户登录部署  
 一种可能的部署策略是开发人员用来创建一种机制来通过使用客户自己的私钥签名代表其客户的部署。 这可以防止开发人员无需管理私钥或多个部署包。 开发人员只需为每个客户提供相同的部署。 负责客户自定义它以便其环境使用签名的服务。  
  
 此方法的一个缺陷就是的时间和实现它所需的费用。 可以通过使用.NET Framework SDK 中提供的工具生成此类服务，它将向产品生命周期中添加更多的开发时间。  
  
 如本主题中前面所述，另一个缺点是，每个客户的版本的应用程序将具有相同的应用程序标识，这可能导致冲突。 如果这是一个问题，开发人员可以更改名称字段用于生成部署清单时提供一个唯一名称的每个应用程序。 这将创建单独的标识每个版本的应用程序，并消除任何潜在的标识冲突。 此字段对应于`-Name`自变量以 Mage.exe 中，请和**名称**字段上**名称**MageUI.exe 中的选项卡。  
  
 例如，开发人员创建名为应用程序 1 的应用程序。 而不是使用名称字段设置为应用程序 1 中创建单个部署，开发人员可以与此名称，如应用程序 1 CustomerA，应用程序 1 CustomerB，特定于客户的变体创建多个部署，依此类推。  
  
### <a name="deploy-using-a-setup-package"></a>使用安装包进行部署  
 第二个可能的部署策略是生成 Microsoft 安装程序项目，以执行 ClickOnce 应用程序的初始部署。 这可以提供几种不同的格式之一： 作为 MSI 部署，作为可执行安装程序 (。EXE)，或作为 cabinet (.cab) 文件以及一个批处理脚本。  
  
 使用此技术，开发人员将提供客户部署包含应用程序文件、 应用程序清单中和一个用作模板的部署清单。 客户将运行安装程序会提示客户 （服务器或文件共享的用户将从其中安装 ClickOnce 应用程序的位置） 时，部署 URL 以及数字证书。 安装应用程序还可以选择为提示输入其他 ClickOnce 配置选项，如更新检查间隔。 收集此信息之后, 安装程序将生成实际的部署清单、 其签名，以及发布 ClickOnce 应用程序到指定的服务器位置。  
  
 有三种方法，客户可以在此情况下部署清单进行签名：  
  
1.  客户可以使用由证书颁发机构 (CA) 颁发的有效证书。  
  
2.  为此方法变体，客户可以选择对其使用自签名证书的部署清单进行签名。 这的缺点是，它将导致应用程序时将其安装要求用户显示单词"未知发布服务器"。 但是的好处是它可防止较小的客户无需投入时间和资金所需的证书颁发机构颁发的证书。  
  
3.  最后，开发人员可以在安装程序包中包含其自己的自签名的证书。 它引入了与本主题前面所述的应用程序标识的潜在问题。  
  
 安装程序部署项目方法的缺点是时间和生成自定义部署应用程序所需的开销。  
  
### <a name="have-customer-generate-deployment-manifest"></a>让客户生成部署清单  
 第三个可能的部署策略是移交应用程序文件和应用程序清单关闭给客户。 在此方案中，客户负责使用.NET Framework SDK 来生成和部署清单进行签名。  
  
 此方法的缺点是，它需要客户若要安装.NET Framework SDK 工具中，并在开发人员或系统管理员是水平地使用它们。 有些客户可能要求解决方案需要很少或没有技术其一部分工作。  
  
## <a name="see-also"></a>另请参阅  
 [为测试部署 ClickOnce 应用程序服务器和生产服务器无需重新签名](../deployment/deploying-clickonce-applications-for-testing-and-production-servers-without-resigning.md)   
 [演练：手动部署 ClickOnce 应用程序](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [演练：手动部署不需要重新签名并且保留署名信息的 ClickOnce 应用程序](../deployment/walkthrough-manually-deploying-a-clickonce-application-that-does-not-require-re-signing-and-that-preserves-branding-information.md)