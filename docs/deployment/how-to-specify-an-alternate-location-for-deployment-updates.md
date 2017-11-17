---
title: "如何： 指定部署更新的备用位置 |Microsoft 文档"
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
- ClickOnce deployment, updates
- deployment update, alternative locations
ms.assetid: 7faacd35-2638-492d-80f6-6b57e5f820de
caps.latest.revision: "15"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: a429fa17285018190530ca8058dfb4db7bcb47a2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-specify-an-alternate-location-for-deployment-updates"></a>如何：指定部署更新的其他位置
你可以安装你[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]应用程序最初从 CD 或文件共享，但应用程序必须检查在 Web 上找到的定期更新。 可以在你的部署清单中指定更新的备用位置，以便你的应用程序在其初始安装后可从 Web 自行更新。  
  
> [!NOTE]
>  必须配置应用程序以安装本地以使用此功能。 有关详细信息，请参阅[演练： 手动部署 ClickOnce 应用程序](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)。 此外，如果你安装[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]应用程序从网络上，设置的原因的备用位置[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]要用于该位置的初始安装和所有后续更新。 如果你安装本地应用程序 （例如，在从 CD)，使用的原始媒体执行初始安装和所有后续更新都将使用备用位置。  
  
### <a name="specifying-an-alternate-location-for-updates-by-using-mageuiexe-windows-forms-based-utility"></a>使用 MageUI.exe （基于 Windows 窗体的实用程序） 指定更新的备用位置  
  
1.  打开一个.NET Framework 命令提示符并键入：  
  
     **mageui.exe**  
  
2.  上**文件**菜单上，选择**打开**以打开应用程序的部署清单。  
  
3.  选择**部署选项**选项卡。  
  
4.  在文本框中名为**启动位置**，输入将包含的部署清单的应用程序更新的目录的 URL。  
  
5.  保存部署清单。  
  
### <a name="specifying-an-alternate-location-for-updates-by-using-mageexe"></a>使用 Mage.exe 指定更新的备用位置  
  
1.  打开.NET Framework 命令提示符。  
  
2.  设置使用以下命令的更新位置。 在此示例中， **HelloWorld.exe.application**是路径你[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]始终具有.application 扩展名，应用程序清单和**http://adatum.com/Update/Path**是 URL[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]将检查应用程序更新。  
  
     **Mage-更新 HelloWorld.exe.application-ProviderUrl http://adatum.com/Update/Path**  
  
3.  保存该文件。  
  
    > [!NOTE]
    >  你现在必须使用 Mage.exe 文件重新进行签名。 有关详细信息，请参阅[演练： 手动部署 ClickOnce 应用程序](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)。  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 如果你的应用程序安装脱机媒体如 CD、 中和在计算机处于联机状态，[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]首先检查指定的 URL`<deploymentProvider>`部署清单，以确定是否更新位置包含较新版本的中的标记应用程序。 如果是这样，[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]从初始安装目录中，而不是安装直接从该处，应用程序和公共语言运行时 (CLR) 确定你的应用程序的信任级别使用`<deploymentProvider>`。 如果计算机处于脱机状态，或`<deploymentProvider>`无法访问，[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]从 CD、 和 CLR 安装授予信任基于安装点; 对于 CD 安装，这意味着你的应用程序获得完全信任权限。 所有后续更新将继承该信任级别。  
  
 所有[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]使用的应用程序`<deploymentProvider>`应显式声明在其应用程序清单，所需的权限，因此，应用程序不会收到的不同计算机上的信任级别不同。  
  
## <a name="see-also"></a>另请参阅  
 [演练：手动部署 ClickOnce 应用程序](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [ClickOnce 部署清单](../deployment/clickonce-deployment-manifest.md)   
 [保护 ClickOnce 应用程序](../deployment/securing-clickonce-applications.md)   
 [选择 ClickOnce 更新策略](../deployment/choosing-a-clickonce-update-strategy.md)