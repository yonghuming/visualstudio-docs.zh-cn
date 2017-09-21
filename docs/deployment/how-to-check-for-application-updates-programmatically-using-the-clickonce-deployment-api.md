---
title: "如何：使用 ClickOnce 部署 API 以编程方式检查应用程序更新 | Microsoft Docs"
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
  - "应用程序更新"
  - "ClickOnce 部署, 更新"
ms.assetid: 1a886310-67c8-44e5-a382-c2f0454f887d
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 如何：使用 ClickOnce 部署 API 以编程方式检查应用程序更新
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

ClickOnce 提供了两种在部署后更新应用程序的方法。  在第一种方法中，可以将 ClickOnce 部署配置为以特定间隔时间自动检查是否有更新。  在第二种方法中，可以编写使用 <xref:System.Deployment.Application.ApplicationDeployment> 类根据事件（如用户请求）检查是否有更新的代码。  
  
 下面的过程演示一些执行编程更新的代码，同时描述如何配置 ClickOnce 部署，以启用编程更新检查。  
  
 为了以编程方式更新 ClickOnce 应用程序，必须为更新指定一个位置。  这有时称为部署提供程序。  有关设置此属性的更多信息，请参见[选择 ClickOnce 更新策略](../deployment/choosing-a-clickonce-update-strategy.md)。  
  
> [!NOTE]
>  也可以使用下面所描述的技术在一个位置部署应用程序，而从其他位置更新该应用程序。  有关更多信息，请参见[如何：指定部署更新的其他位置](../deployment/how-to-specify-an-alternate-location-for-deployment-updates.md)。  
  
### 以编程方式检查更新  
  
1.  使用您喜爱的命令行或可视化工具创建一个新的 Windows 窗体应用程序。  
  
2.  创建希望让用户选择以检查是否有更新的任何按钮、菜单项或其他用户界面项。  从该项的事件处理程序调用下列方法以检查是否有更新并安装更新。  
  
     [!CODE [ClickOnceAPI#6](../CodeSnippet/VS_Snippets_Winforms/ClickOnceAPI#6)]  
  
3.  编译应用程序。  
  
### 使用 Mage.exe 部署以编程方式检查是否有更新的应用程序  
  
-   按照 [演练：手动部署 ClickOnce 应用程序](../deployment/walkthrough-manually-deploying-a-clickonce-application.md) 中描述的使用 Mage.exe 部署应用程序的说明进行操作。  在调用 Mage.exe 生成部署清单时，确保使用命令行开关 `providerUrl` 及指定 ClickOnce 应检查是否有更新的 URL。  例如，如果应用程序将从 [http:\/\/www.adatum.com\/MyApp](http://www.adatum.com/MyApp) 进行更新，则生成部署清单的调用可能如下所示：  
  
    ```  
    mage -New Deployment -ToFile WindowsFormsApp1.application -Name "My App 1.0" -Version 1.0.0.0 -AppManifest 1.0.0.0\MyApp.manifest -providerUrl http://www.adatum.com/MyApp/MyApp.application  
    ```  
  
### 使用 MageUI.exe 部署以编程方式检查是否有更新的应用程序  
  
-   按照 [演练：手动部署 ClickOnce 应用程序](../deployment/walkthrough-manually-deploying-a-clickonce-application.md) 中描述的使用 Mage.exe 部署应用程序的说明进行操作。  在**“部署选项”**选项卡上，将**“启动位置”**字段设置为 ClickOnce 应检查是否有更新的应用程序清单。  在**“更新选项”**选项卡上，清除**“此应用程序应该检查更新”**复选框。  
  
## .NET Framework 安全性  
 若要使用编程更新，则您的应用程序必须具有完全信任权限。  
  
## 请参阅  
 [如何：指定部署更新的其他位置](../deployment/how-to-specify-an-alternate-location-for-deployment-updates.md)   
 [选择 ClickOnce 更新策略](../deployment/choosing-a-clickonce-update-strategy.md)   
 [发布 ClickOnce 应用程序](../deployment/publishing-clickonce-applications.md)