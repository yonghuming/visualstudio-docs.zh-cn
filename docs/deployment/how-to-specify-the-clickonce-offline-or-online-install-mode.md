---
title: "如何： 指定 ClickOnce 脱机或联机安装模式 |Microsoft 文档"
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
- ClickOnce deployment, specifying install mode
- install mode
- online applications
- offline applications
- ClickOnce install mode
ms.assetid: 0aee5fc1-e966-4bda-9b8f-d9997aeaa779
caps.latest.revision: "8"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 5376ef32ce768100af8bc1c9f18267f7ac39895a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-specify-the-clickonce-offline-or-online-install-mode"></a>如何：指定 ClickOnce 脱机或联机安装模式
`Install Mode`为[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]应用程序确定应用程序是脱机还是联机。 当你选择**应用程序仅可联机**，用户必须有权[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]发布 （网页或文件共享） 才能运行应用程序的位置。 当你选择**应用程序也可以脱机使用**，应用程序将条目添加到**启动**菜单和**添加或删除程序**对话框; 用户是能够在不连接时运行该应用程序。  
  
 `Install Mode`可以对设置**发布**页**项目设计器**。  
  
 **请注意**`Install Mode`还可以通过使用发布向导设置。 有关详细信息，请参阅[如何： 发布 ClickOnce 应用程序使用发布向导](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)。  
  
### <a name="to-make-a-clickonce-application-available-online-only"></a>提供 ClickOnce 应用程序联机仅  
  
1.  在“解决方案资源管理器” 中选择了项目的情况下，在“项目”  菜单上单击“属性” 。  
  
2.  单击**发布**选项卡。  
  
3.  在**安装模式和设置**区域中，单击**应用程序仅可联机**选项按钮。  
  
### <a name="to-make-a-clickonce-application-available-online-or-offline"></a>若要使 ClickOnce 应用程序可用，联机或脱机  
  
1.  在“解决方案资源管理器” 中选择了项目的情况下，在“项目”  菜单上单击“属性” 。  
  
2.  单击**发布**选项卡。  
  
3.  在**安装模式和设置**区域中，单击**应用程序也可以脱机使用**选项按钮。  
  
     安装时，应用程序将条目添加到**启动**菜单和**添加或删除程序**控制面板中。  
  
## <a name="see-also"></a>另请参阅  
 [发布 ClickOnce 应用程序](../deployment/publishing-clickonce-applications.md)   
 [如何： 发布 ClickOnce 应用程序使用发布向导](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)   
 [选择 ClickOnce 部署策略](../deployment/choosing-a-clickonce-deployment-strategy.md)