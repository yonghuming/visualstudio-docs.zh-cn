---
title: "如何： 检查应用程序更新使用 ClickOnce 部署 API 以编程方式 |Microsoft 文档"
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
- application updates
ms.assetid: 1a886310-67c8-44e5-a382-c2f0454f887d
caps.latest.revision: "9"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 9b240bcdcc576e7ace85e766b54e5cd70e4e5503
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api"></a>如何：使用 ClickOnce 部署 API 以编程方式检查应用程序更新
ClickOnce 提供两种方法部署后更新的应用程序。 在第一种方法，你可以配置 ClickOnce 部署，以自动检查更新某些时间间隔。 在第二个方法中，你可以编写使用的代码<xref:System.Deployment.Application.ApplicationDeployment>类，以检查更新基于事件，例如用户请求。  
  
 下面的过程查看用于执行的以编程方式更新一些代码，并还描述如何配置 ClickOnce 部署，以启用以编程方式更新检查。  
  
 若要以编程方式更新 ClickOnce 应用程序，你必须指定更新的位置。 这有时称为部署提供程序。 有关设置此属性的详细信息，请参阅[选择 ClickOnce 更新策略](../deployment/choosing-a-clickonce-update-strategy.md)。  
  
> [!NOTE]
>  你还可以使用下面所述部署应用程序从一个位置，但从另一个对其进行更新的技术。 有关详细信息，请参阅[如何： 指定部署更新的备用位置](../deployment/how-to-specify-an-alternate-location-for-deployment-updates.md)。  
  
### <a name="to-check-for-updates-programmatically"></a>若要以编程方式检查更新  
  
1.  创建使用你首选的命令行或可视化工具的新 Windows 窗体应用程序。  
  
2.  创建任何按钮、 菜单项或其他用户界面项您希望用户能够进行选择以检查更新。 从该项的事件处理程序，调用以下方法来检查和安装更新。  
  
     [!code-csharp[ClickOnceAPI#6](../deployment/codesnippet/CSharp/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api_1.cs)]
     [!code-cpp[ClickOnceAPI#6](../deployment/codesnippet/CPP/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api_1.cpp)]
     [!code-vb[ClickOnceAPI#6](../deployment/codesnippet/VisualBasic/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api_1.vb)]  
  
3.  编译应用程序。  
  
### <a name="using-mageexe-to-deploy-an-application-that-checks-for-updates-programmatically"></a>使用 Mage.exe 部署的应用程序以编程方式检查更新  
  
-   按照说明部署应用程序中所述使用 Mage.exe[演练： 手动部署 ClickOnce 应用程序](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)。 当调用 Mage.exe 生成部署清单，请确保使用命令行开关`providerUrl`，并指定 ClickOnce 检查更新的位置的 URL。 如果你的应用程序将更新从[http://www.adatum.com/MyApp](http://www.adatum.com/MyApp)，例如，若要生成的部署清单的调用可能如下所示：  
  
    ```  
    mage -New Deployment -ToFile WindowsFormsApp1.application -Name "My App 1.0" -Version 1.0.0.0 -AppManifest 1.0.0.0\MyApp.manifest -providerUrl http://www.adatum.com/MyApp/MyApp.application  
    ```  
  
### <a name="using-mageuiexe-to-deploy-an-application-that-checks-for-updates-programmatically"></a>使用 MageUI.exe 部署的应用程序以编程方式检查更新  
  
-   按照说明部署应用程序中所述使用 Mage.exe[演练： 手动部署 ClickOnce 应用程序](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)。 上**部署选项**选项卡上，设置**启动位置**字段 ClickOnce 应检查是否有更新的应用程序清单。 上**更新选项**选项卡上，清除**此应用程序应检查更新**复选框。  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 你的应用程序必须具有完全信任权限，用于以编程方式更新。  
  
## <a name="see-also"></a>另请参阅  
 [如何： 指定部署更新的备用位置](../deployment/how-to-specify-an-alternate-location-for-deployment-updates.md)   
 [选择 ClickOnce 更新策略](../deployment/choosing-a-clickonce-update-strategy.md)   
 [发布 ClickOnce 应用程序](../deployment/publishing-clickonce-applications.md)