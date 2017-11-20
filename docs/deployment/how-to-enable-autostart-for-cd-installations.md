---
title: "如何： 为 CD 安装启用自动启动 |Microsoft 文档"
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
- ClickOnce deployment, AutoStart
- ClickOnce deployment, installation on CD or DVD
- deploying applications [ClickOnce], installation on CD or DVD
ms.assetid: caaec619-900c-4790-90e3-8c91f5347635
caps.latest.revision: "17"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: e3656c3d32dcba946cf66d7fba56a68b3de467f6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-enable-autostart-for-cd-installations"></a>如何：为 CD 安装启用自动启动
在部署时[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]通过可移动媒体如 CD-ROM 或 DVD-ROM 的应用程序，你可以启用`AutoStart`以便[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]插入媒体时自动启动应用程序。  
  
 `AutoStart`可以在上启用**发布**页**项目设计器**。  
  
### <a name="to-enable-autostart"></a>若要启用自动启动  
  
1.  在“解决方案资源管理器” 中选择一个项目，然后在“项目”  菜单上单击“属性” 。  
  
2.  单击**发布**选项卡。  
  
3.  单击**选项**按钮。  
  
     **发布选项**对话框随即出现。  
  
4.  单击**部署**。  
  
5.  选择**对于 CD 安装，插入 CD 时自动启动安装程序**复选框。  
  
     在发布应用程序时，才能将 Autorun.inf 文件复制到发布位置。  
  
## <a name="see-also"></a>另请参阅  
 [发布 ClickOnce 应用程序](../deployment/publishing-clickonce-applications.md)   
 [如何：使用发布向导发布 ClickOnce 应用程序](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)