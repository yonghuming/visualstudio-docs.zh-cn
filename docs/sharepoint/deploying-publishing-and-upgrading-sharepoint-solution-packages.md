---
title: "部署、发布和升级 SharePoint 解决方案包 | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.SharePointTools.Project.SharePointProjectPropertyTab"
  - "VS.SharePointTools.Project.Publishing"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "部署 [Visual Studio 中的 SharePoint 开发]"
  - "Visual Studio 中的 SharePoint 开发, 部署"
ms.assetid: 5efc1d99-2bd2-4f1a-a7b0-86c3b8f533f0
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# 部署、发布和升级 SharePoint 解决方案包
  在 Visual Studio 开发 SharePoint 解决方案后，则可以部署其包 \(.wsp\) 文件到本地 SharePoint 服务器或发布到远程或本地 SharePoint 服务器。  如果您部署文件，您可以自定义如何部署包文件 \(.wsp\) 。  
  
> [!NOTE]  
>  目前，只有沙盒解决方案可发布到远程 SharePoint 服务器。  有关详细信息，请参阅[沙盒解决方案注意事项](../sharepoint/sandboxed-solution-considerations.md)。  
  
## 部署，发布和升级  
 *部署* 引用复制 Visual Studio 中的 SharePoint 项目生成的 SharePoint 解决方案文件到本地主机。  在已部署的解决方案，您可以配置一个部署步骤回收，例如 Internet Information Services \(IIS\) 池，部署后激活解决方案，依此类推。  若要部署，请使用在 **生成** 菜单的 **部署** 命令。  有关更多信息，请参见[如何：编辑 SharePoint 部署配置](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md)和[如何：将 SharePoint 解决方案部署和发布到本地 SharePoint 网站](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md)。  
  
 *发布* 是指上载沙盒 SharePoint 解决方案文件到远程 SharePoint 网站；即在另一系统上的网站。  您还可以通过发布沙盒 SharePoint 解决方案文件到本地 SharePoint 网站，但无论网站发布是否为本地或远程的，您无法为其配置部署步骤。  
  
 *升级* 是指提供远程或本地发布到的 SharePoint 解决方案。  对Visual Studio 中 SharePoint 解决方案的所有更改之后，您更改解决方案的程序包文件名，将解决方案重新发布，然后在成功发布之后，升级解决方案。  如果重新发布本地发布的解决方案，可以覆盖现有的解决方案文件。  
  
## 部署包  
 可以将包文件部署到开发计算机上的 SharePoint Server 以便进行测试和调试。  您也可以创建可在另一台计算机上安装的包文件，通过在**发布** 对话框中选择 **发布到文件系统** 选项按钮。  包创建和复制到指定的本地文件路径。  若要将 SharePoint 解决方案部署到本地服务器，请使用**生成**菜单中的**部署**命令。  有关详细信息，请参阅[如何：将 SharePoint 解决方案部署和发布到本地 SharePoint 网站](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md)。  
  
 有关如何部署列表定义、添加事件接收器以及使用功能设计器和包设计器的信息，请参见[演练：部署项目任务列表定义](../sharepoint/walkthrough-deploying-a-project-task-list-definition.md)。  
  
## 自定义部署过程  
 下表显示了在调试和部署 SharePoint 解决方案时可使用的两项部署配置。  
  
|部署配置|说明|  
|----------|--------|  
|默认|默认部署配置。  将执行以下部署步骤:<br /><br /> 1.  运行预先部署命令。<br />2.  回收 IIS 应用程序池。<br />3.  收回解决方案。<br />4.  添加解决方案。<br />5.  激活功能。<br />6.  运行后期部署命令。<br /><br /> 在卸载包时，将执行以下收回步骤。<br /><br /> 1.  回收 IIS 应用程序池。<br />2.  收回解决方案。|  
|无激活|此部署配置运行与“默认值”配置相同的步骤，只不过它会跳过激活步骤。|  
  
 您可以创建自己的部署配置以完成单个步骤或更改部署过程中的步骤顺序。  有关详细信息，请参阅[如何：编辑 SharePoint 部署配置](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md)。  
  
 也可以添加要在部署前后运行的命令。  有关详细信息，请参阅[如何：设置 SharePoint 部署命令](../sharepoint/how-to-set-sharepoint-deployment-commands.md)。  
  
## 向远程或本地服务器发布包  
 若要发布一个沙盒 SharePoint 解决方案到远程服务器，请在菜单栏上，依次选择 **生成**、**发布**，在**发布** 对话框中，选择**发布到 SharePoint 网站** 选项按钮，提供远程服务器的 URL，如 https:\/\/someremoteserver.sharepoint.microsoftonline.com。  
  
 若要发布 SharePoint 解决方案到本地服务器，在 **发布** 对话框中，选择 **发布到文件系统** 选项按钮，提供本地系统路径。  
  
 在解决方案成功发布到 SharePoint 后，解决方案会显示在 **解决方案库**中，您可以激活它。  有关详细信息，请参阅[如何：在远程服务器上部署、发布和升级 SharePoint 解决方案](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md)。  
  
### 升级已发布的包  
 如果您在任务发布后，对Visual Studio中的 SharePoint 项目做任何更改，则必须升级包含更改的发布包。  若要升级成功，包必须具有唯一的名称。  如果在 SharePoint 网站找到名称相同的包，当您正在更新现有应用程序时，会发生错误，并通知您访问文件名冲突并允许对包进行重命名。  在发布后，新包随即在 SharePoint 站点，并且可升级。  通过使用较旧的包的数据升级包的更新解决方案，然后激活 SharePoint 中的解决方案。  有关详细信息，请参阅[如何：在远程服务器上部署、发布和升级 SharePoint 解决方案](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md)。  
  
## 请参阅  
 [打包和部署 SharePoint 解决方案](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  