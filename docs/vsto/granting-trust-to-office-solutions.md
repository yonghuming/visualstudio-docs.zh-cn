---
title: "向 Office 解决方案授予信任 |Microsoft 文档"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- security [Office development in Visual Studio], trust
- inclusion lists [Office development in Visual Studio], about inclusion lists
- trust [Office development in Visual Studio], 2007 Office system
- granting trust [Office development in Visual Studio]
ms.assetid: 6c33e614-d367-4556-9e76-0f302ad0f929
caps.latest.revision: "37"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: da7f4695bc817a66761c579b4c5af85b59ee041f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="granting-trust-to-office-solutions"></a>向 Office 解决方案授予信任
  向 Office 解决方案授予信任信任意味着修改每个目标计算机以信任解决方案程序集、 应用程序清单、 部署清单和文档的安全策略。 由您或最终用户，可以向 Office 解决方案授予信任。  
  
 可以通过对应用程序和部署清单进行签名来授予对 Office 解决方案的完全信任。  
  
 最终用户可以通过做出信任决定在授予 Office 解决方案的信任[!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]信任提示。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
##  <a name="Signing"></a>向解决方案授予信任的签名的应用程序和部署清单  
 所有应用程序和部署清单为 Office 解决方案必须使用标识发布者的证书进行签名。 证书提供基础来做出信任决定。  
  
 临时证书是为你创建，并且在生成时授予信任，以便在调试时，将运行该解决方案。 如果发布使用的临时证书进行签名的解决方案，则将提示最终用户来做出信任决定。  
  
 如果签名包含一个已知且受信任的证书的解决方案，而不提示最终用户做出信任决定将自动安装解决方案。 有关如何获取用于签名的证书的详细信息，请参阅[ClickOnce 和 Authenticode](/visualstudio/deployment/clickonce-and-authenticode)。 获取证书后，必须将它添加到受信任的发行者列表的显式信任该证书。 有关详细信息，请参阅[如何： 为 ClickOnce 应用程序添加到客户端计算机的受信任的发布服务器](/visualstudio/deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications)。  
  
 如果开发人员进行签名包含一个临时证书的解决方案，管理员可以通过使用清单生成和编辑工具 (mage.exe)，这是 Microsoft.NET Framework 工具之一进行重新注册与一个已知且受信任的证书的自定义项。 有关对解决方案进行签名的详细信息，请参阅[How to： 登录 Office 解决方案](../vsto/how-to-sign-office-solutions.md)和[How to： 登录应用程序和部署清单](/visualstudio/ide/how-to-sign-application-and-deployment-manifests)。  
  
##  <a name="TrustPrompt"></a>向解决方案授予信任使用 ClickOnce 信任提示  
 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]将提示最终用户如果没有组织范围策略信任解决方案的证书做出信任决定。 如果最终用户授予到解决方案的信任，则会创建包含要存储此信任决定的 URL 和公钥的包含列表条目。 更高版本运行时的受信任的自定义项，最终用户不会再次提示。  
  
 管理员可以禁用[!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]信任提示或需要仅对使用验证码证书进行签名的解决方案出现提示。 有关如何更改这些设置为 MyComputer、 LocalIntranet、 Internet、 TrustedSites，和 UntrustedSites 区域的详细信息，请参阅[如何： 配置 ClickOnce 信任提示行为](/visualstudio/deployment/how-to-configure-the-clickonce-trust-prompt-behavior)。  
  
## <a name="see-also"></a>另请参阅  
 [保护 Office 解决方案](../vsto/securing-office-solutions.md)   
 [向文档授予信任](../vsto/granting-trust-to-documents.md)   
 [Office 解决方案安全性疑难解答](../vsto/troubleshooting-office-solution-security.md)   
 [Office 解决方案的特定安全注意事项](../vsto/specific-security-considerations-for-office-solutions.md)  
  
  