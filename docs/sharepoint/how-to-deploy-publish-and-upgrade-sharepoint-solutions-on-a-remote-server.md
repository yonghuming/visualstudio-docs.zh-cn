---
title: "如何：在远程服务器上部署、发布和升级 SharePoint 解决方案 | Microsoft Docs"
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
helpviewer_keywords: 
  - "部署 [Visual Studio 中的 SharePoint 开发]"
  - "远程部署 [Visual Studio 中的 SharePoint 开发]"
  - "Visual Studio 中的 SharePoint 开发, 部署"
  - "Visual Studio 中的 SharePoint 开发, 远程部署"
ms.assetid: d9c67fae-d097-4e26-a2b9-0f72ff800987
caps.latest.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 13
---
# 如何：在远程服务器上部署、发布和升级 SharePoint 解决方案
  除了部署到本地系统的 SharePoint 解决方案外，您可以发布沙盒 SharePoint 解决方案到远程站点或本地 SharePoint 网站。  远程的发布过程将 .wsp 文件复制到 SharePoint Server，安装解决方案，然后可以激活解决方案。  在更改之后，您还可以升级到远程 SharePoint 安装解决方案。  
  
## 发布一个沙盒 SharePoint 解决方案到远程 SharePoint Server  
  
1.  在“解决方案资源管理器”中，打开要发布的沙盒 SharePoint 项目的快捷菜单，然后选择“发布”。  
  
2.  在 **发布** 对话框中，选择 **发布到 SharePoint 网站** 选项按钮，然后输入一联机发布网站的 URL，如以下示例：https:\/\/mytestsite.sharepoint.microsoftonline.com。  
  
3.  选择 **发布后在浏览器中打开“解决方案库”页** 选项按钮，在发布之后在**解决方案库**页中显示解决方案列表。  
  
4.  选择**“发布”**按钮。  
  
5.  如有必要，请登录到远程服务器进行用户身份验证。  
  
     在 Visual Studio **输出** 窗口显示发布进度。  在过程完成时，该解决方案 \(.wsp\) 文件在远程 SharePoint 服务器上安装。  但是，在 SharePoint 中使用之前，它必须激活。  
  
6.  在 **解决方案库** 页，选择 SharePoint 应用程序，然后在功能区上，选择 **激活** 按钮。  
  
7.  在 **激活解决方案** 对话框，在功能区，请选择 **激活** 按钮。  
  
     **状态** 列在 **解决方案库** 页指示应用程序处于活动状态。  
  
## 在远程 SharePoint 服务器，升级沙盒SharePoint 解决方案  
 如果一个沙盒 SharePoint 解决方案已发布在远程服务器上，您在[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]对应用程序进行更改之后，以下过程可以将其升级。  
  
1.  在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]中重命名SharePoint 包。  为此，在**“解决方案资源管理器”**中，打开包。  它出现在**包资源管理器**。  
  
2.  在 **包资源管理器**，**名称** 框中，请将包名称改为一个唯一的名称。  
  
3.  保存项目。  
  
4.  在**“解决方案资源管理器”**中，打开项目的快捷菜单，然后选择**“发布”**。  
  
5.  在 **发布** 对话框中，选择 **发布到 SharePoint 网站** 选项按钮，如果存储在远程服务器的 URL中的解决方案丢失，请输入它。  
  
6.  选择 **发布后在浏览器中打开“解决方案库”页** 选项按钮，在发布之后在**解决方案库**页中显示解决方案列表。  
  
7.  选择**“发布”**按钮。  
  
8.  如有必要，请登录到远程服务器进行用户身份验证。  
  
     如果最近登录到远程服务器，可能不需要身份验证。  
  
     如果仍然有同名应用程序的旧版本存在于 SharePoint 服务器中，您将收到同名的包已存在于 SharePoint 服务器的错误。  在发布前，您必须重命名包为一个唯一的名称。  
  
9. 选择 SharePoint 中的新应用程序，然后在功能区上，选择 **升级** 按钮。  
  
10. 在 **升级解决方案** 对话框，在功能区，请选择 **升级** 按钮。  在 **解决方案库** 页的**状态** 列，现在应指示应用程序处于活动状态。  
  
     解决方案的早期版本停用，解决方案的新版本用旧解决方案的数据维护，并且，则新的解决方案会在 SharePoint 中激活。  
  
## 请参阅  
 [如何：将 SharePoint 解决方案部署和发布到本地 SharePoint 网站](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md)   
 [创建 SharePoint 解决方案包](../sharepoint/creating-sharepoint-solution-packages.md)   
 [如何：自定义 SharePoint 解决方案包](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)   
 [如何：使用包设计器在包中添加和移除功能和项](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)  
  
  