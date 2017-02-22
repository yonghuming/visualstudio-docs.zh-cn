---
title: "ClickOnce 如何执行应用程序更新 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
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
  - "ClickOnce 部署, 更新"
  - "部署应用程序 [ClickOnce], 应用程序更新"
  - "更新, ClickOnce"
ms.assetid: d54313c2-cf0c-420d-b151-99953a95f0bb
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# ClickOnce 如何执行应用程序更新
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

ClickOnce 使用应用程序部署清单中指定的文件版本信息来决定是否更新应用程序的文件。  更新开始之后，ClickOnce 使用一种称作“文件修补”的技术来避免多余的应用程序文件下载。  
  
## 文件修补  
 在更新应用程序时，除非文件发生更改，否则 ClickOnce 不会下载新版本应用程序的全部文件。  它将在当前应用程序的应用程序清单中指定的文件哈希签名与新版本清单中的签名进行比较。  如果文件签名不同，则 ClickOnce 下载新版本。  如果签名匹配，则说明该文件未从一个版本更改为下一个版本。  这种情况下，ClickOnce 将复制现有文件，并在应用程序的新版本中使用该文件。  这种方法可以防止 ClickOnce 在即使只有一个或两个文件发生更改的情况下再次下载整个应用程序。  
  
 文件修补也可用于使用 <xref:System.Deployment.Application.ApplicationDeployment.DownloadFileGroup%2A> 和 <xref:System.Deployment.Application.ApplicationDeployment.DownloadFileGroupAsync%2A> 方法按需下载的程序集。  
  
 如果使用 Visual Studio 编译应用程序，则无论何时重新生成整个项目，均会为所有文件生成新的哈希签名。  在这种情况下，虽然只有几个程序集可能发生更改，但所有程序集都将被下载到客户端。  
  
 文件修补对标记为数据和存储在数据目录中的文件不起作用。  无论文件的哈希签名如何，都会下载这些文件。  有关数据目录的更多信息，请参见[在 ClickOnce 应用程序中访问本地数据和远程数据](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)。  
  
## 请参阅  
 [选择 ClickOnce 更新策略](../deployment/choosing-a-clickonce-update-strategy.md)   
 [选择 ClickOnce 部署策略](../deployment/choosing-a-clickonce-deployment-strategy.md)