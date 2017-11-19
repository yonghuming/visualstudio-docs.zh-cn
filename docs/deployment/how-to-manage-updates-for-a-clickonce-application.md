---
title: "如何： 管理 ClickOnce 应用程序的更新 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: Microsoft.VisualStudio.Publish.ClickOnceProvider.Dialog.Update
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, managing applications
- ClickOnce deployment, updates
- updating data, ClickOnce
- application updates
ms.assetid: a3f23f05-e7f1-4620-b23c-2d68f9643684
caps.latest.revision: "13"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 8de46a08d49bb71da055021b6785e4a3e2e97efc
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-manage-updates-for-a-clickonce-application"></a>如何：管理 ClickOnce 应用程序的更新
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]应用程序可以自动或以编程方式检查更新。 作为开发人员，您可以非常灵活地指定何时以及如何执行更新检查、 是否强制进行更新和应用程序应检查更新。  
  
 你可以配置要在应用程序启动后检查更新自动前在应用程序启动，或在设置的时间间隔的应用程序。 此外可以指定最小所需的版本;也就是说，如果用户的版本低于所需版本，则会安装更新。  
  
 你可以配置应用程序检查更新，以编程方式根据用户请求等事件。 "以编程方式检查更新"的过程本主题中演示了如何将编写使用代码<xref:System.Deployment.Application.ApplicationDeployment>基于事件的类，以检查更新。  
  
 此外可以部署应用程序从一个位置，并从另一个更新。 请参阅"指定不同的更新位置。"的过程  
  
 有关详细信息，请参阅[选择 ClickOnce 更新策略](../deployment/choosing-a-clickonce-update-strategy.md)。  
  
 在中管理更新行为**应用程序更新**对话框中，可从**发布**页**项目设计器。**  
  
### <a name="to-check-for-updates-before-the-application-starts"></a>若要在应用程序启动之前检查更新  
  
1.  在“解决方案资源管理器” 中选择了项目的情况下，在“项目”  菜单上单击“属性” 。  
  
2.  单击**发布**选项卡。  
  
3.  单击**更新**按钮以打开**应用程序更新**对话框。  
  
4.  在**应用程序更新**对话框框中，请确保**应用程序应检查更新**复选框处于选中状态。  
  
5.  在**选择应用程序应检查更新时**部分中，选择**应用程序启动前**。 这可确保始终连接到网络的用户使用最新的更新运行应用程序。  
  
### <a name="to-check-for-updates-in-the-background-after-the-application-starts"></a>若要在应用程序启动后检查在后台更新  
  
1.  在“解决方案资源管理器” 中选择了项目的情况下，在“项目”  菜单上单击“属性” 。  
  
2.  单击**发布**选项卡。  
  
3.  单击**更新**按钮以打开**应用程序更新**对话框。  
  
4.  在**应用程序更新**对话框框中，确保选中复选框**应用程序应检查更新**选择。  
  
5.  在**选择何时应用程序应检查更新部分**，选择**应用程序启动后**。 应用程序将启动更快地这种方式，，然后它将在后台检查更新，并仅在有可用的更新时通知用户。 安装完成后，更新才会生效，直到重新启动应用程序。  
  
6.  在**指定应用程序检查更新的频率**部分中，选择**每次应用程序运行时检查**（默认值） 或**检查每个**然后输入一个数字和时间间隔。  
  
### <a name="to-specify-a-minimum-required-version-for-the-application"></a>若要指定应用程序需要的最低版本  
  
1.  在“解决方案资源管理器” 中选择了项目的情况下，在“项目”  菜单上单击“属性” 。  
  
2.  单击**发布**选项卡。  
  
3.  单击**更新**按钮以打开**应用程序更新**对话框。  
  
4.  在**应用程序更新**对话框框中，请确保**应用程序应检查更新**复选框处于选中状态。  
  
5.  选择**指定此应用程序需要的最低版本**复选框，，然后输入**主要**，**次要**，**生成**，和**修订**应用程序的数字。  
  
### <a name="to-specify-a-different-update-location"></a>若要指定不同的更新位置  
  
1.  在“解决方案资源管理器” 中选择了项目的情况下，在“项目”  菜单上单击“属性” 。  
  
2.  单击**发布**选项卡。  
  
3.  单击**更新**按钮以打开**应用程序更新**对话框。  
  
4.  在**应用程序更新**对话框框中，请确保**应用程序应检查更新**复选框处于选中状态。  
  
5.  在**更新位置**字段中，输入具有完全限定的 URL，使用格式 http://Hostname/ApplicationName 或使用格式的 UNC 路径的更新位置\\\Server\ApplicationName，或单击**浏览**按钮以浏览的更新位置。  
  
### <a name="to-check-for-updates-programmatically"></a>若要以编程方式检查更新  
  
1.  在“解决方案资源管理器” 中选择了项目的情况下，在“项目”  菜单上单击“属性” 。  
  
2.  单击**发布**选项卡。  
  
3.  单击**更新**按钮以打开**应用程序更新**对话框。  
  
4.  在**应用程序更新**对话框框中，请确保**应用程序应检查更新**清除复选框。 （或者，你可以选中此复选框可检查更新，以编程方式，同时让 ClickOnce 运行时自动检查更新。）  
  
5.  在**更新位置**字段中，输入具有完全限定的 URL，使用格式 http://Hostname/ApplicationName 或使用格式的 UNC 路径的更新位置\\\Server\ApplicationName，或单击**浏览**按钮以浏览的更新位置。 更新位置是应用程序将寻找本身的更新版本。  
  
6.  用户将选择检查更新为 Windows 窗体上创建一个按钮、 菜单项或其他用户界面项。 从该项的事件处理程序，调用方法，以检查和安装更新。 中的此类的方法，可查找的 Visual Basic 和 Visual C# 代码示例[如何： 检查应用程序更新以编程方式使用 ClickOnce 部署 API](../deployment/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api.md)。  
  
7.  生成你的应用程序。  
  
## <a name="see-also"></a>另请参阅  
 <xref:System.Deployment.Application.ApplicationDeployment>   
 [应用程序更新对话框](http://msdn.microsoft.com/en-us/8eca8743-8e68-4d04-bfd5-4dc0a9b2934f)   
 [选择 ClickOnce 更新策略](../deployment/choosing-a-clickonce-update-strategy.md)   
 [发布 ClickOnce 应用程序](../deployment/publishing-clickonce-applications.md)   
 [如何： 发布 ClickOnce 应用程序使用发布向导](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)   
 [如何：使用 ClickOnce 部署 API 以编程方式检查应用程序更新](../deployment/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api.md)