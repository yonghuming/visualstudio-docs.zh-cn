---
title: "ClickOnce 如何执行应用程序更新 |Microsoft 文档"
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
- updates, ClickOnce
- ClickOnce deployment, updates
- deploying applications [ClickOnce], application updates
ms.assetid: d54313c2-cf0c-420d-b151-99953a95f0bb
caps.latest.revision: "9"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 32e0b56ab5d4507c971948b98c8f7660650e70cc
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="how-clickonce-performs-application-updates"></a>ClickOnce 如何执行应用程序更新
ClickOnce 使用应用程序的部署清单中指定的文件版本信息来决定是否要更新应用程序的文件。 ClickOnce 更新开始后，使用一种称为技术*文件修补*从而避免冗余下载的应用程序文件。  
  
## <a name="file-patching"></a>文件修补程序  
 在更新应用程序，ClickOnce 不会下载的所有应用程序的新版本文件除非文件已更改。 相反，它将针对新版本的清单中的签名对当前应用程序的应用程序清单中指定的文件的哈希签名进行比较。 如果文件的签名不同，ClickOnce 将下载最新版本。 如果签名匹配，文件未更改从一个版本到下一步。 在这种情况下，ClickOnce 将现有文件复制，并在新版本的应用程序使用它。 此方法可防止 ClickOnce 无需下载一次，整个应用程序即使只能将一个或两个文件已更改。  
  
 亦文件修补程序适用于下载的程序集上需要使用<xref:System.Deployment.Application.ApplicationDeployment.DownloadFileGroup%2A>和<xref:System.Deployment.Application.ApplicationDeployment.DownloadFileGroupAsync%2A>方法。  
  
 如果使用 Visual Studio 来编译你的应用程序，它将生成新的哈希签名的所有文件，每当您重新生成整个项目。 在这种情况下，所有程序集将下载到客户端，尽管只有几个程序集可能已更改。  
  
 修补文件不能用于标记为数据和存储在数据目录中的文件。 这些始终会下载而不考虑文件的哈希签名。 数据目录的详细信息，请参阅[访问本地数据和 ClickOnce 应用程序中的远程数据](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)。  
  
## <a name="see-also"></a>另请参阅  
 [选择 ClickOnce 更新策略](../deployment/choosing-a-clickonce-update-strategy.md)   
 [选择 ClickOnce 部署策略](../deployment/choosing-a-clickonce-deployment-strategy.md)