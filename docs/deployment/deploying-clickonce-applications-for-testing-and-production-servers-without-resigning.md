---
title: "为测试部署 ClickOnce 应用程序服务器和生产服务器无需重新签名 |Microsoft 文档"
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
- ClickOnce applications, deploying without resigning
- ClickOnce deployment, without resigning
- application updates, ClickOnce
- update location [ClickOnce]
- deploymentProvider tag
- manifests [ClickOnce]
ms.assetid: 1218a98d-1ad5-4eef-95dd-0e0b3c44168c
caps.latest.revision: "10"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 91261e0bb70092861f216333bd73a11dc07790ba
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="deploying-clickonce-applications-for-testing-and-production-servers-without-resigning"></a>在不重新签名的情况下为测试服务器和生产服务器部署 ClickOnce 应用程序
本主题讨论 ClickOnce.NET Framework 版本 3.5，而无需重新签名，或更改 ClickOnce 可以从多个网络位置的 ClickOnce 应用程序的部署清单中引入的新功能。  
  
> [!NOTE]
>  重新签名仍然是部署新版本的应用程序的首选的方法。 只要可能，则使用重新签名的方法。 有关详细信息，请参阅 [Mage.exe（清单生成和编辑工具）](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)。  
  
 第三方开发人员和 Isv 可以选择加入此功能，使其更便于客户更新他们的应用程序。 在以下情况下，可以使用此功能：  
  
-   当更新应用程序，而非应用程序的第一个安装。  
  
-   只有一个配置的计算机上的应用程序时。 例如，如果应用程序配置为指向两个不同的数据库，你无法使用此功能。  
  
## <a name="excluding-deploymentprovider-from-deployment-manifests"></a>从部署清单中排除 deploymentProvider  
 在.NET Framework 2.0 和.NET Framework 3.0 中，在脱机可用性的系统安装任何 ClickOnce 应用程序必须指定`deploymentProvider`在其部署清单。 `deploymentProvider`通常称为的更新位置; 它是在其中 ClickOnce 将检查应用程序更新的位置。 此要求，结合了要对其部署签名的应用程序发布者的需求，使公司更新供应商或其他第三方提供 ClickOnce 应用程序的困难。 它还使更难从同一网络上的多个位置相同的应用程序部署。  
  
 使用在.NET Framework 3.5 的 ClickOnce 对所做的更改，就可能为第三方提供到另一个组织，然后可以将其自己的网络上的应用程序部署 ClickOnce 应用程序。  
  
 若要充分利用此功能，ClickOnce 应用程序的开发人员必须排除`deploymentProvider`从其部署清单。 这意味着不包括`-providerUrl`自变量时创建部署清单 Mage.exe，或确保与**启动位置**上的文本框**应用程序清单**选项卡上为空如果你正在生成使用 MageUI.exe 的部署清单。  
  
## <a name="deploymentprovider-and-application-updates"></a>deploymentProvider 和应用程序更新  
 从.NET Framework 3.5 开始，不再需要指定`deploymentProvider`若要部署的 ClickOnce 应用程序联机和脱机使用部署清单中。 这样可支持方案中，你需要以打包和签名部署你自己，但允许其他公司来对其网络上部署应用程序。  
  
 要记住的要点是，应用程序排除`deploymentProvider`期间无法更改其安装位置更新，直到它们提供的更新包含`deploymentProvider`再次标记。  
  
 下面是两个示例来澄清这一点。 在第一个示例中，发布的 ClickOnce 应用程序未包含任何`deploymentProvider`标记，并且你要求用户从 http://www.adatum.com/MyApplication/ 安装它。 如果你决定你想要将下一步更新 http://subdomain.adatum.com/MyApplication/ 应用程序的发布，则将必须没有表明这驻留在 http://www.adatum.com/MyApplication/ 部署清单中的方法。 你可以执行以下两项操作之一：  
  
-   通知用户卸载以前的版本中，并从新位置中安装新版本。  
  
-   包括的更新，包括 http://www.adatum.com/MyApplication/`deploymentProvider`指向 http://www.adatum.com/MyApplication/。 然后，释放更高版本与另一个更新`deploymentProvider`指向 http://subdomain.adatum.com/MyApplication/。  
  
 在第二个示例中，发布 ClickOnce 应用程序，指定`deploymentProvider`，，然后决定将其删除。 不带一次新的版本`deploymentProvider`已下载到客户端，你将无法重定向之前发布的应用程序具有的版本，用于更新的路径`deploymentProvider`还原。 与第一个示例中，`deploymentProvider`最初必须指向当前的更新位置，而不是新位置。 在此情况下，如果你尝试插入`deploymentProvider`，是指 http://subdomain.adatum.com/MyApplication/，则下一次更新将失败。  
  
## <a name="creating-a-deployment"></a>创建部署  
 创建可以从不同的网络位置部署的部署分步指南，请参阅[演练： 手动部署 ClickOnce 应用程序，不会不需要重新签名并且该保留的品牌信息](../deployment/walkthrough-manually-deploying-a-clickonce-application-that-does-not-require-re-signing-and-that-preserves-branding-information.md).  
  
## <a name="see-also"></a>另请参阅  
 [Mage.exe（清单生成和编辑工具）](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)   
 [MageUI.exe（图形化客户端中的清单生成和编辑工具）](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)