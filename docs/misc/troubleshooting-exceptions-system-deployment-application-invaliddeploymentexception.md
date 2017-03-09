---
title: "异常疑难解答：System.Deployment.Application.InvalidDeploymentException | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "InvalidDeploymentException 类"
ms.assetid: 4361e053-8eaf-44e3-b8ac-95516d8d1832
caps.latest.revision: 22
caps.handback.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 异常疑难解答：System.Deployment.Application.InvalidDeploymentException
应用程序或其应用程序清单和部署清单无效时，将引发 <xref:System.Deployment.Application.InvalidDeploymentException> 异常。  
  
## 相关提示  
 **确保此应用程序的清单有效。**  
 应用程序清单是一个 XML 文件，它描述并标识应用程序在运行时应该绑定到的共享和私有并行程序集。 这些程序集的版本应与测试应用程序时使用的程序集版本相同。 应用程序清单还可以描述应用程序的私有文件的元数据。  
  
 **使用 ClickOnce 功能来部署应用程序。**  
 使用 ClickOnce 将 Windows 应用程序发布到 Web 服务器或网络文件共享，从而简化安装。 有关详细信息，请参阅[ClickOnce 安全和部署](../deployment/clickonce-security-and-deployment.md)。  
  
## 请参阅  
 <xref:System.Deployment.Application.InvalidDeploymentException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [ClickOnce 部署疑难解答](../deployment/troubleshooting-clickonce-deployments.md)   
 [Windows 窗体的 ClickOnce 部署](../Topic/ClickOnce%20Deployment%20for%20Windows%20Forms.md)