---
title: "打包和部署 SharePoint 解决方案 |Microsoft 文档"
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
- packaging [SharePoint development in Visual Studio]
- deploying [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, packaging and deploying
ms.assetid: 39072fa7-9f94-49c0-9a67-cbcce0147e61
caps.latest.revision: "34"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 362667d4f07acb7a6c245247b40911be35479b96
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="packaging-and-deploying-sharepoint-solutions"></a>打包和部署 SharePoint 解决方案
  通常情况下，SharePoint 解决方案部署到 SharePoint 服务器通过使用解决方案包 (.wsp) 文件。 将你的 SharePoint 项目项组织到功能以及用于创建包以部署你的 SharePoint 功能，你可以使用 Visual Studio。  
  
 本主题提供以下信息：  
  
-   [创建功能和包](#Creating)  
  
-   [功能和打包工具支持](#Tools)  
  
-   [部署 SharePoint 解决方案](#Deploying)  
  
-   [部署 SharePoint 解决方案中的文件](#DeployingFiles)  
  
##  <a name="Creating"></a>创建功能和包  
 你可以使用 Visual Studio 将相关的 SharePoint 元素到*功能*。 例如，联系人列表定义的功能可能包括列表实例和列表定义。 可以将这两个元素合并到单个功能以进行部署。 有关功能的详细信息，请参阅[构建基块： 功能](http://go.microsoft.com/fwlink/?LinkID=169183)。  
  
 接下来，你可以创建 SharePoint 解决方案包 (.wsp) 捆绑到一个包中，在多个功能、 站点定义，程序集和其他文件将文件存储在由 SharePoint 所需文件部署到服务器的格式。 有关详细信息，请参阅[构建基块： 解决方案](http://go.microsoft.com/fwlink/?LinkID=169186)。  
  
##  <a name="Tools"></a>功能和打包工具支持  
 可以使用在 Visual Studio 中的 SharePoint 开发工具快速将 SharePoint 文件组织为功能和更易于部署的解决方案包。 以下工具可用于配置功能和解决方案包。  
  
-   功能设计器和包设计器。  
  
-   打包资源管理器，工具窗口。  
  
-   解决方案资源管理器。  
  
### <a name="feature-designer-and-package-designer"></a>功能设计器和包设计器  
 你可以创建功能、 设置作用域，并将其他功能标记为依赖关系，使用功能设计器。 设计器还显示描述每个功能的最后一个 XML 文件。 有关详细信息，请参阅[创建 SharePoint 功能](../sharepoint/creating-sharepoint-features.md)。  
  
 通过设置应用于特定的网站或组的网站的功能其*作用域*功能设计器中。 如果为单个网站激活一项功能，则该功能将仅适用于该特定的 Web 站点。 如果网站集激活功能，功能中的项应用于整个站点集合。 有关详细信息，请参阅[元素范围](http://go.microsoft.com/fwlink/?LinkID=169189)。  
  
 如果你的功能依赖于其他功能，则可以设置*功能激活依赖项*发布该功能之前标记相关的功能。 功能激活依赖关系检查，是否在该范围内已激活相关功能。 有关详细信息，请参阅[激活依赖关系和作用域](http://go.microsoft.com/fwlink/?LinkID=169190)。  
  
 在包设计器中，你可以 SharePoint 元素分组到单个解决方案包中，并配置是否在部署期间重置 Web 服务器。 若要设置部署服务器类型，请使用**属性**窗口。 设计器还会生成描述包内容的 XML 文件。 有关详细信息，请参阅[创建 SharePoint 解决方案包](../sharepoint/creating-sharepoint-solution-packages.md)。  
  
 在部署期间，Internet 信息服务 (IIS) 服务已停止，将解决方案文件复制到 SharePoint 服务器。 通过使用 Visual Studio 中的包设计器，您可以选择是否应重新启动 Web 服务器。 若要配置解决方案部署到前端 Web 服务器或应用程序服务器，请使用**属性**窗口。 有关详细信息，请参阅[解决方案元素 （解决方案）](http://go.microsoft.com/fwlink/?LinkID=169191)。  
  
### <a name="packaging-explorer"></a>打包资源管理器  
 进行补充的功能设计器和包设计器，你可以使用打包资源管理器将 SharePoint 文件到功能和包。 此外，请参阅层次结构视图的包，功能，SharePoint 项目项和文件。 打包资源管理器是一个工具窗口，可用于完成以下任务：  
  
-   打开 SharePoint 项目项和文件。  
  
-   拖到另一个功能从放 SharePoint 项目项。  
  
-   拖放到另一个包从 SharePoint 项目项和功能。  
  
-   将一项新功能添加到包。  
  
-   打开功能或包设计器。  
  
-   验证功能和包。  
  
 Visual Studio 中的 SharePoint 开发工具具有验证规则来帮助确保解决方案包的位置正确。 此外，规则将验证，.wsp 解决方案文件可成功部署和激活 SharePoint 服务器上。 功能的 XML 架构的详细信息，请参阅[功能架构](http://go.microsoft.com/fwlink/?LinkID=169192)。  
  
 你可以将自定义功能和包验证规则添加到 SharePoint 项目系统。 有关详细信息，请参阅[如何： 创建自定义功能和包验证规则，为 SharePoint 解决方案](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md)。  
  
 有关打包资源管理器的详细信息，请参阅[如何： 添加和使用打包资源管理器中删除功能和包项](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer.md)。  
  
### <a name="solution-explorer"></a>“解决方案资源管理器”  
 解决方案资源管理器可用于导航和打开 SharePoint 项目的文件。 在解决方案资源管理器中使用上下文菜单添加功能，功能事件接收器和功能的资源。 此外，你可以打开功能设计器和包设计器配置的功能和部署的包。  
  
##  <a name="Deploying"></a>部署 SharePoint 解决方案  
 自定义功能和 Visual Studio 中的包后，你可以创建.wsp 文件将部署到 SharePoint 服务器。 可以使用 Visual Studio 进行调试和测试.wsp 仅在开发计算机上的 SharePoint 服务器上。 有关如何将 SharePoint 解决方案部署到远程 SharePoint 服务器的详细信息，请参阅[部署解决方案](http://go.microsoft.com/fwlink/?LinkID=169194)。  
  
 你还可以自定义开发计算机上的执行部署步骤。 有关详细信息，请参阅[部署、 发布和升级 SharePoint 解决方案包](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md)。  
  
##  <a name="DeployingFiles"></a>部署 SharePoint 解决方案中的文件  
 通常情况下，当你将 SharePoint 项目项添加到 SharePoint 解决方案时，所有所需的文件包含。 可以是文件编译 （代码文件） 都内置于解决方案的输出程序集。 但是，你可能还需要将非可编译的文件，例如，.xml、.txt 或资源文件添加到 SharePoint 项目。 这些文件不是自动打包到你的解决方案中。 若要确保它们打包，请将文件添加到映射的文件夹或 SharePoint 项目项。  
  
 部署解决方案时，添加到映射的文件夹的文件自动会复制到的 SharePoint 配置单元。 添加到 SharePoint 项目项文件部署到中指定的位置**部署位置**每个文件，部分设置的属性基于**部署类型**属性。 默认情况下，**部署类型**属性值是**NoDeployment**，这意味着没有与解决方案部署该文件。 你必须设置为要将文件包括在包的属性的其他值。  
  
 例如，若要将.xml 文件添加到 SharePoint 项目中，执行以下操作之一：  
  
-   将 SharePoint"布局"映射文件夹添加到你的项目。 这将创建在**解决方案资源管理器**名为的文件夹**布局**具有的项目的子文件夹。 将.xml 文件添加到新的子文件夹。 默认情况下，将文件部署到下的 SharePoint 文件系统...\TEMPLATE\LAYOUTS\\*文件夹名称*\\。 有关如何添加映射的文件夹的信息，请参阅[如何： 添加和移除映射文件夹](../sharepoint/how-to-add-and-remove-mapped-folders.md)。  
  
-   将.xml 文件添加到 SharePoint 项目项的文件夹，然后更改**部署类型**从的.xml 文件的属性**NoDeployment**到另一个设置如**RootFile**或**ElementFile**。 相应**部署类型**设置取决于文件和项目。 有关详细信息**部署类型**属性设置，请参阅[开发 SharePoint 解决方案](../sharepoint/developing-sharepoint-solutions.md)。  
  
 如果添加的文件不适用于解决方案中的任何特定项目，可以将空 SharePoint 项目添加到你的解决方案，然后向其添加其他文件。 有关将文件部署到 SharePoint，特别是对于内容数据库的另一种方法是将模块添加到项目，然后将文件添加到模块。 有关详细信息，请参阅[使用模块添加到解决方案中包含文件](../sharepoint/using-modules-to-include-files-in-the-solution.md)。  
  
## <a name="see-also"></a>另请参阅  
 [开发 SharePoint 解决方案](../sharepoint/developing-sharepoint-solutions.md)   
 [生成和调试 SharePoint 解决方案](../sharepoint/building-and-debugging-sharepoint-solutions.md)  
  
  