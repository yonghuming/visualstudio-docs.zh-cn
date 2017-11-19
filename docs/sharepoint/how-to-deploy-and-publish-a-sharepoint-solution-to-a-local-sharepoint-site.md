---
title: "如何： 部署并将其发布到本地 SharePoint 站点的 SharePoint 解决方案 |Microsoft 文档"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- deploying [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, deploying
ms.assetid: 73f8d6a9-4c64-4bba-ae0e-9474baf8df26
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4959334c9d6949e199ad18934e69ea46e1172b55
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site"></a>如何：将 SharePoint 解决方案部署和发布到本地 SharePoint 网站
  你可以部署或发布到本地 SharePoint 服务器的 SharePoint 解决方案，你的开发计算机上。 在部署过程将.wsp 文件复制到 SharePoint 服务器，安装该解决方案，然后启用的功能。 发布过程仅将.wsp 文件复制到 SharePoint 服务器，并安装它。 你必须手动激活它，以使它在 SharePoint 中。  
  
## <a name="to-deploy-a-sharepoint-solution-to-the-local-sharepoint-server"></a>将 SharePoint 解决方案部署到本地 SharePoint 服务器  
  
1.  在**解决方案资源管理器**，选择你想要部署的项目。  
  
2.  在菜单栏上，选择**生成**，**部署解决方案**。  
  
     创建并在本地 SharePoint 服务器上安装.wsp 文件。 此外，将激活功能。  
  
## <a name="to-publish-a-sharepoint-solution-to-a-local-sharepoint-server"></a>若要发布到本地 SharePoint 服务器的 SharePoint 解决方案  
  
1.  在**解决方案资源管理器**，打开你想要发布，然后选择 SharePoint 项目的快捷菜单**发布**。  
  
2.  在**发布**对话框框中，选择**发布到文件系统**选项按钮。  
  
3.  在**目标位置**文本框中，输入本地路径，然后选择**发布**按钮。  
  
     在 Visual Studio 中将显示发布进度**输出**窗口。 完成该过程，在本地 SharePoint 服务器上安装解决方案 (.wsp) 文件。 但是，它必须仍激活要在 SharePoint 中使用。 如果解决方案文件已存在，会出现错误，并询问您是否要覆盖现有文件。 有关升级包的信息，请参阅部分升级中的远程包[如何： 部署，发布，并在远程服务器上升级 SharePoint 解决方案](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md)。  
  
## <a name="see-also"></a>另请参阅  
 [如何： 部署、 发布和升级远程服务器上的 SharePoint 解决方案](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md)   
 [创建 SharePoint 解决方案包](../sharepoint/creating-sharepoint-solution-packages.md)   
 [如何： 自定义 SharePoint 解决方案包](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)   
 [如何：使用包设计器在包中添加和删除功能和项](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)  
  
  