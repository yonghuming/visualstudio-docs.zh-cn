---
title: "如何： 为 SharePoint 应用程序页创建用户控件或 Web 部件 |Microsoft 文档"
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
- user controls [SharePoint development in Visual Studio], creating
- user controls [SharePoint development in Visual Studio], adding
ms.assetid: 492ea376-7188-4b5a-a2eb-adc0e3f51484
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1c6384ce4437290c0baa5ea1438a0751b4ec1fcf
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part"></a>如何：为 SharePoint 应用程序页或 Web 部件创建用户控件
  可以创建为 SharePoint 解决方案提供自定义功能的自定义用户控件，您可以在项目中重复使用此功能。 可以在 Web 部件或应用程序页中包含用户控件、添加其他 ASP.NET 控件和 SharePoint 控件、定义控件的属性和方法。 有关用户控件的详细信息，请参阅[为 Web 部件或应用程序页创建可重用控件](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)和[用户控件和 SharePoint 中的服务器控件](http://blogs.msdn.com/b/kaevans/archive/2011/04/28/user-controls-and-server-controls-in-sharepoint.aspx)。  
  
### <a name="to-create-a-user-control-for-sharepoint"></a>若要为 SharePoint 创建用户控件  
  
1.  在 Visual Studio 中打开或创建一个 SharePoint 项目。  
  
     请参阅[SharePoint 项目和项目项模板](../sharepoint/sharepoint-project-and-project-item-templates.md)。  
  
2.  在 **“解决方案资源管理器”**中，选择项目节点。  
  
3.  在菜单栏上，选择**项目**，**添加新项**。  
  
     此时将打开“添加新项”对话框。  
  
4.  在**已安装**窗格中，选择**Office/SharePoint**节点。  
  
5.  在 SharePoint 模板列表中，选择**用户控件 （仅场解决方案）**。  
  
    > [!NOTE]  
    >  用户控件仅适用于场解决方案。  
  
6.  在**名称**框中，为用户控件中，指定一个名称，然后选择**添加**按钮。  
  
     Visual Studio 将添加到你的项目的几个文件夹和文件。 有关这些文件的详细信息，请参阅[为 Web 部件或应用程序页创建可重用控件](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)。  
  
     默认情况下，用户控件文件将显示在**源**Visual Web Developer 设计器的视图。 在此视图中，您可以编辑该控件的 XML 标记。 您可以切换到**设计**查看如果你想要通过将控件从来以可视方式设计控件**工具箱**。 请参阅[设计视图、 网页设计器](http://msdn.microsoft.com/en-us/d8f2270a-357d-40a4-9b39-1a3f2366216d)。  
  
7.  如果要处理控件中发生的事件，请将代码添加到此用户控件的代码文件。  
  
     此文件将显示在**解决方案资源管理器**下的用户控件文件并具有.cs 或.vb 扩展名，具体取决于项目的语言。  
  
## <a name="see-also"></a>另请参阅  
 [为 Web 部件或应用程序页创建可重用控件](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)   
 [为 SharePoint 创建应用程序页](../sharepoint/creating-application-pages-for-sharepoint.md)   
 [为 SharePoint 创建 Web 部件](../sharepoint/creating-web-parts-for-sharepoint.md)  
  
  