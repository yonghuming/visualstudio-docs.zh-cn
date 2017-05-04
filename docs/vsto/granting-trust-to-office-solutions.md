---
title: "向 Office 解决方案授予信任 | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "安全性 [Visual Studio 中的 Office 开发]，信任"
  - "包含列表 [Visual Studio 中的 Office 开发]，有关包含列表"
  - "信任 [Visual Studio 中的 Office 开发]，2007 Office system"
  - "授予信任 [Visual Studio 中的 Office 开发]"
ms.assetid: 6c33e614-d367-4556-9e76-0f302ad0f929
caps.latest.revision: 37
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 36
---
# 向 Office 解决方案授予信任
  向 Office 解决方案授予信任意味着修改每个目标计算机的安全策略信任解决方案程序集清单、应用程序清单，的部署，并且文档。  信任可以向 Office 解决方案授予供您或最终用户。  
  
 可以授予完全信任 Office 解决方案通过对应用程序，并部署清单。  
  
 最终用户可以对 Office 解决方案授予信任通过做出在 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 信任提示信任决定。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
##  <a name="Signing"></a> 信任解决方案通过对应用程序和部署清单  
 必须使用标识发行者的证书对所有 Office 解决方案的应用程序清单和部署清单进行签名。  证书为做出信任决策提供基础。  
  
 在生成时为您创建了临时证书并向其授予信任，因此在调试解决方案时将运行此解决方案。  如果您发布用临时证书对解决方案，则会提示最终用户做出信任决定。  
  
 如果使用已知的受信任证书对解决方案进行签名，则将自动安装解决方案，而不会提示最终用户做出信任决定。  有关如何获取证书以进行签名的更多信息，请参见 [ClickOnce 和 Authenticode](../deployment/clickonce-and-authenticode.md)。  获得证书后，必须通过将证书添加到“受信任的发行者”列表中显式表示信任该证书。  有关更多信息，请参见[如何：为 ClickOnce 应用程序向客户端计算机添加一个受信任的发行者](~/deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)。  
  
 如果开发人员使用临时证书对解决方案进行签名，则管理员通过使用清单生成和编辑工具 \(mage.exe\)（Microsoft .NET Framework 工具之一），可以用已知的受信任证书对自定义项进行重新签名。  有关对解决方案进行签名的更多信息，请参见[如何：对 Office 解决方案进行签名](../vsto/how-to-sign-office-solutions.md) 和[如何：对应用程序和部署清单进行签名](~/ide/how-to-sign-application-and-deployment-manifests.md)。  
  
##  <a name="TrustPrompt"></a> 信任使用 ClickOnce 信任提示的解决方案  
 如果没有信任解决方案证书的组织策略，则 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 会提示最终用户做出信任决定。  如果最终用户向解决方案授予信任，则会创建一个包含 URL 和公钥的包含列表项以存储此信任决定。  以后运行受信任的自定义项时，将不再提示最终用户。  
  
 管理员可以禁用 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 信任提示，或者要求只针对用 Authenticode 证书签名的解决方案进行提示。  有关如何更改 MyComputer、LocalIntranet、Internet、TrustedSites 和 UntrustedSites 区域的这些设置的更多信息，请参见[如何：配置 ClickOnce 信任提示行为](~/deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md)。  
  
## 请参阅  
 [保护 Office 解决方案的安全](../vsto/securing-office-solutions.md)   
 [向文档授予信任](../vsto/granting-trust-to-documents.md)   
 [Office 解决方案安全性疑难解答](../vsto/troubleshooting-office-solution-security.md)   
 [Office 解决方案的特定安全注意事项](../vsto/specific-security-considerations-for-office-solutions.md)  
  
  