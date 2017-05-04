---
title: "发布向导（Visual Studio 中的 Office 开发） | Microsoft Docs"
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
  - "VST.ProjectProperties.PublishWizard"
  - "VST.PublishWizard.Publish.2007System"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "ClickOnce 部署 [Visual Studio 中的 Office 开发]，发布向导"
  - "部署应用程序 [Visual Studio 中的 Office 开发]，发布向导"
  - "Office 应用程序 [Visual Studio 中的 Office 开发]，发布向导"
  - "发布向导，Office 解决方案"
ms.assetid: 793314b6-b6a6-4509-8f1c-dd9466cf5190
caps.latest.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 13
---
# 发布向导（Visual Studio 中的 Office 开发）
  使用 **发布向导** 解决方案文件复制到指定位置，创建清单文件，并创建安装程序。  
  
 若要访问此向导， **生成** 菜单上，选择 **发布** *SolutionName*。  还可以从访问 **解决方案资源管理器**的 **发布向导** 。  打开项目节点的快捷菜单，然后选择 **发布**。  
  
 下面每一节中描述向导的页。  
  
## 在哪里若要发布应用程序?  
 **指定发布此应用程序的位置**  
 必需。  发布位置是 **发布向导** 复制解决方案文件 \(比如清单，程序集、临时证书和生成中的其他文件内容。  您必须对该目录的写访问权。  
  
 键入位置作为磁盘路径、文件共享、 FTP 站点或网站 URL 或单击 **浏览** 按钮以浏览位置。  该路径可以使用以下格式:  
  
-   标准 windows 的相对路径或绝对路径格式，如 C:\\Deploy\\MyApplication 或 \\ MyApplication。  
  
-   通用命名 \(UNC\)约定 \(unc\) 路径，如 \\ \\ ServerName \\ MyApplication \\。  
  
-   一个网站的 URL，例如 http:\/\/www.microsoft.com\/MyApplication。  
  
 默认情况下，发布位置是 *http:\/\/localhost\/projectname\/* ，如果安装了 IIS，则发布位置为 publish \\ 目录，如果没有安装 IIS。  
  
> [!NOTE]  
>  ，如果目标计算机运行的是 Windows vista，还有其他一些注意事项。  若要使用本地的 Windows vista 计算机上的管理员发布选项。  此外，默认位置始终是 *publish \\* 内容，无论是否已安装 IIS。  
  
## 什么是在最终用户计算机上的默认安装路径?  
 安装路径是可选的。  ，如果您愿意，可以在以后安装路径。  有关详细信息，请参见 [如何：更改 Office 解决方案的安装路径](http://msdn.microsoft.com/zh-cn/d0eaa07b-2d72-4902-899f-2f9fb165b8fd)。  
  
 安装路径是最终用户将在其中安装自定义项的目录。  这也是解决方案将用于检查更新的路径。  **发布向导** 不将解决方案部署到此位置，除非路径，这与于您在上一页的 **指定发布此应用程序的位置** 框中输入了。  
  
 **从网站**  
 指定最终用户将按照安装解决方案的 URL。  
  
 **从 UNC 路径或文件共享**  
 指定最终用户将按照安装解决方案的 UNC 路径。  
  
 **从 CD\-ROM 或 DVD\-ROM**  
 此选项不需要安装路径。  
  
 Visual Studio 不写入 CD 或 DVD。  您必须手动将输出复制到 CD 或 DVD。  
  
## 请参阅  
 [使用 ClickOnce 部署 Office 解决方案](../vsto/deploying-an-office-solution-by-using-clickonce.md)   
 [项目设计器 -&#62;“发布页”（Visual Studio 中的 Office 开发）](../vsto/publish-page-project-designer-office-development-in-visual-studio.md)   
 [部署 Office 解决方案](../vsto/deploying-an-office-solution.md)  
  
  