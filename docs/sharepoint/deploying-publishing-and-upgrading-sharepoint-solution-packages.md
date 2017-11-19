---
title: "部署、 发布和升级 SharePoint 解决方案包 |Microsoft 文档"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.SharePointTools.Project.SharePointProjectPropertyTab
- VS.SharePointTools.Project.Publishing
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- deploying [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, deploying
ms.assetid: 5efc1d99-2bd2-4f1a-a7b0-86c3b8f533f0
caps.latest.revision: "23"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 5ae973b0a1fc30f0592f6cb2702df645708ab43f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="deploying-publishing-and-upgrading-sharepoint-solution-packages"></a>部署、发布和升级 SharePoint 解决方案包
  开发 Visual Studio 中的 SharePoint 解决方案后，你可以将其包 (.wsp) 文件部署到本地 SharePoint 服务器，或将其发布到远程或本地 SharePoint 服务器。 如果将文件部署，你可以自定义部署的包文件 (.wsp) 的方式。  
  
> [!NOTE]  
>  目前，仅为沙盒解决方案可以发布到远程 SharePoint 服务器。 有关详细信息，请参阅[沙盒解决方案注意事项](../sharepoint/sandboxed-solution-considerations.md)。  
  
## <a name="deploying-publishing-and-upgrading"></a>部署、 发布和升级  
 *部署*指复制生成的本地主机的 Visual Studio 中的 SharePoint 项目的 SharePoint 解决方案文件。 在部署解决方案中，你可以配置的部署步骤，如回收 Internet 信息服务 (IIS) 池、 在部署后，激活解决方案，等等。 若要部署，使用**部署**命令**生成**菜单。 有关详细信息，请参阅[如何： 编辑 SharePoint 部署配置](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md)和[如何： 部署和发布到本地 SharePoint 站点的 SharePoint 解决方案](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md)。  
  
 *发布*指将沙盒的 SharePoint 解决方案文件上载到远程 SharePoint 站点; 即，位于另一个系统上的站点。 此外可以将 SharePoint 沙盒解决方案文件发布到本地 SharePoint 站点，但无论发布到的站点是本地或远程的无法配置其部署步骤。  
  
 *升级*指的是更新现有的远程或本地已发布的 SharePoint 解决方案。 对 Visual Studio 中的 SharePoint 解决方案进行任何更改后，你将更改解决方案的包文件名称、 重新发布该解决方案，然后再升级解决方案后成功重新发布。 如果重新发布本地已发布的解决方案时，你可以覆盖现有的解决方案文件。  
  
## <a name="deploying-packages"></a>部署包  
 你可以进行测试和调试开发计算机上将包文件部署到 SharePoint 服务器中。 你还可以创建包文件，可以在另一台计算机上安装的选择**发布到文件系统**中的选项按钮**发布**对话框。 创建包并将其复制到指定的本地文件路径。 若要将 SharePoint 解决方案部署到本地服务器，使用**部署**命令**生成**菜单。 有关详细信息，请参阅[如何： 部署和发布到本地 SharePoint 站点的 SharePoint 解决方案](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md)。  
  
 若要了解如何部署列表定义、 添加事件接收器，和使用的功能设计器和包设计器，请参阅[演练： 部署项目任务列表定义](../sharepoint/walkthrough-deploying-a-project-task-list-definition.md)。  
  
## <a name="customizing-the-deployment-process"></a>自定义部署过程  
 下表显示在调试和部署 SharePoint 解决方案时，你可以使用两套部署配置。  
  
|部署配置|描述|  
|------------------------------|-----------------|  
|默认|默认部署配置。 将执行以下的部署步骤：<br /><br /> 1.运行预先部署命令。<br />2.回收 IIS 应用程序池。<br />3.收回解决方案。<br />4.将解决方案添加。<br />5.激活功能。<br />6.运行后期部署命令。<br /><br /> 当包已卸载时，将执行以下收回步骤。<br /><br /> 1.回收 IIS 应用程序池。<br />2.收回解决方案。|  
|未激活|此部署配置为默认配置中，运行相同的步骤，但将跳过激活步骤。|  
  
 你可以创建你自己的部署配置来完成单步执行或更改在部署过程中的步骤的顺序。 有关详细信息，请参阅[如何： 编辑 SharePoint 部署配置](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md)。  
  
 你还可以添加命令以运行之前和之后部署。 有关详细信息，请参阅[如何： 设置 SharePoint 部署命令](../sharepoint/how-to-set-sharepoint-deployment-commands.md)。  
  
## <a name="publishing-packages-to-a-remote-or-local-server"></a>包发布到远程或本地服务器  
 若要将沙盒的 SharePoint 解决方案发布到远程服务器上，在菜单栏上，选择**生成**，**发布**，然后在**发布**对话框框中，选择**发布到 SharePoint 站点**选项按钮，提供远程服务器的 URL，例如**https://someremoteserver.sharepoint.microsoftonline.com**。  
  
 若要在发布到本地服务器，SharePoint 解决方案**发布**对话框框中，选择**发布到文件系统**选项按钮，提供本地系统路径。  
  
 一种解决方案已成功将发布到 SharePoint 后，该解决方案将显示在**解决方案库**其中你可以将其激活。 有关详细信息，请参阅[如何： 部署，发布，并在远程服务器上升级 SharePoint 解决方案](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md)。  
  
### <a name="upgrading-published-packages"></a>升级已发布的包  
 如果发布后，可对 Visual Studio 中的 SharePoint 项目中进行任何更改，必须升级发布的包，以包括所做的更改。 若要成功升级，包必须具有唯一的名称。 如果具有相同名称的包位于在 SharePoint 站点上-这可能发生在更新现有应用程序时的错误警报你的文件名称冲突，并允许您重命名包。 之后重新发布，新的包显示在 SharePoint 站点上，可以进行升级。 已升级的包使用的数据从较旧的包中，更新解决方案，然后激活 SharePoint 中的解决方案。 有关详细信息，请参阅[如何： 部署，发布，并在远程服务器上升级 SharePoint 解决方案](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md)。  
  
## <a name="see-also"></a>另请参阅  
 [打包和部署 SharePoint 解决方案](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  