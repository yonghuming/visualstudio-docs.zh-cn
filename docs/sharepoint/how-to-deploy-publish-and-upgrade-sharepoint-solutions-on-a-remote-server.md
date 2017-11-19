---
title: "如何： 部署、 发布和升级远程服务器上的 SharePoint 解决方案 |Microsoft 文档"
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
helpviewer_keywords:
- remote deployment [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, remote deployment
- deploying [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, deploying
ms.assetid: d9c67fae-d097-4e26-a2b9-0f72ff800987
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 115509e8ff79aafa703c429b476041d558e3167c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server"></a>如何：在远程服务器上部署、发布和升级 SharePoint 解决方案
  除了部署 SharePoint 解决方案到本地系统，你可以将沙盒 SharePoint 解决方案发布到远程站点或本地 SharePoint 站点。 远程发布过程将.wsp 文件复制到 SharePoint 服务器，安装该解决方案，然后，可以激活解决方案。 对它进行更改之后，你还可以升级远程安装的 SharePoint 解决方案。  
  
## <a name="to-publish-a-sandboxed-sharepoint-solution-to-a-remote-sharepoint-server"></a>若要发布到远程 SharePoint 服务器的沙盒的 SharePoint 解决方案  
  
1.  在**解决方案资源管理器**，打开你想要发布，然后选择沙盒 SharePoint 项目的快捷菜单**发布**。  
  
2.  在**发布**对话框框中，选择**发布到 SharePoint 站点**选项按钮，然后再联机发布站点，如下面的示例的输入的 URL: **https://mytestsite.sharepoint.microsoftonline.com**。  
  
3.  选择**浏览器中打开解决方案库页上，在发布后**选项按钮以查看中的解决方案的列表**解决方案库**发布后的页。  
  
4.  选择**发布**按钮。  
  
5.  如果需要用户身份验证，登录到远程服务器。  
  
     在 Visual Studio 中将显示发布进度**输出**窗口。 完成该过程，在远程 SharePoint 服务器上安装解决方案 (.wsp) 文件。 但是，它必须仍先将其激活它可以在 SharePoint 中使用。  
  
6.  上**解决方案库**页上，选择 SharePoint 应用程序，然后在功能区中，选择**激活**按钮。  
  
7.  在**激活解决方案**对话框中，在功能区中，选择**激活**再次按钮。  
  
     **状态**列**解决方案库**页指示应用程序处于活动状态。  
  
## <a name="to-upgrade-a-sandboxed-sharepoint-solution-on-a-remote-sharepoint-server"></a>若要升级在 SharePoint 服务器上远程沙盒 SharePoint 解决方案  
 如果远程服务器上已发布沙盒的 SharePoint 解决方案，使用下列过程使你可以将其升级到中的应用程序进行更改之后[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。  
  
1.  重命名中的 SharePoint 包[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。 为此，请在**解决方案资源管理器**中打开包。 它将出现在**包资源管理器**。  
  
2.  在**包资源管理器**中**名称**框中，将包名称更改为唯一的名称。  
  
3.  保存项目。  
  
4.  在**解决方案资源管理器**，打开该项目的快捷菜单，然后选择**发布**。  
  
5.  在**发布**对话框框中，选择**发布到 SharePoint 站点**选项按钮，，然后，如果缺少解决方案的保存位置的远程服务器的 URL，输入密码。  
  
6.  选择**浏览器中打开解决方案库页上，在发布后**选项按钮以查看中的解决方案的列表**解决方案库**发布后的页。  
  
7.  选择**发布**按钮。  
  
8.  如果需要用户身份验证，登录到远程服务器。  
  
     如果你在登录到远程服务器最近，可能不需要身份验证。  
  
     如果 SharePoint 服务器上仍存在具有相同名称的应用程序的较旧版本，你将收到的错误消息 SharePoint 服务器上已存在具有相同名称的包。 你必须为唯一的名称在发布前重命名包。  
  
9. 在 SharePoint 中，选择新的应用程序，然后，在功能区中，选择**升级**按钮。  
  
10. 在**升级解决方案**对话框中，在功能区中，选择**升级**再次按钮。 **状态**列**解决方案库**页现在应指明应用程序处于活动状态。  
  
     停用旧版本的解决方案，该解决方案的新版本升级与从旧的解决方案中，保留数据，并且在 SharePoint 中激活新的解决方案。  
  
## <a name="see-also"></a>另请参阅  
 [如何： 部署并将其发布到本地 SharePoint 站点的 SharePoint 解决方案](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md)   
 [创建 SharePoint 解决方案包](../sharepoint/creating-sharepoint-solution-packages.md)   
 [如何： 自定义 SharePoint 解决方案包](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)   
 [如何：使用包设计器在包中添加和删除功能和项](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)  
  
  