---
title: "打包和部署 SharePoint 解决方案"
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
  - "打包 [Visual Studio 中的 SharePoint 开发]"
  - "Visual Studio 中的 SharePoint 开发, 打包和部署"
ms.assetid: 39072fa7-9f94-49c0-9a67-cbcce0147e61
caps.latest.revision: 34
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 33
---
# 打包和部署 SharePoint 解决方案
  通常使用解决方案包 \(.wsp\) 文件将 SharePoint 解决方案部署到 SharePoint Server。  可以使用 Visual Studio 将 SharePoint 项目项组织到功能中，并创建一个包来部署 SharePoint 功能。  
  
 本主题提供以下信息：  
  
-   [创建功能和包](#Creating)  
  
-   [功能和打包工具支持](#Tools)  
  
-   [部署 SharePoint 解决方案](#Deploying)  
  
-   [在 SharePoint 解决方案中部署文件](#DeployingFiles)  
  
##  <a name="Creating"></a> 创建功能和包  
 可以使用 Visual Studio 将相关的 SharePoint 元素组合到功能中。  例如，“联系人”列表定义的功能可以包括列表实例和列表定义。  可以将这两个元素合并到单个功能中以进行部署。  有关功能的更多信息，请参见 [生成块：功能](http://go.microsoft.com/fwlink/?LinkID=169183)。  
  
 接下来，您可以创建一个 SharePoint 解决方案包 \(.wsp\) 以将多个功能、网站定义、程序集和其他文件捆绑到单个包中，此包会使用 SharePoint 所需的格式来存储文件以将文件部署到服务器。  有关更多信息，请参见 [生成块：解决方案](http://go.microsoft.com/fwlink/?LinkID=169186)。  
  
##  <a name="Tools"></a> 功能和打包工具支持  
 可以使用 Visual Studio 中的 SharePoint 开发工具将 SharePoint 文件快速组织到功能和解决方案包中以便更轻松地部署。  可以使用以下工具来配置功能和解决方案包。  
  
-   功能设计器和包设计器。  
  
-   打包资源管理器（一个工具窗口）。  
  
-   解决方案资源管理器。  
  
### 功能设计器和包设计器  
 利用功能设计器，可以创建功能、设置作用域以及将其他功能标记为依赖项。  该设计器还会显示用于描述每项功能的最后一个 XML 文件。  有关详细信息，请参阅[创建 SharePoint 功能](../sharepoint/creating-sharepoint-features.md)。  
  
 通过在功能设计器中设置功能的范围，将功能应用于某个特定网站或一组网站。  如果为单个网站激活某项功能，则此功能只能在该特定网站中工作。  如果为网站集激活某项功能，则此功能中的项适用于整个网站集。  有关更多信息，请参见 [元素范围](http://go.microsoft.com/fwlink/?LinkID=169189)。  
  
 如果您的功能依赖于其他功能，则可以在发布该功能之前设置功能激活依赖项以标记从属功能。  功能激活依赖项将检查是否已在此范围内激活从属功能。  有关更多信息，请参见 [激活依赖关系和范围](http://go.microsoft.com/fwlink/?LinkID=169190)。  
  
 在包设计器中，可以将 SharePoint 元素组合到单个解决方案包中，并配置是否在部署期间重置 Web 服务器。  若要设置部署服务器类型，请使用**“属性”**窗口。  该设计器还会生成用于描述包内容的 XML 文件。  有关详细信息，请参阅[创建 SharePoint 解决方案包](../sharepoint/creating-sharepoint-solution-packages.md)。  
  
 在部署过程中，将停止 Internet Information Servers \(IIS\) 服务以将解决方案文件复制到 SharePoint Server。  利用 Visual Studio 中的包设计器，可以选择是否应重新启动 Web 服务器。  若要配置是将解决方案部署到前端 Web 服务器还是应用程序服务器，请使用**“属性”**窗口。  有关更多信息，请参见 [解决方案元素 \(解决方案\)](http://go.microsoft.com/fwlink/?LinkID=169191)。  
  
### 打包资源管理器  
 作为对功能设计器和包设计器的补充，可以使用打包资源管理器将 SharePoint 文件组织到功能和包中。  此外，可以查看包、功能、SharePoint 项目项和文件的分层视图。  打包资源管理器是一个可用于完成下列任务的工具窗口：  
  
-   打开 SharePoint 项目项和文件。  
  
-   将 SharePoint 项目项从一个功能拖放到另一个功能。  
  
-   将 SharePoint 项目项和功能从一个包拖放到另一个包。  
  
-   向包中添加新功能。  
  
-   打开功能设计器或包设计器。  
  
-   验证功能和包。  
  
 Visual Studio 中的 SharePoint 开发工具带有验证规则，可有助于确保解决方案包的格式正确。  此外，这些规则验证是否能在 SharePoint Server 上成功部署和激活 .wsp 解决方案文件。  有关功能的 XML 架构的更多信息，请参见 [功能架构](http://go.microsoft.com/fwlink/?LinkID=169192)。  
  
 可以将自定义功能和包验证规则添加到 SharePoint 项目系统中。  有关详细信息，请参阅[How to: Create Custom Feature and Package Validation Rules for SharePoint Solutions](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md)。  
  
 有关打包资源管理器的更多信息，请参见[如何：使用打包资源管理器在包中添加和移除功能和项](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer.md)。  
  
### 解决方案资源管理器  
 可以使用解决方案资源管理器导航并打开 SharePoint 项目的文件。  使用解决方案资源管理器中的上下文菜单可以添加功能、功能事件接收器和功能资源。  此外，可以打开功能设计器和包设计器来配置功能和包以进行部署。  
  
##  <a name="Deploying"></a> 部署 SharePoint 解决方案  
 在 Visual Studio 中自定义功能和包后，可以创建要部署到 SharePoint Server 的 .wsp 文件。  可以使用 Visual Studio 仅在开发计算机上的 SharePoint Server 上调试和测试 .wsp。  有关如何将 SharePoint 解决方案部署到远程 SharePoint Server 的更多信息，请参见 [部署解决方案](http://go.microsoft.com/fwlink/?LinkID=169194)。  
  
 也可以自定义开发计算机上的部署步骤。  有关详细信息，请参阅[部署、发布和升级 SharePoint 解决方案包](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md)。  
  
##  <a name="DeployingFiles"></a> 在 SharePoint 解决方案中部署文件  
 一般而言，将 SharePoint 项目项添加到 SharePoint 解决方案中时，将会包含所有必需的文件。  可编译的文件（代码文件）将生成到解决方案的输出程序集中。  但是，您可能还必须将非可编译文件（如 .xml、.txt 或资源文件）添加到 SharePoint 项目中。  这些文件不会自动打包在解决方案中。  若要确保将这些文件进行打包，请将它们添加到一个映射文件夹或 SharePoint 项目项中。  
  
 当部署解决方案时，添加到映射文件夹中的文件会自动复制到 SharePoint 配置单元。  添加到 SharePoint 项目项中的文件会自动部署到在每个文件的**“部署位置”**属性中指定的位置，此位置部分地基于**“部署类型”**属性设置。  默认情况下，**“部署类型”**属性值为**“NoDeployment”**，这意味着该文件不会随解决方案一起部署。  您必须为该属性设置其他值以将该文件包含在包中。  
  
 例如，若要将 .xml 文件添加到 SharePoint 项目中，请执行以下操作之一：  
  
-   将 SharePoint 的“Layouts”映射文件夹添加到您的项目中。  这将在**“解决方案资源管理器”**中创建一个名为**“Layouts”**的文件夹，该文件夹包含该项目的子文件夹。  将 .xml 文件添加到新的子文件夹中。  默认情况下，该文件将部署到 SharePoint 文件系统的 ..\\TEMPLATE\\LAYOUTS\\*Folder Name*\\下。  有关如何添加映射文件夹的信息，请参见[如何：添加和移除映射文件夹](../sharepoint/how-to-add-and-remove-mapped-folders.md)。  
  
-   将 .xml 文件添加到 SharePoint 项目项的文件夹中，然后将 .xml 文件的**“部署类型”**属性从**“NoDeployment”**更改为其他设置，如**“RootFile”**或**“ElementFile”**。  **“部署类型”**设置是否适当取决于文件和项目。  有关**“部署类型”**属性设置的更多信息，请参见[开发 SharePoint 解决方案](../sharepoint/developing-sharepoint-solutions.md)。  
  
 如果添加的文件不适用于解决方案中的任何特定项目，则可以在您的解决方案中添加一个空的 SharePoint 项目，然后将其他文件添加到其中。  将文件部署到 SharePoint 的另一个方法（尤其适用于内容数据库）是，在项目中添加一个模块，然后将文件添加到该模块中。  有关详细信息，请参阅[使用模块包括解决方案中的文件](../sharepoint/using-modules-to-include-files-in-the-solution.md)。  
  
## 请参阅  
 [开发 SharePoint 解决方案](../sharepoint/developing-sharepoint-solutions.md)   
 [生成和调试 SharePoint 解决方案](../sharepoint/building-and-debugging-sharepoint-solutions.md)  
  
  