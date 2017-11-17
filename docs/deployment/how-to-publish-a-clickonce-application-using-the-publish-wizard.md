---
title: "如何： 发布 ClickOnce 应用程序使用发布向导 |Microsoft 文档"
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
- ClickOnce deployment, publishing
- deploying applications [ClickOnce], Publish wizard
- Windows applications, ClickOnce deployments
- publishing, ClickOnce
ms.assetid: 2e4aa67c-4445-4f7b-9e03-9acb95829127
caps.latest.revision: "25"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: f7921ccebf9872f8a1f8ed79e6ee8da05d04e320
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-publish-a-clickonce-application-using-the-publish-wizard"></a>如何：使用发布向导发布 ClickOnce 应用程序
ClickOnce 应用程序必须发布到文件共享或路径、FTP 服务器或可移动媒体，才能供用户使用。 你可以通过使用发布向导中; 发布应用程序与发布相关的其他属性都位于**发布**页**项目设计器**。 有关详细信息，请参阅[发布 ClickOnce 应用程序](../deployment/publishing-clickonce-applications.md)。  
  
 在运行发布向导前，应适当地设置发布属性。 例如，如果你想要指定密钥为 ClickOnce 应用程序签名，你可以执行依此类推**签名**页**项目设计器**。 有关详细信息，请参阅[保护 ClickOnce 应用程序](../deployment/securing-clickonce-applications.md)。  
  
> [!NOTE]
>  当使用 ClickOnce 安装多个版本的应用程序时，安装会将应用程序的早期版本移动到位于你指定的发布位置的名为“Archive”的文件夹中。 按照这种方式对早期版本进行存档，可以使安装目录与早期版本所在的文件夹分开。  
  
> [!NOTE]
>  显示的对话框和菜单命令可能会与“帮助”中的描述不同，具体取决于你的当前设置或版本。 若要更改设置，请单击 **“工具”** 菜单上的 **“导入和导出设置”** 。 有关详细信息，请参阅[个性化设置 Visual Studio IDE](../ide/personalizing-the-visual-studio-ide.md)。  
  
### <a name="to-publish-to-a-file-share-or-path"></a>发布到文件共享或路径  
  
1.  在**解决方案资源管理器**，选择应用程序项目。  
  
2.  上**生成**菜单上，单击**发布**`Projectname`。  
  
     出现“发布向导”。  
  
3.  在**要在其中发布应用程序？**页上，输入有效的 FTP 服务器地址或有效的文件路径使用一种格式所示，，然后单击**下一步**。  
  
4.  在**用户如何安装应用程序？**页上，选择用户将转至安装应用程序的位置：  
  
    -   如果用户从网站安装，请单击**从网站**和输入在上一步中输入的文件路径相对应的 URL。 单击 **“下一步”**。 （此选项通常在将 FTP 地址指定为发布位置时使用。 不支持从 FTP 直接下载。 因此，必须在此处输入 URL。）  
  
    -   如果用户将直接从文件共享安装应用程序，请单击**从 UNC 路径或文件共享**，然后单击**下一步**。 (这是用于发布位置的窗体 c:\deploy\myapp 或\\\server\myapp。)  
  
    -   如果用户从可移动媒体安装，请单击**从 CD-ROM 或 DVD-ROM**，然后单击**下一步**。  
  
5.  上**应用程序可以脱机？**页上，单击适当的选项：  
  
    -   如果你想要使应用程序在运行时用户已与网络断开连接，请单击**是，此应用程序可联机或脱机**。 上的快捷方式**启动**菜单将创建应用程序。  
  
    -   如果你想要直接从发布位置运行应用程序，请单击**否，此应用程序才可用联机**。 上的快捷方式**启动**将不会创建菜单。  
  
     单击 **“下一步”** 以继续。  
  
6.  单击**完成**发布应用程序。  
  
     发布状态显示在状态通知区域中。  
  
### <a name="to-publish-to-a-cd-rom-or-dvd-rom"></a>发布到 CD-ROM 或 DVD-ROM  
  
1.  在**解决方案资源管理器**，右键单击应用程序项目，然后单击**属性**。  
  
     随即显示“项目设计器”。  
  
2.  单击**发布**选项卡以打开**发布**页面**项目设计器**，然后单击**发布向导**按钮。  
  
     出现“发布向导”。  
  
3.  在**要在其中发布应用程序？**页上，输入的文件路径或 FTP 位置，将已发布应用程序，例如 d:\deploy。 然后单击**下一步**以继续。  
  
4.  上**用户如何安装应用程序？**页上，单击从**CD-ROM 或 DVD-ROM**，然后单击**下一步**。  
  
    > [!NOTE]
    >  如果你想安装自动运行当 CD-ROM 插入到驱动器中，打开**发布**页面**项目设计器**单击**选项**按钮，然后在**发布选项**向导中，选择**对于 CD 安装，插入 CD 时自动启动安装程序**。  
  
5.  如果在 CD-ROM 上发布应用程序，可能会希望从网站提供更新。 在**其中将应用程序检查更新？**页上，选择更新选项：  
  
    -   如果应用程序将检查更新，请单击**应用程序将检查从以下位置下载更新**并输入将发布更新的位置。 该位置可以是文件位置、网站或 FTP 服务器。  
  
    -   如果应用程序将不检查更新，请单击**应用程序将不检查更新**。  
  
     单击 **“下一步”** 以继续。  
  
6.  单击**完成**发布应用程序。  
  
     发布状态显示在状态通知区域中。  
  
    > [!NOTE]
    >  完成发布后，必须使用 CD 刻录机或 DVD 刻录机从步骤 3 中指定的位置将文件复制到 CD-ROM 或 DVD-ROM 媒体。  
  
## <a name="see-also"></a>另请参阅  
 [ClickOnce 安全和部署](../deployment/clickonce-security-and-deployment.md)   
 [保护 ClickOnce 应用程序](../deployment/securing-clickonce-applications.md)   
 [使用 ClickOnce 部署 Office 解决方案](/office-dev/office-dev/deploying-an-office-solution-by-using-clickonce)