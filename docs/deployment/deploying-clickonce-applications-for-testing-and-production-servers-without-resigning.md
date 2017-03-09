---
title: "在不重新签名的情况下为测试服务器和生产服务器部署 ClickOnce 应用程序 | Microsoft Docs"
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
  - "应用程序更新, ClickOnce"
  - "ClickOnce 应用程序, 无需重新签名的部署"
  - "ClickOnce 部署, 无需重新签名"
  - "deploymentProvider 标记"
  - "清单 [ClickOnce]"
  - "更新位置 [ClickOnce]"
ms.assetid: 1218a98d-1ad5-4eef-95dd-0e0b3c44168c
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 在不重新签名的情况下为测试服务器和生产服务器部署 ClickOnce 应用程序
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

本主题讨论 .NET Framework 3.5 版中引入的 ClickOnce 的一个新增功能，该功能支持从多个网络位置部署 ClickOnce 应用程序，而无需重新签名或更改 ClickOnce 清单。  
  
> [!NOTE]
>  部署应用程序的新版本时重新签名仍然是首选方式。  应尽可能使用重新签名方法。  有关更多信息，请参见[Mage.exe（清单生成和编辑工具）](../Topic/Mage.exe%20\(Manifest%20Generation%20and%20Editing%20Tool\).md)。  
  
 第三方开发人员和 ISV 可以选用此功能，使其客户更加方便地更新他们的应用程序。  此功能可在下列情况下使用：  
  
-   在更新应用程序而不是首次安装应用程序时。  
  
-   当计算机上仅有应用程序的一个配置时。  例如，当某个应用程序配置为指向两个不同的数据库时，不能使用此功能。  
  
## 从部署清单中排除 deploymentProvider  
 在 .NET Framework 2.0 和 .NET Framework 3.0 中，任何安装在系统上以提供脱机可用性的 ClickOnce 应用程序都必须在其部署清单中指定 `deploymentProvider`。  通常将 `deploymentProvider` 称为更新位置，它是 ClickOnce 将在其中检查有无应用程序更新的位置。  此要求以及让应用程序发行者对其部署签名的要求，使公司很难更新供应商或其他第三方提供的 ClickOnce 应用程序。  这也使得从同一网络上的多个位置部署同一应用程序更为困难。  
  
 在 .NET Framework 3.5 中对 ClickOnce 进行更改后，第三方可以将 ClickOnce 应用程序提供给另一组织，而后者随后可将该应用程序部署到自己的网络中。  
  
 为了利用此功能，ClickOnce 应用程序的开发人员必须从其部署清单中排除 `deploymentProvider`。  这意味着，在使用 Mage.exe 创建部署清单时排除 `-providerUrl` 参数，或者在使用 MageUI.exe 生成部署清单时确保**“应用程序清单”**选项卡上的**“启动位置”**文本框保留为空。  
  
## deploymentProvider 和应用程序更新  
 从 .NET Framework 3.5 开始，您不必再在部署清单中指定 `deploymentProvider` 即可部署在脱机和联机时都可用的 ClickOnce 应用程序。  这就支持了以下情况：您需要自己对部署进行打包和签名，但允许其他公司在其网络上部署该应用程序。  
  
 需要记住的要点是，排除 `deploymentProvider` 的应用程序在再次提供包含 `deploymentProvider` 标记的更新之前无法在更新过程中更改其安装位置。  
  
 下面提供两个示例来说明这一点。  在第一个示例中，您发布了一个没有 `deploymentProvider` 标记的 ClickOnce 应用程序，并且要求用户从 http:\/\/www.adatum.com\/MyApplication\/ 安装它。  如果您决定要从 http:\/\/subdomain.adatum.com\/MyApplication\/ 发布该应用程序的下一个更新，您将无法在驻留在 http:\/\/www.adatum.com\/MyApplication\/ 中的部署清单中说明这一点。  您可以执行以下两项操作之一：  
  
-   通知用户卸载早期版本，并从新位置安装新版本。  
  
-   在 http:\/\/www.adatum.com\/MyApplication\/ 上添加一个更新，其中包含一个指向 http:\/\/www.adatum.com\/MyApplication\/ 的 `deploymentProvider`。  然后发布另一个包含指向 http:\/\/subdomain.adatum.com\/MyApplication\/ 的 `deploymentProvider` 的更新。  
  
 在第二个示例中，您发布了一个指定 `deploymentProvider` 的 ClickOnce 应用程序，然后您决定移除该标记。  在不带 `deploymentProvider` 的新版本下载到客户端后，您将无法重定向用于更新的路径，直到发布已经还原了 `deploymentProvider` 的应用程序版本。  如同第一个示例一样，`deploymentProvider` 最初必须指向当前的更新位置而不是新位置。  在此情况下，如果您尝试插入一个引用 http:\/\/subdomain.adatum.com\/MyApplication\/ 的 `deploymentProvider`，则下一个更新随后将失败。  
  
## 创建部署  
 有关创建可从不同网络位置进行部署的部署的分步指导，请参见[演练：手动部署不需要重新签名并且保留署名信息的 ClickOnce 应用程序](../deployment/walkthrough-manually-deploying-a-clickonce-application-that-does-not-require-re-signing-and-that-preserves-branding-information.md)。  
  
## 请参阅  
 [Mage.exe（清单生成和编辑工具）](../Topic/Mage.exe%20\(Manifest%20Generation%20and%20Editing%20Tool\).md)   
 [MageUI.exe（图形化客户端中的清单生成和编辑工具）](../Topic/MageUI.exe%20\(Manifest%20Generation%20and%20Editing%20Tool,%20Graphical%20Client\).md)