---
title: "如何：将 SharePoint 解决方案部署和发布到本地 SharePoint 网站"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "部署 [Visual Studio 中的 SharePoint 开发]"
  - "Visual Studio 中的 SharePoint 开发, 部署"
ms.assetid: 73f8d6a9-4c64-4bba-ae0e-9474baf8df26
caps.latest.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# 如何：将 SharePoint 解决方案部署和发布到本地 SharePoint 网站
  您可以将 SharePoint 解决方案部署或发布到开发计算机上的本地 SharePoint 服务器。  此部署过程将 .wsp 文件复制到 SharePoint Server，安装解决方案，然后激活功能。  发布过程只将 .wsp 文件复制到 SharePoint 服务器并安装它。  您必须手动将其激活并在 SharePoint 中启用它。  
  
## 将 SharePoint 解决方案部署到本地 SharePoint Server  
  
1.  在**“解决方案资源管理器”**中，选择要部署的项目。  
  
2.  在菜单栏上，依次选择**“生成”**、**“部署解决方案”**。  
  
     这将创建 .wsp 文件并将该文件安装到本地 SharePoint Server 上，  还将激活功能。  
  
## 将 SharePoint 解决方案发布到本地 SharePoint 服务器  
  
1.  在“解决方案资源管理器”中，打开要发布的 SharePoint 项目的快捷菜单，然后选择“发布”。  
  
2.  在 **发布** 对话框中，选择 **发布到文件系统** 选项按钮。  
  
3.  在 **目标位置** 文本框，输入本地路径，然后选择 **发布** 按钮。  
  
     在 Visual Studio **输出** 窗口显示发布进度。  在过程完成时，该解决方案 \(.wsp\) 文件在本地 SharePoint 服务器上安装。  但是，仍然必须在 SharePoint中使用并激活。  如果解决方案文件已经存在，错误并询问是否覆盖现有文件。  升级有关包的信息，请参见在[如何：在远程服务器上部署、发布和升级 SharePoint 解决方案](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md)中升级的远程包的部分。  
  
## 请参阅  
 [如何：在远程服务器上部署、发布和升级 SharePoint 解决方案](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md)   
 [创建 SharePoint 解决方案包](../sharepoint/creating-sharepoint-solution-packages.md)   
 [如何：自定义 SharePoint 解决方案包](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)   
 [如何：使用包设计器在包中添加和移除功能和项](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)  
  
  