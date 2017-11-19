---
title: "如何： 指定 ClickOnce 应用程序的发布页 |Microsoft 文档"
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
- deploying applications [ClickOnce], specifying publish page
- Publish Page property
- publishing, ClickOnce
- ClickOnce deployment, specifying publish page
ms.assetid: 9d70eebb-bdee-4b42-8e7e-7a07e199bdf7
caps.latest.revision: "18"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: e05718d2a00df76d2c78e16c5b4473ab48d43a39
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-specify-a-publish-page-for-a-clickonce-application"></a>如何：指定 ClickOnce 应用程序的发布页
发布时[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]应用程序中，生成默认网页 (publish.htm) 并将其随应用程序一起发布。 此页包含的应用程序、 将其安装应用程序和/或任何必备项的链接和帮助主题描述的链接名称[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]。 **发布页**为你的项目的属性，可指定 Web 页的名称你[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]应用程序。  
  
 指定发布页后, 的下次发布时，则将其复制到发布位置中;它不会再次发布如果被覆盖。 如果你想要自定义的页的外观，你可以这样做无需担心丢失所做的更改。 有关详细信息，请参阅[如何： 自定义 ClickOnce 默认网页](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md)。  
  
 **发布页**属性可以在中设置**发布选项**对话框中，可从访问**发布**窗格**项目设计器**.  
  
### <a name="to-specify-a-custom-web-page-for-a-clickonce-application"></a>指定 ClickOnce 应用程序的自定义 Web 页  
  
1.  在“解决方案资源管理器” 中选择一个项目，然后在“项目”  菜单上单击“属性” 。  
  
2.  选择**发布**窗格。  
  
3.  单击**选项**按钮以打开**发布选项**对话框。  
  
4.  单击**部署**。  
  
5.  在**发布选项**对话框框中，请确保**发布后打开部署网页**选中复选框 （默认情况下应选中）。  
  
6.  在**部署网页：**框中，为你的 Web 页面上，输入名称，然后单击**确定**。  
  
### <a name="to-prevent-the-publish-page-from-launching-each-time-you-publish"></a>若要阻止发布页启动每次您发布  
  
1.  在“解决方案资源管理器” 中选择一个项目，然后在“项目”  菜单上单击“属性” 。  
  
2.  选择**发布**窗格。  
  
3.  单击**选项**按钮以打开**发布选项**对话框。  
  
4.  单击**部署**。  
  
5.  在**发布选项**对话框中，清除**发布后打开部署网页**复选框。  
  
## <a name="see-also"></a>另请参阅  
 [发布 ClickOnce 应用程序](../deployment/publishing-clickonce-applications.md)   
 [如何： 发布 ClickOnce 应用程序使用发布向导](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)   
 [如何： 自定义 ClickOnce 的默认网页](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md)